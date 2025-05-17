from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.firefox.service import Service
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.firefox.options import Options
import time


def test_avito_ru():
    driver = webdriver.Firefox()

    try:
        driver.get("https://www.avito.ru/")
        # time.sleep(20)
        driver.maximize_window()

        event = driver.find_element(By.CSS_SELECTOR, "a.index-module-nav-link-YtJag:nth-child(3)")
        event.click()
        print("Кнопка - Вход и регистрация нажата")
        time.sleep(3)

        event = driver.find_element(By.XPATH, "//input[@name='login']")
        event.send_keys("+7 978 812-67-41")
        print("Введен логин")
        time.sleep(5)

        event = driver.find_element(By.XPATH, "//input[@name='password']")
        event.send_keys("VaD9iSHondaAccord1999")
        print("Введен пароль")
        time.sleep(5)


        # event = driver.find_element(By.XPATH, "//button[@name='submit']")#copy "/html/body/div[6]/div/div/div/div/div/div/div/div[1]/form/button" другой путь к кнопке
        # event.click()
        # time.sleep(10)


        #Закрыть окно авторизации
        event = driver.find_element(By.CSS_SELECTOR, ".css-89rnpj")
        event.click()
        print("Окно авторизации закрыто")
        time.sleep(3)


        event = driver.find_element(By.XPATH, "/html/body/div[1]/div/buyer-pages-mfe-location/div/div/div/div[2]/div/div[1]/div/div/div[3]/div[2]/div[2]/div/div/label/div/div/div/input")
        time.sleep(4)
        event.send_keys("iphone")
        time.sleep(2)
        event = driver.find_element(By.CSS_SELECTOR, ".styles-module-text_size_s-GNjbH > span:nth-child(1)")
        event.click()
        time.sleep(4)
        print("В поиск введен iphone и нажата кнопка найти!")
        driver.back()

        elem = driver.find_element(By.XPATH, "/html/body/div[1]/div/buyer-pages-mfe-location/div/div/div/div[2]/div/div[1]/div/div/div[3]/div[2]/div[2]/div/div/label/div/div/div/input")
        elem.send_keys("Honda")
        elem.send_keys(Keys.RETURN)
        time.sleep(3)

        elem = driver.find_element(By.XPATH, "/html/body/div[1]/div/buyer-pages-mfe-location/div/div/div/div[2]/div/div[2]/div[3]/div[3]/div[3]/div[2]/div[1]/div/div/div[2]/div[1]")
        elem.click()
        time.sleep(3)

        to_add_favourites = WebDriverWait(driver, 10).until((
            EC.element_to_be_clickable((By.CSS_SELECTOR, ".FavoritesFilled-module-mask-THBMo"))
        ))
        to_add_favourites.click()
        time.sleep(5)

        elem = driver.find_element(By.XPATH, "/html/body/div[1]/div/div[3]/div[1]")
        elem.click()
        time.sleep(5)


        events_elements = driver.find_element(By.XPATH, "/html/body/div[1]/div/buyer-pages-mfe-location/div/div/div/div[2]/div/div[2]/div[3]/div[2]/div[1]/div/div/a[1]")
        events_elements.click()
        print("Кнопка авто нажата")
        time.sleep(2)

        driver.back()
        time.sleep(2)

        events_elements = driver.find_element(By.XPATH, "/html/body/div[1]/div/buyer-pages-mfe-location/div/div/div/div[2]/div/div[2]/div[3]/div[2]/div[1]/div/div/a[2]")
        events_elements.click()
        print("Кнопка недвижимость нажата")
        time.sleep(2)

        driver.back()
        time.sleep(2)

        events_elements = driver.find_element(By.XPATH, "/html/body/div[1]/div/buyer-pages-mfe-location/div/div/div/div[2]/div/div[2]/div[3]/div[2]/div[1]/div/div/a[3]")
        events_elements.click()
        print("Кнопка работа нажата")
        time.sleep(2)

        driver.back()
        time.sleep(2)

        events_elements = driver.find_element(By.XPATH, "/html/body/div[1]/div/buyer-pages-mfe-location/div/div/div/div[2]/div/div[2]/div[3]/div[2]/div[1]/div/div/a[4]")
        events_elements.click()
        print("Кнопка одежда нажата")
        time.sleep(2)

        driver.back()
        time.sleep(2)

        events_elements = driver.find_element(By.XPATH, "/html/body/div[1]/div/buyer-pages-mfe-location/div/div/div/div[2]/div/div[2]/div[3]/div[2]/div[1]/div/div/a[5]")
        events_elements.click()
        print("Кнопка хобби и отдых нажата")
        time.sleep(2)
        driver.back()
        time.sleep(2)

    finally:
        driver.quit()


if __name__ == "__main__":
    test_avito_ru()
