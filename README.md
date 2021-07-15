package ru.autoDrom;

import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.SendKeysAction;

import javax.swing.text.html.parser.AttributeList;
import javax.swing.text.html.parser.Element;
import java.util.concurrent.TimeUnit;

public class TestClass {

    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "C:\\Users\\Denis\\IdeaProjects\\ProgectMaven\\driver\\chromedriver.exe");
        ChromeDriver driver = new ChromeDriver();

        String log = ("***");       //мой логин
        String pass = ("***");      //мой пароль

        driver.manage().window().maximize();
        driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);

        driver.get("https://auto.drom.ru/");
        WebElement mainpage = driver.findElement(By.xpath("/html/body/div[2]/div[2]/div[1]/div/div[3]/a"));
        mainpage.click();

        WebElement sign = driver.findElement(By.xpath("//*[@id=\"sign\"]"));
        WebElement password = driver.findElement(By.xpath("//*[@id=\"password\"]"));
        WebElement login = driver.findElement(By.xpath("//*[@id=\"signbutton\"]"));
        sign.sendKeys(log);
        password.sendKeys(pass);
        login.click();

        WebElement Audi = driver.findElement(By.xpath("/html/body/div[2]/div[5]/div[1]/div[1]/div[7]/div[1]/div[1]/div/a"));
        Audi.click();
        WebElement Variant1 = driver.findElement(By.xpath("/html/body/div[2]/div[5]/div[1]/div[1]/div[6]/div/div[2]/a[1]"));
        Variant1.click();
        WebElement addFavorites = driver.findElement(By.xpath("/html/body/div[2]/div[4]/div[1]/div[1]/div[2]/div[1]/div[3]/div[1]/div[1]/span"));
        addFavorites.click();
        WebElement Announcement1 = driver.findElement(By.xpath("/html/body/div[2]/div[2]/div[2]/div/div[1]/div/div[5]"));
        String x = Announcement1.getText();
        System.out.println(x);

        WebElement myFavorites = driver.findElement(By.xpath("/html/body/div[2]/div[2]/div[1]/div/div[3]/div[2]/div/a[2]/div"));
        myFavorites.click();
        WebElement myFavorites1 = driver.findElement(By.xpath("//*[@id=\"bulletinId\"]"));
        myFavorites1.click();
        WebElement Announcement2 = driver.findElement(By.xpath("/html/body/div[2]/div[2]/div[2]/div/div[1]/div/div[5]"));
        String y = (Announcement2.getText());
        System.out.println(y);
        System.out.println();

        if (x == y) {
        System.out.println("Failure");
        } else {
            System.out.println("Succses");
        }

        driver.quit();
    }
}
