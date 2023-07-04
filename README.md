# Amazon_Inspection_Selenium
package Section_3;

import java.awt.AWTException;
import java.awt.Robot;
import java.awt.event.KeyEvent;

import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;
import org.openqa.selenium.interactions.Actions;
public class Amazon
{
	public static void main(String[] args) throws InterruptedException, AWTException 
	{
		System.setProperty("WebDriver.Chrome.Driver","C:\\Users\\sivap\\eclipse-workspace\\Selenium\\server\\chromedriver.exe");
		ChromeOptions opt = new ChromeOptions();//IF BROWSER VERSION IS CHANGED THEN WE CAN USE THIS 
		opt.addArguments("--remote-allow-origins=*");//OR
		ChromeDriver d=new ChromeDriver(opt);//IF WE GET THREAD IO MAIN EXCEPTON AND STATUS CODE IS 403 FORBIDDEN
		d.manage().window().maximize();
		d.get("https://www.amazon.in/");
		d.findElement(By.id("twotabsearchtextbox")).sendKeys("Wrist Watches",Keys.ENTER);
		Thread.sleep(3000);
		
		//TITAN
		d.findElement(By.xpath("//*[@id=\"p_89/Titan\"]/span/a/div/label/i")).click();
		Thread.sleep(3000);
		
		//DISCOUNT 25% OR MORE
		WebElement discount= d.findElement(By.xpath("//*[@id=\"p_n_pct-off-with-tax/2665400031\"]/span/a/span"));
		JavascriptExecutor jse =(JavascriptExecutor)d;
		jse.executeScript("window.scrollBy(0,1100)", discount);
		Thread.sleep(3000);
		discount.click();
		Thread.sleep(3000);
		
		//ANALOUGE
		WebElement analouge= d.findElement(By.xpath("//*[@id=\"p_n_feature_seven_browse-bin/1480900031\"]/span/a/div/label/i"));
	    JavascriptExecutor jse1 =(JavascriptExecutor)d;
		jse1.executeScript("window.scrollBy(0,1100)", analouge);
		Thread.sleep(3000);
		analouge.click();
		Thread.sleep(3000);
		
		//LEATHER
		WebElement leather= d.findElement(By.xpath("//*[@id=\"p_n_material_browse/1480907031\"]/span/a/div/label/i"));
	    JavascriptExecutor jse2 =(JavascriptExecutor)d;
		jse2.executeScript("window.scrollBy(0,1100)", leather);
		Thread.sleep(3000);
		leather.click();
		Thread.sleep(3000);
		
		//EXIT
		d.close();	
	}
}
