Web Link: https://securitycipher.com/docs/captcha-bypass/ <br><br>
Consider these techniques for bypassing captchas during penetration testing or bug bounty.

## Method 1: Reuse Previous Captcha
This technique involves using a captcha code that you’ve seen or solved before, assuming that the same code will work again multiple times.

```
POST /submit-form HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded

captcha=ABC123 #{ola_captch_value}
```
In this example, we are submitting the same captcha code “ABC123” multiple times, hoping that one of the attempts will be accepted by the server.

## Method 2: Submit Empty Captcha
Trying to bypass the captcha by leaving the captcha field empty when submitting a form.

```
POST /submit-form HTTP/1.1 
Host: example.com 
Content-Type: application/x-www-form-urlencoded 

captcha=
```
## Method 3: Alter Data Format
Changing the format in which data is sent to the server, such as converting it to JSON or plain text, in the hope that the captcha won’t be validated.

A sample POST request with JSON data instead of the expected XML data:

```
POST /submit-data HTTP/1.1 
Host: example.com 
Content-Type: application/json 

{ 
"key": "value", 
"captcha": "YourCaptchaCodeHere" 
}
```
## Method 4: Change Request Method
Modify the way you send requests to the server by switching between different HTTP request methods like GET, POST, or PUT.

A sample GET request instead of the expected POST request:

```
GET /submit-data?key=value&captcha=YourCaptchaCodeHere HTTP/1.1 
Host: example.com
```
## Method 5: Manipulate Headers
Using custom headers like X-Forwarded-For, X-Remote-IP, X-Original-IP, X-Remote-Addr, etc., to make it appear as though the requests are coming from different IP addresses, thereby avoiding captcha validation.

A sample GET request with a custom “X-Forwarded-For” header:

```
GET /page HTTP/1.1 
Host: example.com 
X-Forwarded-For: 127.0.0.1
```
## Method 6: Inspect Parameters
Always thoroughly examine the entire request (body, headers, or uri part) and understand the purpose of each parameter. By changing certain parameter values, you might find a way to bypass the captcha.

```
POST /submit-form HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded

user_id=12345
captcha=WXYZ789
```
In this case, the “user_id” parameter might be related to captcha validation. By experimenting with different values for “user_id,” you may discover a way to bypass the captcha.

## Method 7: Automate with Tools
Using automation tools like Selenium or OCR (Optical Character Recognition) software to automatically identify and solve captchas.

Here’s a Python Selenium script that automates captcha entry:

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

url = "https://example.com/login"
username = "your_username"
password = "your_password"
driver = webdriver.Chrome(executable_path='/path/to/chromedriver')

try:
driver.get(url)
username_field = driver.find_element(By.ID, "username_field_id")
password_field = driver.find_element(By.ID, "password_field_id")
username_field.send_keys(username)
password_field.send_keys(password)

WebDriverWait(driver, 10).until(EC.presence_of_element_located((By.ID, "captcha_element_id")))
login_button = driver.find_element(By.ID, "login_button_id")
login_button.click()
WebDriverWait(driver, 10).until(EC.url_to_be("https://example.com/dashboard"))
except Exception as e:
print("An error occurred:", str(e))

finally:
# Close the WebDriver
driver.quit()
```
## Method 8: Human-Based Captcha Solving Services
Instead of automated methods, you can use human-based captcha-solving services where real individuals solve captchas for you in exchange for a fee.
