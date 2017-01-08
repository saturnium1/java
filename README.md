import java.util.Scanner;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.ie.InternetExplorerDriver;

public class NewTesting {
	
	
	public static void functia(int i, String name, String pass) throws InterruptedException
	
	{
		WebDriver wdr=null;
		switch (i)
		{
		case 1:
		{
			System.setProperty("webdriver.gecko.driver", "C://selenium//geckodriver.exe");
			
			wdr = new FirefoxDriver();
			break;
		}
		case 2:
		{
			System.setProperty("webdriver.chrome.driver", "C://selenium//chromedriver.exe");
			wdr = new ChromeDriver();
			break;
		}
		default : break;
			
		}
		wdr.get("http://www.gmail.com");
		
		wdr.findElement(By.id("Email")).clear();
		wdr.findElement(By.id("Email")).sendKeys(name);
		wdr.findElement(By.id("next")).click();
		Thread.sleep(2000);
		
		wdr.findElement(By.id("Passwd")).sendKeys(pass);
		wdr.findElement(By.id("signIn")).click();
			
		Thread.sleep(20000);
		String inbox=wdr.findElement(By.partialLinkText("Inbox")).getText();
		String rez="";
		for(int count=0; count<inbox.length(); count++){
			char c = inbox.charAt(count);
	        if(c > 47 && c < 58)
	           rez+=c;
	           
		}
		System.out.println("Unread messages in inbox: "+rez);
		
		if(wdr!=null)
		wdr.quit();
		
	}

	public static void main(String[] args) throws InterruptedException
	{
		
		
		/*System.setProperty("webdriver.ie.driver", "C://Selenium//IEDriverServer.exe");
		WebDriver wdr = new InternetExplorerDriver();
		*/

		System.out.println("Choose Your Browser");

		System.out.println("For Firefox --> 1, Crome --> 2");
		Scanner scan;
		scan = new Scanner(System.in);
		int i = scan.nextInt();
		
		System.out.print("Username: ");
		
		String name = scan.next();
		
		System.out.print("Password: ");
		
		String pass = scan.next();

		functia(i,name,pass);
		scan.close();
		
			}

}
