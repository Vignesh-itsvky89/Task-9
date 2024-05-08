import os
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
import time
from selenium.webdriver.common.by import By
paths = r"D:\Automation study\Python Programming\Requirement\chromedriver.exe"
os.environ["PATH"] += os.pathsep + os.path.dirname(paths)
chrome_options = Options()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
time.sleep(2)
driver.get("https://www.saucedemo.com/")
driver.maximize_window()
username = driver.find_element(By.ID,"user-name")
time.sleep(4)
username.click()
time.sleep(2)
username.send_keys("standard_user")
time.sleep(4)
password = driver.find_element(By.ID, "password")
password.click()
time.sleep(2)
password.send_keys("secret_sauce")
time.sleep(2)
login = driver.find_element(By.ID, "login-button")
login.click()
print("Title of webpage:", driver.title)
print("Current URL of webpage:", driver.current_url)
file = open(r"D:\Automation study\Python Programming\Task files\Task 9\webpage_task_11.txt", "x")
p = (driver.find_element(By.XPATH, '//*[@id="root"]'))
files = open(r"D:\Automation study\Python Programming\Task files\Task 9\webpage_task_11.txt", 'w') # write a file
files.write(p.text)
files.close()
file.close()
driver.quit()