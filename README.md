Login flow of the application

Selenium code

@RunWith(Parameterized.class)
public class LoginTest {
    @Parameters
    public static Collection<Object[]> data() {
        return Arrays.asList(new Object[][] {     
         { " standard_user", " secret_sauce" }, 
         { " locked_out_user", " secret_sauce" }, 
         { " problem_user", " secret_sauce" }, 
         { " performance_glitch_user", " secret_sauce" }, 

    });
}

private String username, password;

public LoginTest(String username, String password) {
     this.username = username;
     this.password = password;
}

@Test
public void login() {

System.setProperty("webdriver.chrome.driver", "path of driver");
WebDriver driver=new ChromeDriver();
driver.manage().window().maximize();
driver.get("https://www.saucedemo.com/");
    driver.findElement(By.id("user-name ")).sendKeys(username);
    driver.findElement(By.id("password")).sendKeys(password);

WebElement login=driver.findElement(By.name("login-button")).click();
String actualUrl="https://www.saucedemo.com/inventory.html";
String expectedUrl= driver.getCurrentUrl();
Assert.assertEquals(expectedUrl,actualUrl, “Epic sadface: Username and password do not match any user in this service”);
driver.findElement(By.id("remove-test.allthethings()-t-shirt(red)")).click();;
driver.findElement(By.id("add-to-cart-sauce-labs-backpack")).click();;
driver.findElement(By.id("remove-sauce-labs-bike-light")).click();


}


