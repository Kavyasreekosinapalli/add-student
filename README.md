# add-student

package testintroduction;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.Select;

public class Addstudent {

public static void main(String[] args) throws InterruptedException {
	
	// Launch the Chrome browser
    WebDriver driver = new ChromeDriver();

    // Navigate to the e-commerce website-amazon
    driver.get("https://lms3.vipsclub.org/login");
    driver.manage().window().maximize();

    // Wait for a few seconds to ensure the page is fully loaded
    Thread.sleep(2000);
 
    // Login logic
    // Enter username
    driver.findElement(By.name("email")).sendKeys("test@gmail.com");
    
    //enter password
    driver.findElement(By.name("password")).sendKeys("123456");
    
    //click on login button
    driver.findElement(By.id("auth_login")).click();
    
    //wait until page is fully loaded
    Thread.sleep(5000);
    
    //naviagate to student page
    driver.findElement(By.xpath("(//div[@class='edu_color_boxes box_left'])[2]")).click();
    //click on add student button
    driver.findElement(By.className("edu_admin_btn")).click();
   
    //select gender from dropdown
    WebElement gender = driver.findElement(By.name("gender"));
    Select dropdown= new Select(gender);
    dropdown.selectByIndex(1);
    
    //add name
    driver.findElement(By.name("name")).sendKeys("testing");
 
    //Add date of birth
    driver.findElement(By.name("dob")).click();
   
    //wait until dob is fully loaded 
    Thread.sleep(5000);
    
    String aMonth = driver.findElement(By.className("ui-datepicker-month")).getText();
    String aYear = driver.findElement(By.className("ui-datepicker-year")).getText();
    
    while (aMonth.equals("Aug") && aYear.equals("2022")) {
    	
    	driver.findElement(By.xpath("//a[@title='Prev']")).click();
    	 aMonth = driver.findElement(By.className("ui-datepicker-month")).getText();
    	 aYear = driver.findElement(By.className("ui-datepicker-year")).getText();	 
    }
    
    driver.findElement(By.xpath("//td[@data-handler='selectDay']/a[text()='11']")).click();
    
    //contact number
    driver.findElement(By.name("contact_no")).sendKeys("5971592185");
    //enter email
    driver.findElement(By.name("email")).sendKeys("test4@gmail.com");
    
    //select batch
    WebElement batch = driver.findElement(By.name("multi_batch_id[]"));
    Select dropdown1= new Select(batch);
    dropdown1.selectByIndex(2);
   
   //click on add student button
    driver.findElement(By.xpath("//input[@value='Add Student']")).click();
    
    
    //wait to make sure student is added successfully
    Thread.sleep(10000);
    
    driver.quit();
	}

}
