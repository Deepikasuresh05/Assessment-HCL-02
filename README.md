# Assessment-HCL-02
## Name: Deepika S
## Reg: No : 212223230039

### Code
```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from getpass import getpass
import time

options = webdriver.ChromeOptions()
options.page_load_strategy = "eager"

driver = webdriver.Chrome(options=options)

wait = WebDriverWait(driver, 20)

driver.maximize_window()

driver.get("https://www.amazon.in/")

search = wait.until(
    EC.element_to_be_clickable(
        (By.ID, "twotabsearchtextbox")
    )
)

search.send_keys("Women watches")
search.send_keys(Keys.ENTER)

add_buttons = wait.until(
    EC.presence_of_all_elements_located(
        (By.CSS_SELECTOR, "input[name='submit.addToCart']")
    )
)

for button in add_buttons:
    if button.is_displayed():
        driver.execute_script(
            "arguments[0].click();",
            button
        )
        break

time.sleep(3)

print("Wireless mouse added to cart")

driver.get("https://www.amazon.in/gp/cart/view.html")

time.sleep(4)

print("Cart opened")

checkout = wait.until(
    EC.element_to_be_clickable(
        (By.NAME, "proceedToRetailCheckout")
    )
)

checkout.click()

time.sleep(5)

print("Checkout page opened")

mobile_number = input("Enter your Amazon mobile number: ")

mobile_box = wait.until(
    EC.element_to_be_clickable(
        (By.ID, "ap_email_login")
    )
)

mobile_box.clear()
mobile_box.send_keys(mobile_number)

print("Mobile number entered")

continue_button = wait.until(
    EC.element_to_be_clickable(
        (By.ID, "continue")
    )
)

continue_button.click()

time.sleep(4)

print("Password page opened")

password = getpass("Enter your Amazon password: ")

password_box = wait.until(
    EC.element_to_be_clickable(
        (By.NAME, "password")
    )
)

password_box.clear()
password_box.send_keys(password)

print("Password entered")

sign_in = wait.until(
    EC.element_to_be_clickable(
        (By.ID, "signInSubmit")
    )
)

sign_in.click()

time.sleep(5)

print("Sign in submitted")

security_code = input(
    "Enter the security code received from Amazon: "
)

otp_box = wait.until(
    EC.element_to_be_clickable(
        (By.ID, "input-box-otp")
    )
)

otp_box.clear()
otp_box.send_keys(security_code)

print("Security code entered")

submit_code = wait.until(
    EC.element_to_be_clickable(
        (By.ID, "cvf-submit-otp-button")
    )
)

submit_code.click()

time.sleep(7)

print("Security verification completed")

print("Reached checkout/payment page")

input("Press Enter to close the browser...")

driver.quit()
```

### Output


<img width="1919" height="874" alt="Screenshot 2026-10-07 103427" src="https://github.com/user-attachments/assets/312c7d03-6f78-4112-a134-2c51a0d0d4e1" />










































