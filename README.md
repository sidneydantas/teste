import time
from selenium import webdriver
from selenium.webdriver.firefox.firefox_profile import FirefoxProfile


def waitSecs(function, pathButton, timeToTry=30):
    count=0
    while count < timeToTry:
        try:
            espera = function(pathButton)
            break
        except:
            time.sleep(1)
            count=count+1
            print('loading...')
    return espera

def crwl():

    profile = FirefoxProfile()
    site='http://www.b3.com.br/pt_br/market-data-e-indices/servicos-de-dados/market-data/consultas/mercado-de-derivativos/indicadores/indicadores-financeiros/'
    driver = webdriver.Firefox(firefox_profile=profile)
    driver.get(site)

    buscar = waitSecs(driver.find_element_by_xpath, "/html/body/div[5]/div/div/div[2]/div[3]/table/tbody/tr/td/span", 30)
    dolar = buscar.text
    print(dolar)
    driver.close()
crwl()
