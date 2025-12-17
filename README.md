# ass-17
1. Click “Open New Seperate Windows”, switch to new window, validate URL/Title

URL: https://demo.automationtesting.in/Windows.html

✔ Click button
✔ Switch to new window
✔ Validate Title or URL
✔ Print PASS / FAIL

Selenium Java Program
import java.util.Set;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class WindowHandling {

    public static void main(String[] args) {

        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        WebDriver driver = new ChromeDriver();
        driver.manage().window().maximize();

        driver.get("https://demo.automationtesting.in/Windows.html");

        // Click "Open New Seperate Windows" button
        driver.findElement(By.xpath("//button[contains(text(),'Open New Seperate Windows')]")).click();

        // Get parent window handle
        String parentWindow = driver.getWindowHandle();

        // Get all window handles
        Set<String> allWindows = driver.getWindowHandles();

        for (String window : allWindows) {
            if (!window.equals(parentWindow)) {
                driver.switchTo().window(window);
                break;
            }
        }

        // Get title or URL
        String actualTitle = driver.getTitle();
        String expectedTitle = "Selenium";   // expected title

        System.out.println("New Window Title: " + actualTitle);

        if (actualTitle.contains(expectedTitle)) {
            System.out.println("PASS");
        } else {
            System.out.println("FAIL");
        }

        driver.quit();
    }
}

Sample Output
New Window Title: Selenium
PASS

2. Handle Prompt Alert, enter text and print it

URL: https://www.selenium.dev/selenium/web/alerts.html

✔ Click prompt button
✔ Switch to alert
✔ Enter text
✔ Print entered text

Selenium Java Program
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.Alert;

public class PromptAlert {

    public static void main(String[] args) {

        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        WebDriver driver = new ChromeDriver();
        driver.manage().window().maximize();

        driver.get("https://www.selenium.dev/selenium/web/alerts.html");

        // Click prompt alert button
        driver.findElement(By.id("prompt")).click();

        // Switch to alert
        Alert alert = driver.switchTo().alert();

        // Enter text
        String message = "Hello Selenium";
        alert.sendKeys(message);

        // Print entered text
        System.out.println("Entered Message: " + message);

        // Accept alert
        alert.accept();

        driver.quit();
    }
}

Console Output
Entered Message: Hello Selenium
