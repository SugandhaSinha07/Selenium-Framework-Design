# Selenium Automation Framework (Java + TestNG)

A scalable test automation framework for a demo e-commerce web application, built with **Selenium WebDriver**, **Java**, **TestNG** and **Maven**, using the **Page Object Model**, data-driven testing and **Extent Reports**.

## Tech stack
- Selenium WebDriver 4
- Java
- TestNG (suites, groups, listeners, retry)
- Maven (profiles for each suite)
- Extent Reports 5
- Jackson (JSON test data)

## Framework features
- **Page Object Model**: page classes in `src/main/java/.../pageobjects` (LandingPage, ProductCatalogue, CartPage, CheckOutPage, ConfirmationPage, OrderPage)
- **Reusable components**: `AbstractComponent` with shared waits and header navigation
- **Base test**: `BaseTest` handles browser set-up (Chrome, Chrome headless, Firefox, Edge) from `GlobalData.properties` or `-Dbrowser`
- **Data-driven tests**: JSON test data with a TestNG `@DataProvider` (`data/PurchaseOrder.json`, `DataReader`)
- **Reporting**: Extent Reports with automatic screenshots on failure through a TestNG `Listeners` class
- **Retry**: flaky tests re-run automatically (`Retry` / `IRetryAnalyzer`)
- **Test suites**: `testSuites/` – Regression, Purchase, ErrorValidation

## Test scenarios
- Submit order end to end (login → add product → checkout → confirm order → verify in order history)
- Login error validation
- Product validation in the cart

## How to run
```bash
# set the demo-account password (never commit real passwords)
export TEST_PASSWORD="your_test_password"

mvn test -PRegression
mvn test -PPurchase
mvn test -PErrorValidationTest

# run on a different browser
mvn test -PRegression -Dbrowser=firefox
mvn test -PRegression -Dbrowser=chromeheadless
```
The Extent report is generated at `reports/index.html`.

## Author
**Sugandha Sinha** – QA Automation & Performance Engineer
[LinkedIn](https://www.linkedin.com/in/sugandha-sinha-b158062b)
