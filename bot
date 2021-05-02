from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import time
import numpy as np
from selenium.common.exceptions import NoSuchElementException

driver = webdriver.Chrome('C:/Users/USER/Downloads/chromedriver_win32/chromedriver.exe')
driver.get("https://gost-chat.herokuapp.com/login")
elem_login=driver.find_element_by_id("name")
elem_login.send_keys("네 말 수집 봇")
elem_login.send_keys(Keys.RETURN)

def check_op():
    try:
        driver.find_element_by_class_name("op")
    except NoSuchElementException:
        return False
    return True

# exit
# inputBox_input
names = ["개발자"]
hi_txt = ["안녕하세요!"]
cnt = 0
while 1:
    elem_ischat = driver.find_element_by_id("targetProfile_content_name")
    if elem_ischat.text != "...":
        elem_input=driver.find_element_by_id("inputBox_input")

        if check_op():
            elem_op = driver.find_element_by_class_name("op")
            elem_input.send_keys(elem_op.text + " 라고 말하셨군요!")
            elem_input.send_keys(Keys.RETURN)

            same = False
            elem_name = driver.find_element_by_id("targetProfile_content_name").text
            for i in range(0,len(names)):
                if hi_txt[i] == elem_op.text and names[i] == elem_name:
                    print("Same")
                    same = True
            if same == False:
                hi_txt.append(elem_op.text)
                names.append(elem_name)

            elem_input.send_keys("다른 분의 인삿말입니다.")
            elem_input.send_keys(Keys.RETURN)
            rand_num = np.random.randint(0, len(names) - 1)
            elem_input.send_keys(names[rand_num] + " : " + hi_txt[rand_num])
            elem_input.send_keys(Keys.RETURN)
            elem_input.send_keys("다음에 뵙겠습니다!")
            elem_input.send_keys(Keys.RETURN)
            print(names)
            print(hi_txt)
            time.sleep(5)
            elem_exit = driver.find_element_by_id("exit")
            elem_exit.click()
