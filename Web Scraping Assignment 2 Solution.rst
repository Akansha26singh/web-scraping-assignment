.. code:: ipython3

    import selenium
    import pandas as pd
    from selenium import webdriver
    import warnings
    warnings.filterwarnings("ignore")
    import time

.. code:: ipython3

    driver=webdriver.Edge(r"C:/Python/msedgedriver.exe")
    driver.get('https://www.naukri.com/')
    search_field_designation=driver.find_element_by_class_name("suggestor-input")
    search_field_designation.send_keys("Data Analyst")

.. code:: ipython3

    search_field_location=driver.find_element_by_xpath('/html/body/div/div[2]/div[3]/div/div/div[3]/div/div/div/input')
    search_field_location.send_keys("Bangalore")

.. code:: ipython3

    search_button=driver.find_element_by_xpath("/html/body/div/div[2]/div[3]/div/div/div[6]")
    search_button.click()

.. code:: ipython3

    job_titles1=[]
    company_names1=[]
    locations_list1=[]
    experience_list1=[]

.. code:: ipython3

    title_tags1=driver.find_elements_by_xpath('//a[@class="title fw500 ellipsis"]') 
    title_tags1[0:4]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="fd76463b-0467-4dc0-b61f-5c0ce17928dd")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="17e854e2-3010-4ce2-a742-37a0f301bbae")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="b8b06866-ea66-461b-b493-afe336c38ca3")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="365bda55-f4e6-4f3d-8b40-3cbb55a8062d")>]



.. code:: ipython3

    for i in title_tags1:             
        title=i.text                   
        job_titles1.append(title)     
    job_titles1[0:4] 




.. parsed-literal::

    ['Senior Data Analyst',
     'Data Analyst- customer facing',
     'Sr Data Analyst II',
     'Data Analyst']



.. code:: ipython3

    companies_tags1=driver.find_elements_by_xpath("//a[@class='subTitle ellipsis fleft']")   
    companies_tags1[0:4]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="d4e424df-e473-4a85-b4fa-387c3bb86e79")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="90c24afa-7813-4b4e-8859-0f8b557dbd41")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="33c781ce-6cbe-480f-bb38-0561890dbf88")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="03207336-a4a8-4303-bab6-a8014c31b286")>]



.. code:: ipython3

    for i in companies_tags1:             
        company_name=i.text                  
        company_names1.append(company_name)       
    company_names1[0:4]




.. parsed-literal::

    ['Thomson Reuters',
     'Synamedia',
     'IHS Markit',
     'VOLVO ASSET FINANCE INDIA PRIVATE LIMITED']



.. code:: ipython3

    experience_tags1=driver.find_elements_by_xpath("//li[@class='fleft grey-text br2 placeHolderLi experience'] /span")
    experience_tags1[0:4]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="d8835dab-7625-432d-afb2-10556c9a6513")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="e0021dfc-803c-46be-b54b-18aff596cfbc")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="4df54e0b-ee8a-457e-995e-f43cc499d945")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="7901b47b-579e-4581-8cea-2b4ff1a8c2d7")>]



.. code:: ipython3

    for i in experience_tags1:             
        experience=i.text                  
        experience_list1.append(experience)      
    experience_list1[0:4]




.. parsed-literal::

    ['2-4 Yrs', '0-3 Yrs', '3-6 Yrs', '2-4 Yrs']



.. code:: ipython3

    locations_tags1=driver.find_elements_by_xpath("//li[@class='fleft grey-text br2 placeHolderLi location']/span[1]")
    locations_tags1[0:4]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="484aa1f7-d4b6-49d6-8db1-8054209117d3")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="784d92b1-7e1f-45b0-93f6-6e5aa50644b0")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="cce1d0f6-4a18-49c6-b799-bc4e8fac4422")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d7fefc1143c3a895bb09b73becc7953e", element="02a29772-b152-4a12-a59e-ad2845eb4015")>]



.. code:: ipython3

    for i in locations_tags1:
        location=i.text
        locations_list1.append(location)
    locations_list1[0:4]




.. parsed-literal::

    ['Bangalore/Bengaluru',
     'Bangalore/Bengaluru',
     'Gurgaon/Gurugram, Bangalore/Bengaluru',
     'Bangalore/Bengaluru']



.. code:: ipython3

    print(len(job_titles1),len(company_names1),len(experience_list1),len(locations_list1))


.. parsed-literal::

    20 20 20 20
    

.. code:: ipython3

    import pandas as pd
    jobs1=pd.DataFrame({})
    jobs1['title']=job_titles1
    jobs1['company']=company_names1
    jobs1['experience_required']=experience_list1
    jobs1['location']=locations_list1

.. code:: ipython3

    jobs1




.. raw:: html

    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    
        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>title</th>
          <th>company</th>
          <th>experience_required</th>
          <th>location</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>Senior Data Analyst</td>
          <td>Thomson Reuters</td>
          <td>2-4 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>1</th>
          <td>Data Analyst- customer facing</td>
          <td>Synamedia</td>
          <td>0-3 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Sr Data Analyst II</td>
          <td>IHS Markit</td>
          <td>3-6 Yrs</td>
          <td>Gurgaon/Gurugram, Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>3</th>
          <td>Data Analyst</td>
          <td>VOLVO ASSET FINANCE INDIA PRIVATE LIMITED</td>
          <td>2-4 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>4</th>
          <td>Hiring For Data Analyst with SAP ABAP &amp; BW - C...</td>
          <td>MILLION MINDS INFOTECH PRIVATE LIMITED</td>
          <td>7-10 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>5</th>
          <td>Senior Business Analyst - Data Sciences and Ad...</td>
          <td>Vmware</td>
          <td>3-7 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>6</th>
          <td>Business and Data Analyst</td>
          <td>CAREERDOST ENTERPRISE</td>
          <td>0-5 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>7</th>
          <td>Senior Data Analyst | Lululemon</td>
          <td>TALENT500 TECH (INDIA) PRIVATE LIMITED</td>
          <td>5-8 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>8</th>
          <td>Urgent hiring For Senior Data Analyst</td>
          <td>upGrad</td>
          <td>2-7 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>9</th>
          <td>Senior Data Analyst</td>
          <td>Capco</td>
          <td>7-12 Yrs</td>
          <td>Pune, Gurgaon/Gurugram, Chennai, Bangalore/Ben...</td>
        </tr>
        <tr>
          <th>10</th>
          <td>Senior Data Analyst</td>
          <td>Gsn Games India</td>
          <td>3-7 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>11</th>
          <td>Jr . Data Analyst</td>
          <td>Armorblox</td>
          <td>0-2 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>12</th>
          <td>Data Analyst</td>
          <td>G S E-COMMERCE PVT LTD</td>
          <td>4-7 Yrs</td>
          <td>Bangalore/Bengaluru(Jayanagar)</td>
        </tr>
        <tr>
          <th>13</th>
          <td>Data Analyst - IIM/ISB/MDI/FMS/SP Jain</td>
          <td>K12 Techno Services Pvt Ltd</td>
          <td>4-9 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>14</th>
          <td>SQL Data Analyst</td>
          <td>Sequoia Consulting Group</td>
          <td>2-4 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>15</th>
          <td>SAS Analyst / data Analyst / Business analyst ...</td>
          <td>Leading US MNC into analytics</td>
          <td>2-7 Yrs</td>
          <td>Bangalore/Bengaluru, Delhi / NCR, Mumbai (All ...</td>
        </tr>
        <tr>
          <th>16</th>
          <td>Analyst, Item Data</td>
          <td>HUDSON'S BAY SERVICES PRIVATE LIMITED</td>
          <td>0-2 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>17</th>
          <td>Data Analyst II</td>
          <td>Cerner</td>
          <td>6-10 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>18</th>
          <td>Data Analyst - Python / SQL</td>
          <td>Myntra</td>
          <td>1-4 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>19</th>
          <td>Reference Data Analyst</td>
          <td>Deutsche Bank</td>
          <td>2-5 Yrs</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
      </tbody>
    </table>
    </div>




.. code:: ipython3

    driver=webdriver.Edge(r"C:/Python/msedgedriver.exe")

.. code:: ipython3

    driver=webdriver.Edge(r"C:/Python/msedgedriver.exe")
    driver.get('https://www.naukri.com/')
    search_field_designation=driver.find_element_by_class_name("suggestor-input")
    search_field_designation.send_keys("Data Scientist")

.. code:: ipython3

    search_field_location=driver.find_element_by_xpath('/html/body/div/div[2]/div[3]/div/div/div[3]/div/div/div/input')
    search_field_location.send_keys("Bangalore")

.. code:: ipython3

    search_button=driver.find_element_by_xpath("/html/body/div/div[2]/div[3]/div/div/div[6]")
    search_button.click()

.. code:: ipython3

    job_titles2=[]
    company_names2=[]
    locations_list2=[]

.. code:: ipython3

    title_tags2=driver.find_elements_by_xpath('//a[@class="title fw500 ellipsis"]') 
    title_tags2[0:4]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="3ad5e0f55583a9ae12c275d540c2f764", element="61a7da11-2a0e-47e8-86dd-0cc25c41922c")>,
     <selenium.webdriver.remote.webelement.WebElement (session="3ad5e0f55583a9ae12c275d540c2f764", element="621d7cce-79b3-42d2-b87b-6ac735b3e4cb")>,
     <selenium.webdriver.remote.webelement.WebElement (session="3ad5e0f55583a9ae12c275d540c2f764", element="03d6620d-345a-4e3e-82fc-d8177c8e6232")>,
     <selenium.webdriver.remote.webelement.WebElement (session="3ad5e0f55583a9ae12c275d540c2f764", element="cfa6c205-6336-4182-be5c-f4dfd14b4dfb")>]



.. code:: ipython3

    for i in title_tags2:             
        title=i.text                   
        job_titles2.append(title)     
    job_titles2[0:4] 




.. parsed-literal::

    ['Senior Data Scientist',
     'Data Scientist: Advanced Analytics',
     'Data Scientist',
     'Data Scientist: Artificial Intelligence']



.. code:: ipython3

    companies_tags2=driver.find_elements_by_xpath("//a[@class='subTitle ellipsis fleft']")   
    companies_tags2[0:4]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="3ad5e0f55583a9ae12c275d540c2f764", element="d7d19dce-49f9-4bf8-a882-7d72b414f166")>,
     <selenium.webdriver.remote.webelement.WebElement (session="3ad5e0f55583a9ae12c275d540c2f764", element="aa645ec0-f9ea-4b93-8d7f-13bade4e2624")>,
     <selenium.webdriver.remote.webelement.WebElement (session="3ad5e0f55583a9ae12c275d540c2f764", element="4299a169-78d9-43d4-99a1-c32e08130edf")>,
     <selenium.webdriver.remote.webelement.WebElement (session="3ad5e0f55583a9ae12c275d540c2f764", element="06d1f0e9-e657-45dc-9d74-3ad6bea972da")>]



.. code:: ipython3

    for i in companies_tags2:             
        company_name=i.text                  
        company_names2.append(company_name)       
    company_names2[0:4]




.. parsed-literal::

    ['Fractal Analytics', 'IBM', 'VISA', 'IBM']



.. code:: ipython3

    locations_tags2=driver.find_elements_by_xpath("//li[@class='fleft grey-text br2 placeHolderLi location']/span[1]")
    locations_tags2[0:4]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="3ad5e0f55583a9ae12c275d540c2f764", element="894ec33f-671b-4ae8-beac-3c032ba76773")>,
     <selenium.webdriver.remote.webelement.WebElement (session="3ad5e0f55583a9ae12c275d540c2f764", element="8985f7f8-4bc9-4e6a-82e6-1bccb59e022f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="3ad5e0f55583a9ae12c275d540c2f764", element="4ed42b13-9911-4922-a69c-7fbf08cdf9a4")>,
     <selenium.webdriver.remote.webelement.WebElement (session="3ad5e0f55583a9ae12c275d540c2f764", element="e0baa3bb-ccfc-4c81-ab6c-f0a5fbd07c4b")>]



.. code:: ipython3

    for i in locations_tags2:
        location=i.text
        locations_list2.append(location)
    locations_list2[0:4]




.. parsed-literal::

    ['Bangalore/Bengaluru',
     'Bengaluru/Bangalore',
     'Bangalore/Bengaluru',
     'Bangalore/Bengaluru']



.. code:: ipython3

    print(len(job_titles2),len(company_names2),len(locations_list2))


.. parsed-literal::

    20 20 20
    

.. code:: ipython3

    import pandas as pd
    jobs2=pd.DataFrame({})
    jobs2['title']=job_titles2
    jobs2['company']=company_names2
    jobs2['location']=locations_list2

.. code:: ipython3

    jobs2




.. raw:: html

    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    
        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>title</th>
          <th>company</th>
          <th>location</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>Senior Data Scientist</td>
          <td>Fractal Analytics</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>1</th>
          <td>Data Scientist: Advanced Analytics</td>
          <td>IBM</td>
          <td>Bengaluru/Bangalore</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Data Scientist</td>
          <td>VISA</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>3</th>
          <td>Data Scientist: Artificial Intelligence</td>
          <td>IBM</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>4</th>
          <td>Data Scientist: Artificial Intelligence</td>
          <td>IBM</td>
          <td>Bengaluru/Bangalore</td>
        </tr>
        <tr>
          <th>5</th>
          <td>Data Scientist: Artificial Intelligence</td>
          <td>IBM</td>
          <td>Bengaluru/Bangalore</td>
        </tr>
        <tr>
          <th>6</th>
          <td>Data Scientist: Artificial Intelligence</td>
          <td>IBM</td>
          <td>Bengaluru/Bangalore</td>
        </tr>
        <tr>
          <th>7</th>
          <td>Data Scientist, Machine Learning (AIML)</td>
          <td>Fractal Analytics</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>8</th>
          <td>Sr. Data Scientist</td>
          <td>HUDSON'S BAY SERVICES PRIVATE LIMITED</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>9</th>
          <td>Lead Data Scientist</td>
          <td>TransOrg Solutions Services (P) Ltd.</td>
          <td>Bangalore/Bengaluru, Delhi / NCR, Mumbai (All ...</td>
        </tr>
        <tr>
          <th>10</th>
          <td>Senior Data Scientist</td>
          <td>Walmart</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>11</th>
          <td>Cognitive/AI Senior Data Scientist</td>
          <td>IBM</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>12</th>
          <td>Lead - Data Scientist</td>
          <td>Applied Materials</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>13</th>
          <td>Data Scientist</td>
          <td>Aurigo Software Technologies Pvt Ltd</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>14</th>
          <td>DATA SCIENTIST</td>
          <td>Kyndryl</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>15</th>
          <td>Data Scientist</td>
          <td>Aidetic Software Pvt Ltd</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>16</th>
          <td>Applied Data Scientist</td>
          <td>Refinitiv</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
        <tr>
          <th>17</th>
          <td>Senior Associate - Data Scientist</td>
          <td>Affine</td>
          <td>Remote</td>
        </tr>
        <tr>
          <th>18</th>
          <td>Data Scientist</td>
          <td>IBM</td>
          <td>Bengaluru/Bangalore</td>
        </tr>
        <tr>
          <th>19</th>
          <td>Data Scientist: Artificial Intelligence</td>
          <td>IBM</td>
          <td>Bangalore/Bengaluru</td>
        </tr>
      </tbody>
    </table>
    </div>







.. code:: ipython3

    driver=webdriver.Edge(r"C:/Python/msedgedriver.exe")

.. code:: ipython3

    driver=webdriver.Edge(r"C:/Python/msedgedriver.exe")
    driver.get('https://www.naukri.com/')
    search_field_designation=driver.find_element_by_class_name("suggestor-input")
    search_field_designation.send_keys("Data Scientist")

.. code:: ipython3

    search_field_location=driver.find_element_by_xpath('/html/body/div/div[2]/div[3]/div/div/div[3]/div/div/div/input')
    search_field_location.send_keys("Delhi")

.. code:: ipython3

    search_button=driver.find_element_by_xpath("/html/body/div/div[2]/div[3]/div/div/div[6]")
    search_button.click()

.. code:: ipython3

    salary_filter_button=driver.find_element_by_xpath("/html/body/div[1]/div[3]/div[2]/section[1]/div[2]/div[1]/div[2]/div[1]/label/p/span[1]")
    salary_filter_button.click()


.. code:: ipython3

    job_titles3=[]
    company_names3=[]
    locations_list3=[]
    experience_list3=[]

.. code:: ipython3

    title_tags3=driver.find_elements_by_xpath('//a[@class="title fw500 ellipsis"]') 
    title_tags3[0:10]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="46a8179f-0dc2-42af-9412-cce960759343")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="abf82fdf-245a-421b-a398-09a0f621fb2d")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="10114edf-e107-4918-85e1-0d7ad8ab61e4")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="85ad56a6-91b6-4a4a-887a-7981e4195c72")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="7b2d50e0-0284-454c-82f3-bca53f69b655")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="c38d051b-af8c-4803-b2c3-cab5716282c1")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="ed7eb6c9-cbd1-457c-a7f0-7d5bc1f2d5ab")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="2465ff8b-4133-4a14-b805-8f2c79bc9a2b")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="b084e7fc-6d20-49a3-af97-c94649acb249")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="9bd3126b-0290-480c-86de-aabe334253df")>]



.. code:: ipython3

    for i in title_tags3:             
        title=i.text                   
        job_titles3.append(title)     
    job_titles3[0:10] 




.. parsed-literal::

    ['Lead Data Scientist',
     'Data Scientist/Data Engineer',
     'Hiring Senior Data Scientist - AI ( Remote) || Hanu',
     'Urgent Hiring For AI Data Scientist',
     'Data Scientist',
     'Hiring For Senior Data Scientist || Noida/Hyderabad',
     'Hiring For Data Scientist + Python/R+ Predictive Modeling',
     'Data Scientist -Machine Learning with Python',
     'Data Scientist',
     'Principal Data Scientist- 13+ years exp || Remote']



.. code:: ipython3

    companies_tags3=driver.find_elements_by_xpath("//a[@class='subTitle ellipsis fleft']")
    companies_tags3[0:10]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="1a0398ea-ba1b-43a5-9c91-9f17e16e8191")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="167ac8d7-050e-4d31-af62-9f36113506cd")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="9af1e619-9116-4201-82b8-9f6b9f210b31")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="d5068a95-c762-41a9-b1e1-d923cb1d791e")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="20963a2a-9a66-456e-803f-5ab3c3b2da4b")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="f2d445f0-97ff-4c68-a2f9-46212bcc7686")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="761d4241-709d-42c3-b43b-85fe8602b6ce")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="f79c7392-ee39-49f7-b714-8d9f36e9a852")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="da3c9d49-b122-4f91-bf80-792669860ce2")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="bbf5160b-27eb-4ff0-a4f6-ff3093c8f784")>]



.. code:: ipython3

    for i in companies_tags3:             
        company_name=i.text                  
        company_names3.append(company_name)       
    company_names3[0:10]




.. parsed-literal::

    ['TransOrg Solutions Services (P) Ltd.',
     'UST',
     'Hanu Software Solutions',
     'Ashkom Media India Private Limited',
     'Tiger Analytics India LLP',
     'Tokopedia',
     'Genpact',
     'Genpact',
     'Paytm',
     'Hanu Software Solutions']



.. code:: ipython3

    experience_tags3=driver.find_elements_by_xpath("//li[@class='fleft grey-text br2 placeHolderLi experience'] /span")
    experience_tags3[0:10]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="8f3043fc-1ec8-441a-becc-7653ffdb88ca")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="8acbd8ec-5860-47e4-88b5-47f354ff1ac1")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="689ade0d-a391-451a-b2e8-be6dcc4ad853")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="8a7d8441-bf3b-42cc-9bc1-e3151b48322c")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="b10113fc-99f8-45f8-8e6e-41179b968119")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="9e8faa9c-7249-461e-a23b-6f7109da4d0b")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="2c005069-d99d-4fc3-b1f5-558117daa94b")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="fd1822ce-ea15-49a5-8068-614a146e9d35")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="b9ee60f8-e3c7-4f04-8080-21c5e0bff7d6")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="fe903a35-c76b-4214-8d43-42a86194e939")>]



.. code:: ipython3

    for i in experience_tags3:             
        experience=i.text                  
        experience_list3.append(experience)      
    experience_list3[0:10]




.. parsed-literal::

    ['4-9 Yrs',
     '4-9 Yrs',
     '13-20 Yrs',
     '1-4 Yrs',
     '4-9 Yrs',
     '2-4 Yrs',
     '9-14 Yrs',
     '4-9 Yrs',
     '1-6 Yrs',
     '12-18 Yrs']



.. code:: ipython3

    locations_tags3=driver.find_elements_by_xpath("//li[@class='fleft grey-text br2 placeHolderLi location']/span[1]")
    locations_tags3[0:10]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="952af155-8995-42eb-8bf2-873ffef238cb")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="967d86bd-d849-4868-837e-b0f7f1b4a0cd")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="f89a38e2-b121-4223-99e5-719d537facac")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="c0cb646f-4969-4569-81a2-8ed1c7a7a877")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="ae7b3531-cbe9-401a-b25d-7fae327a1b7b")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="c875ff96-b90f-45e0-a70d-18513e27ca1f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="854fdd8d-5656-49dd-a4d9-ca6d17d1d50c")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="59386aff-d726-4149-bd96-1cb68a7e72fd")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="a0f9e851-326a-4cb6-a8cf-b499ff57057c")>,
     <selenium.webdriver.remote.webelement.WebElement (session="9a94f9f0eb7ede0fd02db9b23b322d95", element="a78d4c6e-2a4b-4e2e-93e9-41cdd1ec9b64")>]



.. code:: ipython3

    for i in locations_tags3:
        location=i.text
        locations_list3.append(location)
    locations_list3[0:10]




.. parsed-literal::

    ['Bangalore/Bengaluru, Delhi / NCR, Mumbai (All Areas)',
     'Kochi/Cochin, Hyderabad/Secunderabad, Pune, Ahmedabad, Chennai, Bangalore/Bengaluru, Delhi / NCR, Trivandrum/Thiruvananthapuram, Mumbai (All Areas)',
     'Bangalore/Bengaluru, Delhi / NCR, Mumbai (All Areas)',
     'New Delhi, Bangalore/Bengaluru, Mumbai (All Areas)',
     'Kolkata, Hyderabad/Secunderabad, Pune, Ahmedabad, Chennai, Bangalore/Bengaluru, Delhi / NCR',
     'Noida, New Delhi, Hyderabad/Secunderabad, Gurgaon/Gurugram',
     'Noida, Gurgaon/Gurugram',
     'New Delhi, Gurgaon/Gurugram, Delhi / NCR',
     'Noida, Delhi / NCR',
     'Bangalore/Bengaluru, Delhi / NCR, Mumbai (All Areas)']



.. code:: ipython3

    print(len(job_titles3),len(company_names3),len(experience_list3),len(locations_list3))


.. parsed-literal::

    20 20 20 20
    

.. code:: ipython3

    import pandas as pd
    jobs3=pd.DataFrame({})
    jobs3['title']=job_titles3
    jobs3['company']=company_names3
    jobs3['experience_required']=experience_list3
    jobs3['location']=locations_list3

.. code:: ipython3

    jobs3[0:10]




.. raw:: html

    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    
        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>title</th>
          <th>company</th>
          <th>experience_required</th>
          <th>location</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>Lead Data Scientist</td>
          <td>TransOrg Solutions Services (P) Ltd.</td>
          <td>4-9 Yrs</td>
          <td>Bangalore/Bengaluru, Delhi / NCR, Mumbai (All ...</td>
        </tr>
        <tr>
          <th>1</th>
          <td>Data Scientist/Data Engineer</td>
          <td>UST</td>
          <td>4-9 Yrs</td>
          <td>Kochi/Cochin, Hyderabad/Secunderabad, Pune, Ah...</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Hiring Senior Data Scientist - AI ( Remote) ||...</td>
          <td>Hanu Software Solutions</td>
          <td>13-20 Yrs</td>
          <td>Bangalore/Bengaluru, Delhi / NCR, Mumbai (All ...</td>
        </tr>
        <tr>
          <th>3</th>
          <td>Urgent Hiring For AI Data Scientist</td>
          <td>Ashkom Media India Private Limited</td>
          <td>1-4 Yrs</td>
          <td>New Delhi, Bangalore/Bengaluru, Mumbai (All Ar...</td>
        </tr>
        <tr>
          <th>4</th>
          <td>Data Scientist</td>
          <td>Tiger Analytics India LLP</td>
          <td>4-9 Yrs</td>
          <td>Kolkata, Hyderabad/Secunderabad, Pune, Ahmedab...</td>
        </tr>
        <tr>
          <th>5</th>
          <td>Hiring For Senior Data Scientist || Noida/Hyde...</td>
          <td>Tokopedia</td>
          <td>2-4 Yrs</td>
          <td>Noida, New Delhi, Hyderabad/Secunderabad, Gurg...</td>
        </tr>
        <tr>
          <th>6</th>
          <td>Hiring For Data Scientist + Python/R+ Predicti...</td>
          <td>Genpact</td>
          <td>9-14 Yrs</td>
          <td>Noida, Gurgaon/Gurugram</td>
        </tr>
        <tr>
          <th>7</th>
          <td>Data Scientist -Machine Learning with Python</td>
          <td>Genpact</td>
          <td>4-9 Yrs</td>
          <td>New Delhi, Gurgaon/Gurugram, Delhi / NCR</td>
        </tr>
        <tr>
          <th>8</th>
          <td>Data Scientist</td>
          <td>Paytm</td>
          <td>1-6 Yrs</td>
          <td>Noida, Delhi / NCR</td>
        </tr>
        <tr>
          <th>9</th>
          <td>Principal Data Scientist- 13+ years exp || Remote</td>
          <td>Hanu Software Solutions</td>
          <td>12-18 Yrs</td>
          <td>Bangalore/Bengaluru, Delhi / NCR, Mumbai (All ...</td>
        </tr>
      </tbody>
    </table>
    </div>






.. code:: ipython3

    driver=webdriver.Edge(r"C:/Python/msedgedriver.exe")

.. code:: ipython3

    driver.get('https://www.flipkart.com/')

.. code:: ipython3

    search_field_product1=driver.find_element_by_class_name('_3704LK')
    search_field_product1.send_keys('sunglasses')

.. code:: ipython3

    search_button=driver.find_element_by_xpath('/html/body/div[1]/div/div[1]/div[1]/div[2]/div[2]/form/div/button')
    search_button.click()

.. code:: ipython3

    Brand1_list=[]
    Product_Description1_list=[]
    Price1_list=[]

.. code:: ipython3

    brands_tags1=driver.find_elements_by_xpath("//div[@class='_2WkVRV']")
    brands_tags1[0:100]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="7f67758e-3218-4cee-b325-f5c8cf79617d")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="77013a10-0cf7-4548-809f-dad17dc5d039")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="5b0fbed3-a912-4e69-b6cb-0e50286b2e0a")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="c60fea31-9efe-4c5a-9463-4370e3265f4b")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="49aeae89-5761-42f5-8c1f-0a6167bd98d6")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="3da8b9a7-beef-4f48-afb2-60d98fdeac07")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="97e7917f-2d07-4627-94cd-7fdd2f971902")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="cdc79ad1-3f66-46a9-8249-45fd908be1b6")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="0f8657df-a085-4f4b-808f-b1dc4f733209")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="c7aa6faf-29db-47fd-81a4-1be763c7fa38")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="63ddd3a6-ddd0-4a43-8520-948a88321cfa")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="3c344fa6-3ba8-4e48-9b3c-3e0fa432cbf7")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="c91e3498-237d-4a02-beda-c6203aaca6fe")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="cc1200a4-b688-45a9-93c3-b15f04fd286c")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="1ea672ee-eeab-47a2-8d46-117fec5b60f0")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="7c658b80-c53b-4bfd-8d3a-9f40e2dddad4")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="83472743-838d-4bfd-87e5-26f7725802d6")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="b1253446-8abb-4a52-a9a3-85beab71dade")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="42656caa-f461-4d1e-9ae6-d7551c211aa4")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="36a93f65-6e4a-46b7-b428-621c932c1891")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="c6597175-25bb-444b-b540-9b5b0c526c08")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="e84444bd-1e10-449e-b334-9be4b9186d15")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="07892f54-69c8-4929-a412-390688a6b993")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="1f0309a1-54d6-4470-988b-ed027bcc5724")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="e1e03b9f-f820-4883-88e3-e4e567f129fc")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="45fbf5d1-eae7-44eb-a8d4-079039372d91")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="5a128dcf-fb2b-481f-8453-13b905227d90")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="7a74b3f1-1a52-469b-8595-9c980c4f513a")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="bd4fb1fd-ffa7-46bc-a7e8-d2ea9a25b862")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="9d032157-0187-4103-b013-f5dbba9e626f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="7acdf245-2517-43a9-b1d1-c642d719e2cd")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="509fbe35-464c-4cb1-85a2-bb2ac4341b9f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="f9c8faa8-b30e-4e83-9fa3-d329f0d3c78e")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="377c421a-2df0-4954-be3a-37a8406258dc")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="9290873a-aa5f-4d23-9d9b-801d4a46a2aa")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="4ffe076f-910e-4bd7-a563-5e2f674fe0d2")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="cd309ed8-9398-4c0d-9f68-ad09059b9d48")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="13dba68d-7748-4145-bf51-5976be6a4578")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="69f5ef9c-5767-4f92-a5de-59605ccb67fb")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="5a8d807d-1f7f-40b9-a591-abd96040acf0")>]



.. code:: ipython3

    for i in brands_tags1:
        Brand=i.text
        Brand1_list.append(Brand)
    Brand1_list




.. parsed-literal::

    ['PIRASO',
     'VINCENT CHASE',
     'Fastrack',
     'SUNBEE',
     'Fastrack',
     'Lee Topper',
     'PIRASO',
     'VINCENT CHASE',
     'Elligator',
     'New Specs',
     'Elligator',
     'PIRASO',
     'PIRASO',
     'kingsunglasses',
     'SRPM',
     'PIRASO',
     'DAHAAZIL',
     'SHAAH COLLECTIONS',
     'SUNBEE',
     'PIRASO',
     'New Specs',
     'Elligator',
     'ROZZETTA CRAFT',
     'Singco India',
     'PIRASO',
     'DEIXELS',
     'ROZZETTA CRAFT',
     'CRYSTAL CART',
     'PIRASO',
     'ROZZETTA CRAFT',
     'Lee Topper',
     'CRYSTAL CART',
     'Fastrack',
     'kingsunglasses',
     'hipe',
     'PHENOMENAL',
     'Fastrack',
     'ROZZETTA CRAFT',
     'Fastrack',
     'ROZZETTA CRAFT',
     'PIRASO',
     'VINCENT CHASE',
     'Fastrack',
     'SUNBEE',
     'Fastrack',
     'Lee Topper',
     'PIRASO',
     'VINCENT CHASE',
     'Elligator',
     'New Specs',
     'Elligator',
     'PIRASO',
     'PIRASO',
     'kingsunglasses',
     'SRPM',
     'PIRASO',
     'DAHAAZIL',
     'SHAAH COLLECTIONS',
     'SUNBEE',
     'PIRASO',
     'New Specs',
     'Elligator',
     'ROZZETTA CRAFT',
     'Singco India',
     'PIRASO',
     'DEIXELS',
     'ROZZETTA CRAFT',
     'CRYSTAL CART',
     'PIRASO',
     'ROZZETTA CRAFT',
     'Lee Topper',
     'CRYSTAL CART',
     'Fastrack',
     'kingsunglasses',
     'hipe',
     'PHENOMENAL',
     'Fastrack',
     'ROZZETTA CRAFT',
     'Fastrack',
     'ROZZETTA CRAFT']



.. code:: ipython3

    Product_Description1_tags=driver.find_elements_by_xpath('//a[@class="IRpwTa"]')
    Product_Description1[0:100]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="09f4e299-86cb-40fc-a1ea-d8d9ec7c5bc4")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="0c9f8cae-8b30-4e4f-ad74-409565563a53")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="c3a4f239-8753-4f9d-aaac-654fb0e70232")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="8541156c-280a-4d6b-b179-6e145c8134f5")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="077ccc82-08d4-4c7a-a2c5-60d00c57f9f9")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="d0747b3d-add7-448a-b8ab-e44b608fc8ed")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="1580651e-b496-4786-914f-b717cd67da67")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="395d6321-abca-449f-a597-5a064bc8dfde")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="532bfbf3-0c07-4f4e-9bb0-41114b25b156")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="9067456f-965b-475e-9951-e78b435f6e46")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="adbbaf10-a47f-48e7-bac0-2ca19add1224")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="f0403c7a-d68a-4b43-9100-bb5ab9ab4caa")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="efbd5ee9-6dcb-46e5-be1b-f3bddc5fae73")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="1672cb40-9fb8-4c1e-a24b-86f7d8b594c5")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="f5c573ba-7a97-408b-9f78-84c1830508a2")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="35d84beb-ecf6-447a-9f0b-966243e5acd8")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="af77ce2e-79bb-4ac5-9a34-2ebb7a500516")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="94a32df9-e78c-4de2-b9b7-3f387ce2b7ca")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="d7c06f20-3564-4a34-ad52-a094e0f3e9d8")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="6190efdb-d4e7-4671-8b6f-646841e475f9")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="ffd2122b-0a72-4b43-9741-eed9782801b5")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="6faaa476-5e83-45e7-8a61-0e63b48083df")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="ecee08b4-7364-4810-853b-2571cfe5fd92")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="bc739fbc-9aaa-4a9b-aa2f-46903ed07b13")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="f01912d0-14bf-4152-9dcc-b1d49ea2e38d")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="86a887ff-9ca8-4dbf-b4fd-abd49ee434dc")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="230e6582-9cdc-4efd-b1e2-91db43bae272")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="e0fbc825-ced7-4bdc-80cb-4b34b1d19a0f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="50748cc4-409e-41a7-bf18-51501cb8918c")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="5904752e-ff5a-4a23-be22-d9eb48e83da5")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="7821e6c9-a8b7-4da0-88c6-d423e6c0db3a")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="175dcec4-6a93-4ae5-b0e7-d128a0997041")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="5173dcc6-7924-4f75-9a2e-b9f93a4e41a8")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="f1730130-cd70-4965-9b37-cd60c6dfe839")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="ee8115e8-474b-458c-8746-d6e7b4224880")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="3b189a88-d66c-4e64-ac73-e39dc527b319")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="5db4b3b8-b3fc-4979-93c2-78d37aa037d2")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="9b344982-89a9-4a65-b31b-8ac09a139973")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="a63af700-bcdb-4fb9-b249-7cb362fca977")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="6cc210fb-35af-40f4-92d5-fdafcd9c21fd")>,
     'UV Protection Aviator Sunglasses (54)',
     'UV Protection Rectangular Sunglasses (50)',
     'UV Protection Rectangular Sunglasses (Free Size)',
     'UV Protection, Polarized Wayfarer Sunglasses (Free Size...',
     'UV Protection Wayfarer Sunglasses (Free Size)',
     'Riding Glasses Wrap-around Sunglasses (Free Size)',
     'UV Protection Rectangular Sunglasses (52)',
     'UV Protection Cat-eye Sunglasses (54)',
     'UV Protection Round Sunglasses (54)',
     'UV Protection Rectangular Sunglasses (Free Size)',
     'UV Protection Wayfarer Sunglasses (53)',
     'UV Protection Butterfly Sunglasses (60)',
     'UV Protection Wayfarer Sunglasses (32)',
     'UV Protection, Riding Glasses, Mirrored Wayfarer Sungla...',
     'UV Protection Wayfarer Sunglasses (50)',
     'UV Protection Butterfly Sunglasses (60)',
     'UV Protection, Night Vision, Riding Glasses Wayfarer, W...',
     'UV Protection, Polarized, Mirrored Rectangular Sunglass...',
     'UV Protection, Polarized, Mirrored Retro Square Sunglas...',
     'UV Protection Aviator Sunglasses (54)',
     'Mirrored, UV Protection, Riding Glasses, Others Round S...',
     'UV Protection Aviator Sunglasses (55)',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'Gradient, Toughened Glass Lens, UV Protection Retro Squ...',
     'UV Protection Aviator Sunglasses (54)',
     'UV Protection Aviator, Wayfarer Sunglasses (Free Size)',
     'Polarized, Riding Glasses Sports, Wrap-around Sunglasse...',
     'Polarized, Gradient, UV Protection, Mirrored Over-sized...',
     'UV Protection Aviator Sunglasses (58)',
     'UV Protection, Gradient Retro Square Sunglasses (Free S...',
     'UV Protection Rectangular Sunglasses (Free Size)',
     'Polarized, UV Protection, Gradient, Riding Glasses Rect...',
     'UV Protection Shield Sunglasses (Free Size)',
     'UV Protection Round Sunglasses (54)',
     'Gradient, UV Protection Round Sunglasses (Free Size)',
     'UV Protection Retro Square Sunglasses (Free Size)',
     'UV Protection Wayfarer Sunglasses (Free Size)',
     'UV Protection Retro Square Sunglasses (Free Size)',
     'Gradient, UV Protection Wayfarer Sunglasses (Free Size)',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...']



.. code:: ipython3

    for i in Product_Description1_tags:
        Product=i.text
        Product_Description1_list.append(Product)
    Product_Description1_list




.. parsed-literal::

    ['UV Protection Aviator Sunglasses (54)',
     'UV Protection Rectangular Sunglasses (50)',
     'UV Protection Rectangular Sunglasses (Free Size)',
     'UV Protection, Polarized Wayfarer Sunglasses (Free Size...',
     'UV Protection Wayfarer Sunglasses (Free Size)',
     'Riding Glasses Wrap-around Sunglasses (Free Size)',
     'UV Protection Rectangular Sunglasses (52)',
     'UV Protection Cat-eye Sunglasses (54)',
     'UV Protection Round Sunglasses (54)',
     'UV Protection Rectangular Sunglasses (Free Size)',
     'UV Protection Wayfarer Sunglasses (53)',
     'UV Protection Butterfly Sunglasses (60)',
     'UV Protection Wayfarer Sunglasses (32)',
     'UV Protection, Riding Glasses, Mirrored Wayfarer Sungla...',
     'UV Protection Wayfarer Sunglasses (50)',
     'UV Protection Butterfly Sunglasses (60)',
     'UV Protection, Night Vision, Riding Glasses Wayfarer, W...',
     'UV Protection, Polarized, Mirrored Rectangular Sunglass...',
     'UV Protection, Polarized, Mirrored Retro Square Sunglas...',
     'UV Protection Aviator Sunglasses (54)',
     'Mirrored, UV Protection, Riding Glasses, Others Round S...',
     'UV Protection Aviator Sunglasses (55)',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'Gradient, Toughened Glass Lens, UV Protection Retro Squ...',
     'UV Protection Aviator Sunglasses (54)',
     'UV Protection Aviator, Wayfarer Sunglasses (Free Size)',
     'Polarized, Riding Glasses Sports, Wrap-around Sunglasse...',
     'Polarized, Gradient, UV Protection, Mirrored Over-sized...',
     'UV Protection Aviator Sunglasses (58)',
     'UV Protection, Gradient Retro Square Sunglasses (Free S...',
     'UV Protection Rectangular Sunglasses (Free Size)',
     'Polarized, UV Protection, Gradient, Riding Glasses Rect...',
     'UV Protection Shield Sunglasses (Free Size)',
     'UV Protection Round Sunglasses (54)',
     'Gradient, UV Protection Round Sunglasses (Free Size)',
     'UV Protection Retro Square Sunglasses (Free Size)',
     'UV Protection Wayfarer Sunglasses (Free Size)',
     'UV Protection Retro Square Sunglasses (Free Size)',
     'Gradient, UV Protection Wayfarer Sunglasses (Free Size)',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'UV Protection Aviator Sunglasses (54)',
     'UV Protection Rectangular Sunglasses (50)',
     'UV Protection Rectangular Sunglasses (Free Size)',
     'UV Protection, Polarized Wayfarer Sunglasses (Free Size...',
     'UV Protection Wayfarer Sunglasses (Free Size)',
     'Riding Glasses Wrap-around Sunglasses (Free Size)',
     'UV Protection Rectangular Sunglasses (52)',
     'UV Protection Cat-eye Sunglasses (54)',
     'UV Protection Round Sunglasses (54)',
     'UV Protection Rectangular Sunglasses (Free Size)',
     'UV Protection Wayfarer Sunglasses (53)',
     'UV Protection Butterfly Sunglasses (60)',
     'UV Protection Wayfarer Sunglasses (32)',
     'UV Protection, Riding Glasses, Mirrored Wayfarer Sungla...',
     'UV Protection Wayfarer Sunglasses (50)',
     'UV Protection Butterfly Sunglasses (60)',
     'UV Protection, Night Vision, Riding Glasses Wayfarer, W...',
     'UV Protection, Polarized, Mirrored Rectangular Sunglass...',
     'UV Protection, Polarized, Mirrored Retro Square Sunglas...',
     'UV Protection Aviator Sunglasses (54)',
     'Mirrored, UV Protection, Riding Glasses, Others Round S...',
     'UV Protection Aviator Sunglasses (55)',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...',
     'Gradient, Toughened Glass Lens, UV Protection Retro Squ...',
     'UV Protection Aviator Sunglasses (54)',
     'UV Protection Aviator, Wayfarer Sunglasses (Free Size)',
     'Polarized, Riding Glasses Sports, Wrap-around Sunglasse...',
     'Polarized, Gradient, UV Protection, Mirrored Over-sized...',
     'UV Protection Aviator Sunglasses (58)',
     'UV Protection, Gradient Retro Square Sunglasses (Free S...',
     'UV Protection Rectangular Sunglasses (Free Size)',
     'Polarized, UV Protection, Gradient, Riding Glasses Rect...',
     'UV Protection Shield Sunglasses (Free Size)',
     'UV Protection Round Sunglasses (54)',
     'Gradient, UV Protection Round Sunglasses (Free Size)',
     'UV Protection Retro Square Sunglasses (Free Size)',
     'UV Protection Wayfarer Sunglasses (Free Size)',
     'UV Protection Retro Square Sunglasses (Free Size)',
     'Gradient, UV Protection Wayfarer Sunglasses (Free Size)',
     'UV Protection, Gradient Rectangular Sunglasses (Free Si...']



.. code:: ipython3

    Price1_tags=driver.find_elements_by_xpath('//div[@class="_30jeq3"]')
    Price1_tags[0:100]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="f6675347-6da7-4622-856c-d5fee4c2d1b8")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="22532054-9c51-406b-a47f-1d7598ec6563")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="df404847-0711-451f-9867-67e8f19c66f1")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="1248f581-772d-4fd5-926b-e4a1357fd975")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="5c092ef7-5116-410a-a4c0-6e833c7193ff")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="0dcc3b14-c4f2-47e0-b881-34efdc0618a1")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="bcbeca49-86de-464e-96e3-53f70611e7f7")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="cd7d4937-1b4d-459e-84d9-a22f56eaabfc")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="75ad5d0b-f537-47a9-85dc-8bf67e44937a")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="0473a4b2-9507-416b-8b14-89adf595e72f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="533f22f3-ac3f-4c45-b9bc-bed39752fb91")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="09843ebf-41cc-4f3f-8dd6-64036476d883")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="3062f775-3373-45bc-b5f6-3a0512ada61a")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="4a33f3be-41b9-472a-bb27-76c7cd77194f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="53967bfa-6682-455e-ad1c-eed9f0ded202")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="05b5b219-b0ac-469c-9bb1-762fcb6897eb")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="3303a94f-0cf9-430e-9674-4a29d75f1158")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="6a3fa706-d4fc-4869-b762-68d8c60fbc82")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="8c9cecb2-00e1-4ec9-a027-9583a5682084")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="4cb4944f-b1b4-44ab-86dc-02a4ba5ba535")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="d463a60d-3591-4848-a42a-57e14411a975")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="4de13401-fa29-47b0-92e5-26f4ed4f6dc1")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="15d3b0f0-a1f3-4bdc-81b2-2c0948bce32e")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="0e624a14-8547-48b4-931b-8623d9a9d26a")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="4fa12d27-39c3-48cf-ad10-d2440b36db4e")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="bbe6d891-6694-4328-886f-63226ebbc212")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="56d71e9b-7941-4dda-83b0-a298c91fd39e")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="cfb5afeb-997b-4c14-b51d-e1fb25da69a1")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="d3e0ae8f-6c65-4d68-897a-873b7aba6cc6")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="fd22f2bc-961f-48d6-87c4-90394bf25f8a")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="0a1ac8f6-40a6-432a-baab-04d61a66286e")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="7b71df58-afaf-4507-8dc0-caed0d51762d")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="3b221cbf-f062-43b1-8042-2de57ce6ef1f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="4ae7417b-f233-4980-b1f6-76676fe6a686")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="2333412f-d999-4d50-af17-b618b53e1a41")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="6af9382d-9dce-4452-a00a-ad74669fcbbd")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="d0e41e50-c7a5-4564-8fea-e7a2f995a915")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="35f8f5da-bb14-4882-909d-3abca77115bf")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="95140869-db84-43d7-8559-976458780110")>,
     <selenium.webdriver.remote.webelement.WebElement (session="dae10ff7a933cb74c36dd3bef3b382c1", element="da248156-3381-4094-9c1f-4e7a398d06ea")>]



.. code:: ipython3

    for i in Price1_tags:
        Price=i.text
        Price1_list.append(Price)
    Price1_list




.. parsed-literal::

    ['₹224',
     '₹649',
     '₹639',
     '₹283',
     '₹647',
     '₹299',
     '₹280',
     '₹649',
     '₹295',
     '₹265',
     '₹224',
     '₹410',
     '₹225',
     '₹209',
     '₹249',
     '₹399',
     '₹219',
     '₹195',
     '₹259',
     '₹249',
     '₹299',
     '₹333',
     '₹399',
     '₹664',
     '₹224',
     '₹249',
     '₹499',
     '₹249',
     '₹349',
     '₹349',
     '₹219',
     '₹339',
     '₹809',
     '₹214',
     '₹208',
     '₹362',
     '₹639',
     '₹499',
     '₹639',
     '₹449',
     '₹224',
     '₹649',
     '₹639',
     '₹283',
     '₹647',
     '₹299',
     '₹280',
     '₹649',
     '₹295',
     '₹265',
     '₹224',
     '₹410',
     '₹225',
     '₹209',
     '₹249',
     '₹399',
     '₹219',
     '₹195',
     '₹259',
     '₹249',
     '₹299',
     '₹333',
     '₹399',
     '₹664',
     '₹224',
     '₹249',
     '₹499',
     '₹249',
     '₹349',
     '₹349',
     '₹219',
     '₹339',
     '₹809',
     '₹214',
     '₹208',
     '₹362',
     '₹639',
     '₹499',
     '₹639',
     '₹449']



.. code:: ipython3

    print(len(Brand1),len(Product_Description1),len(Price1))


.. parsed-literal::

    112 360 40
    

.. code:: ipython3

    import pandas as pd
    df1=pd.DataFrame()
    df1["BRAND"]=Brand1_list[:100]
    df1["PRODUCT_DESCRIPTION"]=Product_Description1_list[:100]
    df1["PRICE"]=Price1_list[:100]
    df1




.. raw:: html

    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    
        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>BRAND</th>
          <th>PRODUCT_DESCRIPTION</th>
          <th>PRICE</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>PIRASO</td>
          <td>UV Protection Aviator Sunglasses (54)</td>
          <td>₹224</td>
        </tr>
        <tr>
          <th>1</th>
          <td>VINCENT CHASE</td>
          <td>UV Protection Rectangular Sunglasses (50)</td>
          <td>₹649</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Fastrack</td>
          <td>UV Protection Rectangular Sunglasses (Free Size)</td>
          <td>₹639</td>
        </tr>
        <tr>
          <th>3</th>
          <td>SUNBEE</td>
          <td>UV Protection, Polarized Wayfarer Sunglasses (...</td>
          <td>₹283</td>
        </tr>
        <tr>
          <th>4</th>
          <td>Fastrack</td>
          <td>UV Protection Wayfarer Sunglasses (Free Size)</td>
          <td>₹647</td>
        </tr>
        <tr>
          <th>...</th>
          <td>...</td>
          <td>...</td>
          <td>...</td>
        </tr>
        <tr>
          <th>75</th>
          <td>PHENOMENAL</td>
          <td>UV Protection Retro Square Sunglasses (Free Size)</td>
          <td>₹362</td>
        </tr>
        <tr>
          <th>76</th>
          <td>Fastrack</td>
          <td>UV Protection Wayfarer Sunglasses (Free Size)</td>
          <td>₹639</td>
        </tr>
        <tr>
          <th>77</th>
          <td>ROZZETTA CRAFT</td>
          <td>UV Protection Retro Square Sunglasses (Free Size)</td>
          <td>₹499</td>
        </tr>
        <tr>
          <th>78</th>
          <td>Fastrack</td>
          <td>Gradient, UV Protection Wayfarer Sunglasses (F...</td>
          <td>₹639</td>
        </tr>
        <tr>
          <th>79</th>
          <td>ROZZETTA CRAFT</td>
          <td>UV Protection, Gradient Rectangular Sunglasses...</td>
          <td>₹449</td>
        </tr>
      </tbody>
    </table>
    <p>80 rows × 3 columns</p>
    </div>








.. code:: ipython3

    driver=webdriver.Edge(r"C:/Python/msedgedriver.exe")

.. code:: ipython3

    driver.get('https://www.flipkart.com/apple-iphone-11-black-64-gb-includesearpods-poweradapter/p/itm0f37c2240b217?pid=MOBFKCTSVZAXUHGR&lid=LSTMOBFKC')

.. code:: ipython3

    all_reviews_btn=driver.find_element_by_xpath("//div[@class='_3UAT2v _16PBlm']/span")

.. code:: ipython3

    all_reviews_btn.click()
    

.. code:: ipython3

    rating_tags=driver.find_elements_by_xpath('//div[@class="_3LWZlK _1BLPMq"]')
    rating_tags[0:100]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="74226626344371f3d8780e3b0ba6e568", element="5a968e07-4155-4a65-803b-30567de06ee8")>,
     <selenium.webdriver.remote.webelement.WebElement (session="74226626344371f3d8780e3b0ba6e568", element="e2a04f72-f043-4566-a57c-e2287787ba4d")>,
     <selenium.webdriver.remote.webelement.WebElement (session="74226626344371f3d8780e3b0ba6e568", element="b9a1a1bf-b896-49e1-99cb-7170e1fa40d2")>,
     <selenium.webdriver.remote.webelement.WebElement (session="74226626344371f3d8780e3b0ba6e568", element="fd04a4c6-da08-444b-9357-6390d62b6c8f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="74226626344371f3d8780e3b0ba6e568", element="39111c50-d3fd-4a13-871b-65c578043832")>,
     <selenium.webdriver.remote.webelement.WebElement (session="74226626344371f3d8780e3b0ba6e568", element="f1b798b6-c10b-4617-b0e5-530e6f93f9a6")>,
     <selenium.webdriver.remote.webelement.WebElement (session="74226626344371f3d8780e3b0ba6e568", element="8f8dd062-33f6-4ce0-91b0-a5b169f125d6")>,
     <selenium.webdriver.remote.webelement.WebElement (session="74226626344371f3d8780e3b0ba6e568", element="b754319c-75cb-414b-be22-dfe3dd1922e1")>,
     <selenium.webdriver.remote.webelement.WebElement (session="74226626344371f3d8780e3b0ba6e568", element="8a00e747-439d-4da9-af19-8a1910d3edb7")>,
     <selenium.webdriver.remote.webelement.WebElement (session="74226626344371f3d8780e3b0ba6e568", element="6cf58884-3e23-4166-8827-d69a93dd1209")>]



.. code:: ipython3

    next_button=driver.find_element_by_xpath("/html/body/div[1]/div/div[3]/div/div/div[2]/div[13]/div/div/nav/a[11]/span")
    next_button.click()

.. code:: ipython3

    import time

.. code:: ipython3

     def scrape_rating():
        rating=[]
        driver.refresh()
        rating_el=driver.find_elements_by_xpath("//div[@class='_3LWZlK _1BLPMq']")
        time.sleep(3)
        for i in rating_el:
            try:
                rating.append(i.text)
                driver.execute_script("window.scrollBy(0,document.body.scrollHeight0)")
            except:
                rating.append("--")
        return rating

.. code:: ipython3

    def scrape_review_summary():
        review_sum=[]
        driver.refresh()
        rev_sum=driver.find_elements_by_xpath("//p[@class='_2-N8zT']")
        time.sleep(3)
        for i in rev_sum:
            try:
                review_sum.append(i.text)
                driver.execute_script("window.scrollBy(0,document.body.scrollHeight0)")
            except:
                review_sum.append("--")
        return review_sum
                

.. code:: ipython3

    def scrape_full_review():
        full_review=[]
        driver.refresh()
        rev_el=driver.find_elements_by_xpath("//div[@class='t-ZTKy']/div")
        time.sleep(3)
        for i in rev_el:
            try:
                full_review.append(i.text.replace("\n","  New Line: "))
                driver.execute_script("window.scrollBy(0,document.body.scrollHeight0)")
            except:
                full_review.append("--")
        return full_review
            

.. code:: ipython3

    import time
    rating=[]
    review_sum=[]
    full_review=[]
    length=len(rating)
    while(length<=100):
        driver.refresh()
        rating.extend(scrape_rating())
        review_sum.extend(scrape_review_summary())
        full_review.extend(scrape_full_review())
        time.sleep(5)
        length=len(rating)
        next_btn=driver.find_element_by_xpath("//a[@class='_1LKTO3']/span")
        next_btn.click()
        
    len(review_sum)
        




.. parsed-literal::

    100



.. code:: ipython3

    length_list=[len(full_review),len(rating),len(review_sum)]
    length_list




.. parsed-literal::

    [110, 110, 100]



.. code:: ipython3

    review_sum




.. parsed-literal::

    ['Highly recommended',
     'Perfect product!',
     'Perfect product!',
     'Worth every penny',
     'Highly recommended',
     'Perfect product!',
     'Worth every penny',
     'Simply awesome',
     'Classy product',
     'Terrific',
     'Highly recommended',
     'Perfect product!',
     'Perfect product!',
     'Worth every penny',
     'Highly recommended',
     'Perfect product!',
     'Worth every penny',
     'Simply awesome',
     'Classy product',
     'Terrific',
     'Highly recommended',
     'Perfect product!',
     'Perfect product!',
     'Worth every penny',
     'Highly recommended',
     'Perfect product!',
     'Worth every penny',
     'Simply awesome',
     'Classy product',
     'Terrific',
     'Highly recommended',
     'Perfect product!',
     'Perfect product!',
     'Worth every penny',
     'Highly recommended',
     'Perfect product!',
     'Worth every penny',
     'Simply awesome',
     'Classy product',
     'Terrific',
     'Highly recommended',
     'Perfect product!',
     'Perfect product!',
     'Worth every penny',
     'Highly recommended',
     'Perfect product!',
     'Worth every penny',
     'Simply awesome',
     'Classy product',
     'Terrific',
     'Brilliant',
     'Simply awesome',
     'Best in the market!',
     'Perfect product!',
     'Fabulous!',
     'Worth every penny',
     'Great product',
     'Good choice',
     'Worth every penny',
     'Highly recommended',
     'Brilliant',
     'Simply awesome',
     'Best in the market!',
     'Perfect product!',
     'Fabulous!',
     'Worth every penny',
     'Great product',
     'Good choice',
     'Worth every penny',
     'Highly recommended',
     'Brilliant',
     'Simply awesome',
     'Best in the market!',
     'Perfect product!',
     'Fabulous!',
     'Worth every penny',
     'Great product',
     'Good choice',
     'Worth every penny',
     'Highly recommended',
     'Brilliant',
     'Simply awesome',
     'Best in the market!',
     'Perfect product!',
     'Fabulous!',
     'Worth every penny',
     'Great product',
     'Good choice',
     'Worth every penny',
     'Highly recommended',
     'Brilliant',
     'Simply awesome',
     'Best in the market!',
     'Perfect product!',
     'Fabulous!',
     'Worth every penny',
     'Great product',
     'Good choice',
     'Worth every penny',
     'Highly recommended']



.. code:: ipython3

    import pandas as pd
    df2=pd.DataFrame()
    df2["INDEX"]=range(1,101)
    df2["RATING"]=rating[:100]
    df2["REVIEW_SUMMARY"]=review_sum[:100]
    df2["FULL_REVIEW"]=full_review[:100]
    df2.set_index("INDEX",inplace=True)
    df2




.. raw:: html

    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    
        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>RATING</th>
          <th>REVIEW_SUMMARY</th>
          <th>FULL_REVIEW</th>
        </tr>
        <tr>
          <th>INDEX</th>
          <th></th>
          <th></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>1</th>
          <td>5</td>
          <td>Highly recommended</td>
          <td>iphone 11 is a very good phone to buy only if ...</td>
        </tr>
        <tr>
          <th>2</th>
          <td>5</td>
          <td>Perfect product!</td>
          <td>It’s a must buy who is looking for an upgrade ...</td>
        </tr>
        <tr>
          <th>3</th>
          <td>5</td>
          <td>Perfect product!</td>
          <td>Value for money❤️❤️  New Line: Its awesome mob...</td>
        </tr>
        <tr>
          <th>4</th>
          <td>5</td>
          <td>Worth every penny</td>
          <td>Smooth like butter, camera like fantabulous, s...</td>
        </tr>
        <tr>
          <th>5</th>
          <td>5</td>
          <td>Highly recommended</td>
          <td>It's my first time to use iOS phone and I am l...</td>
        </tr>
        <tr>
          <th>...</th>
          <td>...</td>
          <td>...</td>
          <td>...</td>
        </tr>
        <tr>
          <th>96</th>
          <td>5</td>
          <td>Worth every penny</td>
          <td>Previously I was using one plus 3t it was a gr...</td>
        </tr>
        <tr>
          <th>97</th>
          <td>5</td>
          <td>Great product</td>
          <td>Amazing Powerful and Durable Gadget.  New Line...</td>
        </tr>
        <tr>
          <th>98</th>
          <td>4</td>
          <td>Good choice</td>
          <td>So far it’s been an AMAZING experience coming ...</td>
        </tr>
        <tr>
          <th>99</th>
          <td>5</td>
          <td>Worth every penny</td>
          <td>i11 is worthy to buy, too much happy with the ...</td>
        </tr>
        <tr>
          <th>100</th>
          <td>5</td>
          <td>Highly recommended</td>
          <td>What a camera .....just awesome ..you can feel...</td>
        </tr>
      </tbody>
    </table>
    <p>100 rows × 3 columns</p>
    </div>






.. code:: ipython3

    driver=webdriver.Edge(r"C:/Python/msedgedriver.exe")
    url=('https://www.flipkart.com/')
    driver.get(url)

.. code:: ipython3

    search_column=driver.find_element_by_xpath("//input[@class='_3704LK']")
    search_column.send_keys("sneakers")
    search_btn=driver.find_element_by_xpath("//button[@class='L0Z3Pu']")
    search_btn.click()

.. code:: ipython3

    Brand2_list=[]
    Product_Description2_list=[]
    Price2_list=[]

.. code:: ipython3

    brands_tags2=driver.find_elements_by_xpath("//div[@class='_2WkVRV']")
    brands_tags2[0:4]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="d31bc33d3fd16acf5f53b8a656b35c37", element="cc31885a-c1f6-4569-8322-164af5cb5a8e")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d31bc33d3fd16acf5f53b8a656b35c37", element="9cab828b-4d25-40f3-93f3-ff1006b6476b")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d31bc33d3fd16acf5f53b8a656b35c37", element="f5856c9b-9f17-4527-970a-c720bf084c77")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d31bc33d3fd16acf5f53b8a656b35c37", element="6fc4737e-3697-4e17-b415-cd854dddebe9")>]



.. code:: ipython3

    for i in brands_tags2:
        Brand=i.text
        Brand2_list.append(Brand)
    Brand2_list[0:4]




.. parsed-literal::

    ['Labbin', 'VZAZZY', 'URBANBOX', 'BRUTON']



.. code:: ipython3

    Product_Description2_tags=driver.find_elements_by_xpath("//a[@class='IRpwTa']")
    Product_Description2_tags[0:4]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="d31bc33d3fd16acf5f53b8a656b35c37", element="febe2107-a912-42c4-8a11-c9d912dd1f31")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d31bc33d3fd16acf5f53b8a656b35c37", element="a0b49995-0035-4c80-bed6-904923c8dca0")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d31bc33d3fd16acf5f53b8a656b35c37", element="729b2385-36cc-4c54-95b7-9001304f7fc8")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d31bc33d3fd16acf5f53b8a656b35c37", element="617201d9-543a-49ec-9d39-26e1d4d897aa")>]



.. code:: ipython3

    for i in Product_Description2_tags:
        Product=i.text
        Product_Description2_list.append(Product)
    Product_Description2_list[0:4]




.. parsed-literal::

    ['Sneakers For Men',
     'Sneakers For Men',
     'Modern Trendy Sneakers Shoes Sneakers For Men',
     'STYLISH MENS BLACK SNEAKER Sneakers For Men']



.. code:: ipython3

    Price2_tags=driver.find_elements_by_xpath("//div[@class='_30jeq3']")
    Price2_tags[0:4]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="d31bc33d3fd16acf5f53b8a656b35c37", element="ef280df5-1bac-4e3e-b693-57ebc5b1b7e5")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d31bc33d3fd16acf5f53b8a656b35c37", element="03ca002a-5ce5-4234-983b-441f2fa13b06")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d31bc33d3fd16acf5f53b8a656b35c37", element="dac63280-9166-4473-9610-41fb656ba4d5")>,
     <selenium.webdriver.remote.webelement.WebElement (session="d31bc33d3fd16acf5f53b8a656b35c37", element="d31eb4fa-770d-420d-91a6-fe30c2df7ff2")>]



.. code:: ipython3

    for i in Price2_tags:
        Price=i.text
        Price2_list.append(Price)
    Price2_list[0:4]




.. parsed-literal::

    ['₹449', '₹449', '₹158', '₹245']



.. code:: ipython3

    print(len(Brand2_list),len(Product_Description2_list),len(Price2_list))


.. parsed-literal::

    40 34 40
    

.. code:: ipython3

    df4=pd.DataFrame()
    df4["BRAND"]=Brand2_list[:30]
    df4["PRODUCT_DESCRIPTION"]=Product_Description2_list[:30]
    df4["PRICE"]=Price2_list[:30]
    df4




.. raw:: html

    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    
        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>BRAND</th>
          <th>PRODUCT_DESCRIPTION</th>
          <th>PRICE</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>Labbin</td>
          <td>Sneakers For Men</td>
          <td>₹449</td>
        </tr>
        <tr>
          <th>1</th>
          <td>VZAZZY</td>
          <td>Sneakers For Men</td>
          <td>₹449</td>
        </tr>
        <tr>
          <th>2</th>
          <td>URBANBOX</td>
          <td>Modern Trendy Sneakers Shoes Sneakers For Men</td>
          <td>₹158</td>
        </tr>
        <tr>
          <th>3</th>
          <td>BRUTON</td>
          <td>STYLISH MENS BLACK SNEAKER Sneakers For Men</td>
          <td>₹245</td>
        </tr>
        <tr>
          <th>4</th>
          <td>corsac</td>
          <td>Sneakers For Men</td>
          <td>₹449</td>
        </tr>
        <tr>
          <th>5</th>
          <td>Labbin</td>
          <td>Stylish Comfortable Lightweight, Breathable Wa...</td>
          <td>₹419</td>
        </tr>
        <tr>
          <th>6</th>
          <td>BIRDE</td>
          <td>Kwik FIT casual sneaker shoes and partywear sh...</td>
          <td>₹269</td>
        </tr>
        <tr>
          <th>7</th>
          <td>RapidBox</td>
          <td>Sneakers For Men</td>
          <td>₹600</td>
        </tr>
        <tr>
          <th>8</th>
          <td>KWIK FIT</td>
          <td>Sneakers Sneakers For Men</td>
          <td>₹347</td>
        </tr>
        <tr>
          <th>9</th>
          <td>Magnolia</td>
          <td>Combo Pack Of 4 Casual Shoes Loafer Shoes Snea...</td>
          <td>₹351</td>
        </tr>
        <tr>
          <th>10</th>
          <td>SCATCHITE</td>
          <td>Shark-41 Sneakers For Men</td>
          <td>₹348</td>
        </tr>
        <tr>
          <th>11</th>
          <td>BRUTON</td>
          <td>Sneaker Sneakers For Men</td>
          <td>₹610</td>
        </tr>
        <tr>
          <th>12</th>
          <td>Kraasa</td>
          <td>Sneakers For Men</td>
          <td>₹411</td>
        </tr>
        <tr>
          <th>13</th>
          <td>BRUTON</td>
          <td>Original Luxury Branded Black Fancy Casual Wal...</td>
          <td>₹249</td>
        </tr>
        <tr>
          <th>14</th>
          <td>aadi</td>
          <td>5013-Latest Collection Stylish &amp; Trendy of cas...</td>
          <td>₹297</td>
        </tr>
        <tr>
          <th>15</th>
          <td>RapidBox</td>
          <td>Series 7 Sneakers For Men</td>
          <td>₹630</td>
        </tr>
        <tr>
          <th>16</th>
          <td>ASTEROID</td>
          <td>Sneakers For Men</td>
          <td>₹449</td>
        </tr>
        <tr>
          <th>17</th>
          <td>World Wear Footwear</td>
          <td>STR2 Sneakers For Men</td>
          <td>₹199</td>
        </tr>
        <tr>
          <th>18</th>
          <td>Kraasa</td>
          <td>Lattest Sneakers Shoe Sneakers For Men</td>
          <td>₹405</td>
        </tr>
        <tr>
          <th>19</th>
          <td>Zorth</td>
          <td>Luxury Branded Fashionable Men's Casual Walkin...</td>
          <td>₹397</td>
        </tr>
        <tr>
          <th>20</th>
          <td>ONECENTRE</td>
          <td>Luxury Fashionable casual sneaker shoes Sneake...</td>
          <td>₹250</td>
        </tr>
        <tr>
          <th>21</th>
          <td>BRUTON</td>
          <td>Sneakers For Men</td>
          <td>₹249</td>
        </tr>
        <tr>
          <th>22</th>
          <td>ASTEROID</td>
          <td>5011-Latest Collection Stylish &amp; Trendy Casual...</td>
          <td>₹449</td>
        </tr>
        <tr>
          <th>23</th>
          <td>luxury fashion</td>
          <td>Sneakers For Men</td>
          <td>₹449</td>
        </tr>
        <tr>
          <th>24</th>
          <td>Layasa</td>
          <td>Sneakers For Men</td>
          <td>₹449</td>
        </tr>
        <tr>
          <th>25</th>
          <td>World Wear Footwear</td>
          <td>Latest Collection-1227 Stylish Casual Sports S...</td>
          <td>₹199</td>
        </tr>
        <tr>
          <th>26</th>
          <td>CLYMB</td>
          <td>Men 5014 Latest Collection Stylish Casual Spor...</td>
          <td>₹599</td>
        </tr>
        <tr>
          <th>27</th>
          <td>Nilatin</td>
          <td>STYLISH MENS BLACK TRENDY SNEAKER FOR MENS Sne...</td>
          <td>₹424</td>
        </tr>
        <tr>
          <th>28</th>
          <td>World Wear Footwear</td>
          <td>Sneakers For Men</td>
          <td>₹209</td>
        </tr>
        <tr>
          <th>29</th>
          <td>World Wear Footwear</td>
          <td>Lightweight Pack Of 1 Trendy Sneakers Sneakers...</td>
          <td>₹199</td>
        </tr>
      </tbody>
    </table>
    </div>







.. code:: ipython3

    driver=webdriver.Edge(r"C:/Python/msedgedriver.exe")
    url=('http://www.myntra.com/shoes')
    driver.get(url)

.. code:: ipython3

    price_filter=driver.find_elements_by_xpath("//label[@class='common-customCheckbox vertical-filters-label']")

.. code:: ipython3

    price_filter[7].click()

.. code:: ipython3

    colour_filter=driver.find_elements_by_xpath("//label[@class='common-customCheckbox']")
    colour_filter[0].click()

.. code:: ipython3

    Brand3_list=[]
    Description3_list=[]
    Price3_list=[]

.. code:: ipython3

    brands_tags3=driver.find_elements_by_xpath("//h3[@class='product-brand']")
    brands_tags3[0:100]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="87888753-0c2e-4105-bbd8-cfcf78a7ea55")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="ffc374e3-0ed0-41bd-ab25-fd7b001bd9ea")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="a81d4c04-bebd-488c-a74f-c50afda52c61")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="68ac9106-d698-4e37-9132-0e89cdcb1a7e")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="11c3c41e-ffa5-4b0f-8f31-578d763414af")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="c61ccd34-d4ea-40e4-9d01-cff0f89ae5b0")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="f08f202c-b2f0-47df-b2a1-4a397ddfd240")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="0f77c942-816b-4369-88d4-92f40129c121")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="3f02044e-79de-4aa4-97b9-dd63f816c485")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="f4c32193-f227-4bda-8113-a6022a69e398")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="27a29fcf-9c53-41ba-a63b-f0293177c99d")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="97abca4f-8f76-49bd-937c-aa2794b4bd8d")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="a14c7790-5281-4468-8803-55cce1917b66")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="d3809519-7cc9-458a-8735-ab461ec2b775")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="634addc9-db05-4bef-adb1-88da6050b81d")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="08bb3874-5f04-47b8-acea-8fda96290bfe")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="9528900f-4a62-4238-a059-9b991b983dbd")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="c886a9f2-0d8c-4352-bc3b-1249c1a7970e")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="44372fd3-9101-4c6f-966c-a0ac440d3718")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="f1947a7d-010e-41d7-a885-c314a7309c62")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="c383fb71-cd73-44de-a008-9944dd9eb49f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="dc6af039-7721-44a8-bbbe-6494867bd6aa")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="aa38e651-5dd5-43fc-b882-ba4fd0b68f56")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="1be1ef60-4ff0-478c-a12f-4c0a852ac4b0")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="0858daa6-649d-43fa-ac81-71361488aab0")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="530e06ae-d8b6-4b66-b4e1-036ba33c2b71")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="079ce0d6-9861-47a1-8c48-a4a48272efce")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="654f1658-dec1-4dee-8c16-087480526ece")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="cd707e36-ee43-4256-a49d-4d898fe855eb")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="0a301272-0a96-402b-8eac-fd2bcafe2654")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="02353654-a110-486b-b73c-3f2564454b49")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="47d4d072-4335-441b-ba4b-2708ef9d1409")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="8d5acef5-264d-486e-8b00-23fbd94aac15")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="e6f625d0-5fa6-4eb9-86a7-8ab3142019a4")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="464ceb00-9037-4e9e-a184-44bef0e1791c")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="a57edd15-26e2-47cc-bf15-fc464492988d")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="1ccfd8ec-2ecc-4024-8015-f96f55a699a0")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="12bd5bf0-aa26-4bd6-9f8e-1b41a1e53ddf")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="0aafd80a-9726-473d-b2f6-702c428db0fa")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="ec0fc187-7845-4aa6-9b7f-f513fb055abf")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="23876a02-c6c4-43c9-9f41-76635524a1c6")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="375114c9-7085-476f-9357-b9ff705502a9")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="7737c270-9ee7-4b12-afa2-dec5cd49e9e2")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="593d8540-ab38-437a-bd4c-23cda6dbe59e")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="9a18ff20-c2ae-4fdf-920a-94f32e7ac73b")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="e435c8bd-15fa-4492-a8b9-cba69b70d1e0")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="ae4de2d1-391c-48d5-938b-a71c9f3fe976")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="29fc693a-d9bd-4a27-9f21-efe964d52672")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="99db0ca2-fcf4-4cd5-930c-ec4a8b76bdaf")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="0bd95c9c-d758-4b24-8be2-393d59959f8e")>]



.. code:: ipython3

    for i in brands_tags3:
        Brand=i.text
        Brand3_list.append(Brand)
    Brand3_list[0:100]




.. parsed-literal::

    ['Puma',
     'Puma',
     'Nike',
     'Puma',
     'Red Tape',
     'Skechers',
     'Puma',
     'Red Tape',
     'Puma',
     'Skechers',
     'PUMA Motorsport',
     'Provogue',
     'Louis Philippe',
     'Red Tape',
     'Eego Italy',
     'Red Tape',
     'Lancer',
     'Louis Philippe',
     'Nike',
     'Roadster',
     'Monrow',
     'Skechers',
     'Skechers',
     'Nike',
     'Nike',
     'Red Tape',
     'one8 x PUMA',
     'Skechers',
     'PUMA Motorsport',
     'Skechers',
     'Sparx',
     'San Frissco',
     'Skechers',
     'Action',
     'Nike',
     'U.S. Polo Assn.',
     'RINDAS',
     'Mactree',
     'Campus',
     'DEAS',
     'Nike',
     'Red Tape',
     'ADIDAS',
     'Skechers',
     'INVICTUS',
     'U.S. Polo Assn.',
     'Lancer',
     'Red Tape',
     'one8 x PUMA',
     'Mochi']



.. code:: ipython3

    import time

.. code:: ipython3

    next_button=driver.find_element_by_xpath("/html/body/div[2]/div/div[1]/main/div[3]/div[2]/div/div[2]/section/div[2]/ul/li[12]")
    next_button.click()

.. code:: ipython3

    B_list=[]        
    for i in range(0,2):    
        brands_tags3=driver.find_elements_by_xpath("//h3[@class='product-brand']")  
        for i in brands_tags3:   
            brands=i.text     
            B_list.append(brands)   
        next_button=driver.find_element_by_xpath("/html/body/div[2]/div/div[1]/main/div[3]/div[2]/div/div[2]/section/div[2]/ul/li[12]")
        next_button.click()    
        time.sleep(5)       
    
             
           
         
       
    
    

.. code:: ipython3

    B_list




.. parsed-literal::

    ['Mochi',
     'Puma',
     'Reebok',
     'Puma',
     'Nike',
     'Puma',
     'Red Tape',
     'Red Tape',
     'Nike',
     'Skechers',
     'Skechers',
     'Campus',
     'Nike',
     'Catwalk',
     'Skechers',
     'Roadster',
     'New Balance',
     'ADIDAS',
     'HRX by Hrithik Roshan',
     'Red Tape',
     'Red Tape',
     'Puma',
     'Puma',
     'one8 x PUMA',
     'AfroJack',
     'Red Tape',
     'Skechers',
     'Puma',
     'Nike',
     'Provogue',
     'ADIDAS',
     'Sir Corbett',
     'Skechers',
     'Fentacia',
     'Metro',
     'Red Tape',
     'San Frissco',
     'El Paso',
     'Red Tape',
     'Sparx',
     'WROGN',
     'ADIDAS',
     'London Rag',
     'Red Tape',
     'HRX by Hrithik Roshan',
     'Roadster',
     'mr.wonker',
     'U.S. Polo Assn.',
     'HRX by Hrithik Roshan',
     'Fentacia',
     'MANGO',
     'Shoetopia',
     'Skechers',
     'San Frissco',
     'Fentacia',
     'Mochi',
     'Killer',
     'Reebok',
     'INVICTUS',
     'Roadster',
     'ZAPATOZ',
     'AfroJack',
     'RINDAS',
     'HRX by Hrithik Roshan',
     'Puma',
     'M7 by Metronaut',
     'Fentacia',
     'PUMA Motorsport',
     'HRX by Hrithik Roshan',
     'Metro',
     'Shoetopia',
     'Allen Solly',
     'Skechers',
     'El Paso',
     'ASIAN',
     'Truffle Collection',
     'Skechers',
     'Puma',
     'Red Chief',
     'Anouk',
     'Metro',
     'CLYMB',
     'Clarks',
     'Catwalk',
     'ADIDAS',
     'Shoetopia',
     'HRX by Hrithik Roshan',
     'CLYMB',
     'Metro',
     'Red Tape',
     'San Frissco',
     'Missguided',
     'UNDER ARMOUR',
     'Sparx',
     'Quechua By Decathlon',
     'Crew STREET',
     'Anouk',
     'TARMAK By Decathlon',
     'Catwalk',
     'Carlton London sports']



.. code:: ipython3

    len(B_list)




.. parsed-literal::

    100



.. code:: ipython3

    B_list=Brand3_list

.. code:: ipython3

    len(Brand3_list)




.. parsed-literal::

    50



.. code:: ipython3

    description3_tags3=driver.find_elements_by_xpath("//h4[@class='product-product']")
    description3_tags3[0:100]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="59701146-7ca7-4bd6-9e2e-7c8ac399291c")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="963578b1-d5a1-48e6-ac70-28e6a962d1e0")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="84a2eb94-89d7-4e9f-9851-1518accb15e0")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="fbd35a8e-8069-4077-bb12-d1a3def3a644")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="3b917452-6421-4062-b0f0-3d0d2ad0c2d1")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="c44d76ed-3169-47e0-b51a-206de8714752")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="7926fad7-8df5-4a82-a713-42f7a3dc61e6")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="8700f89a-269b-4991-8e30-fb6d6debe8c5")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="f8093073-078f-4628-91c1-838578501915")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="221a3340-6097-49b0-a807-4ab164216e8e")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="2967b930-a24d-424f-97ef-76e6f62d89d4")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="b49647de-eac2-4197-b8c6-11ceddd0dedc")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="7ee1c205-9301-4faf-8571-072eddebccbc")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="b43dfd86-3a17-4bca-b194-b5ea3d90f9cf")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="3f483008-17e3-4271-a44a-363a0bc52729")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="3862a070-85a3-4364-a463-b386c98623f6")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="337f5235-ead2-4552-ad33-35e92aac2f6d")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="40349982-d89a-4c8e-8562-f86fd7b57466")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="59808f83-bf9e-457a-af9b-97e10beedced")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="ef783605-24f4-4845-bb8d-a6615eeea5d7")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="79bd6fff-44b0-4097-a53c-5cd25fa02704")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="4e7aec94-897e-4d86-b4c0-22b0c54d029c")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="0a378f25-5e67-4d07-b036-40993c0ca905")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="b215e6d3-7dfc-4da7-95e3-5532ac726021")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="b686b236-a55f-4659-b1f3-3eae60d79aad")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="6d96b726-1c1f-4a5d-a68c-874a31bcf5a7")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="0ae88d93-e8b5-4a5f-81a7-2b3b50761caa")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="652bd5a5-26df-43d4-bc8a-d025bb72c954")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="e5d1e0eb-f758-47bf-ab13-55c09d835ae1")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="612c0882-5f31-458f-950d-7c4807a7e5a5")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="3c1c428c-7c43-4e0a-adbb-f1dd65cef381")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="3ec7fd97-a122-45f3-8cb7-9780ada2590a")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="8d7b02f5-7948-488f-a087-5306dfcbd276")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="52021b6a-2b90-4878-bdf2-b4ffa8f15b83")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="1396e868-4c10-4437-82fa-276cc49fc415")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="5b0cd974-52a9-420b-a407-05a1b5d3e850")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="1e5305d8-9880-437c-a28b-7b219a7b71c3")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="9c7f3841-603d-48f9-9b0e-2ebb06f63f70")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="50e03c33-73ab-4ea3-911e-7ae76265b165")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="f08d0936-dbf5-4de9-a1f8-c01d9c168d02")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="02461f39-bba6-4a08-a617-306c152ae118")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="fef3fcbf-36e7-4da1-9939-62326e040563")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="2a9ce0eb-7af8-430d-a163-d1b9463fa1ed")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="7053323c-dc43-4844-897b-dd53fdc1dfd5")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="a554f9fc-7b5a-45a9-bb72-d1dcf6742534")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="1a55dfce-cb9b-4837-9a00-9e6300f9aab4")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="b522a9dd-1dba-4e4c-ac82-8d77da2e1488")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="d20ed391-9207-4d6c-8ae7-53d5b6c8cdae")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="13ae21fb-7f7a-46c1-8cde-3f33bd88e025")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="3e45b950-b6cc-4fc4-88e7-8f1fc31b4f6f")>]



.. code:: ipython3

    for i in description3_tags3:
        description=i.text
        Description3_list.append(description)
    Description3_list[0:100]




.. parsed-literal::

    ['Unisex Kent 2.0 IDP Sneakers',
     'Men Running Shoes',
     'Kids Revolution 4 Running',
     'Men HYBRID Fuego Running Shoes',
     'Men Walking Shoes',
     'Men GO WALK 4 Walking Shoes',
     'Men Solid Running Shoes',
     'Kids Sports Shoes',
     'Women Better Foam Training',
     'ULTRA FLEX 2.0 - LITEWILDE Run',
     'Unisex Mercedes F1 R-Cat',
     'Men Black Solid Formal Debys',
     'Men Solid Driving Shoes',
     'Men Solid Leather Formal Oxfords',
     'Men Trekking Shoes',
     'Men Walking Shoes',
     'Men Running Shoes',
     'Men Solid Driving Shoes',
     'LEGEND ESSENTIAL Training Shoe',
     'Men Casual Sneakers',
     'Women Sandals',
     'Women Walking Shoes',
     'Men GO WALK EVOLUTION Walking',
     'Men Vapor Lite HC Tennis Shoes',
     'Kids REVOLUTION 4 Shoes',
     'Men Walking Shoes',
     'Men Fuse One8 Training Shoes',
     'Men BOUNDER-MIRKLE Sneakers',
     'Unisex Mercedes F1 Sneakers',
     'Women Go Walk J Walking Shoes',
     'Men Running Sports Shoes',
     'Men Solid Formal Loafers',
     'Men TRACK - KNOCKHILL Sneakers',
     'Men Running Shoes',
     'Men KF 5 EP Basketball Shoes',
     'Men Bronx Sneakers',
     'Women Colourblocked Sneakers',
     'Men Suede Loafers',
     'Men DRAGON Running Shoes',
     'Women Mules Flats',
     'Men Zoom Court Lite 3 Tennis',
     'Men Woven Design Sneakers',
     'Men Flydoot Running Shoes',
     'Men Go Walk 5 Walking Shoes',
     'Men Formal Slip-on Shoes',
     'Men LEBRON 2.0 Walking Shoes',
     'Men Regular Running Shoes',
     'Men Walking Shoes',
     'Men Strike Textured Sneakers',
     'Men Solid Leather Formal Slip-Ons',
     'Unisex Kent 2.0 IDP Sneakers',
     'Men Running Shoes',
     'Kids Revolution 4 Running',
     'Men HYBRID Fuego Running Shoes',
     'Men Walking Shoes',
     'Men GO WALK 4 Walking Shoes',
     'Men Solid Running Shoes',
     'Kids Sports Shoes',
     'Women Better Foam Training',
     'ULTRA FLEX 2.0 - LITEWILDE Run',
     'Unisex Mercedes F1 R-Cat',
     'Men Black Solid Formal Debys',
     'Men Solid Driving Shoes',
     'Men Solid Leather Formal Oxfords',
     'Men Trekking Shoes',
     'Men Walking Shoes',
     'Men Running Shoes',
     'Men Solid Driving Shoes',
     'LEGEND ESSENTIAL Training Shoe',
     'Men Casual Sneakers',
     'Women Sandals',
     'Women Walking Shoes',
     'Men GO WALK EVOLUTION Walking',
     'Men Vapor Lite HC Tennis Shoes',
     'Kids REVOLUTION 4 Shoes',
     'Men Walking Shoes',
     'Men Fuse One8 Training Shoes',
     'Men BOUNDER-MIRKLE Sneakers',
     'Unisex Mercedes F1 Sneakers',
     'Women Go Walk J Walking Shoes',
     'Men Running Sports Shoes',
     'Men Solid Formal Loafers',
     'Men TRACK - KNOCKHILL Sneakers',
     'Men Running Shoes',
     'Men KF 5 EP Basketball Shoes',
     'Men Bronx Sneakers',
     'Women Colourblocked Sneakers',
     'Men Suede Loafers',
     'Men DRAGON Running Shoes',
     'Women Mules Flats',
     'Men Zoom Court Lite 3 Tennis',
     'Men Woven Design Sneakers',
     'Men Flydoot Running Shoes',
     'Men Go Walk 5 Walking Shoes',
     'Men Formal Slip-on Shoes',
     'Men LEBRON 2.0 Walking Shoes',
     'Men Regular Running Shoes',
     'Men Walking Shoes',
     'Men Strike Textured Sneakers',
     'Men Solid Leather Formal Slip-Ons']



.. code:: ipython3

    next_button=driver.find_element_by_xpath("/html/body/div[2]/div/div[1]/main/div[3]/div[2]/div/div[2]/section/div[2]/ul/li[12]")
    next_button.click()

.. code:: ipython3

    D_list=[]        
    for i in range(0,2):    
        descriptions3_tags3=driver.find_elements_by_xpath("//h4[@class='product-product']")  
        for i in descriptions3_tags3:   
            description=i.text     
            D_list.append(description)   
        next_button=driver.find_element_by_xpath("/html/body/div[2]/div/div[1]/main/div[3]/div[2]/div/div[2]/section/div[2]/ul/li[12]")
        next_button.click()    
        time.sleep(5) 

.. code:: ipython3

    len(D_list)




.. parsed-literal::

    100



.. code:: ipython3

    D_list=Description3_list

.. code:: ipython3

    len(Description3_list)




.. parsed-literal::

    100



.. code:: ipython3

    Price3_tags=driver.find_elements_by_xpath("//span[@class='product-discountedPrice']")
    Price3_tags[0:50]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="597d313a-d962-46be-9049-d2d9ae007f06")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="b2f10a0e-8ef9-4e31-8f69-45997b0f24b1")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="8c5bc871-2bc6-4cee-9545-0553356b8967")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="c618eecc-943b-4131-b851-469892109deb")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="63bfd8b9-0756-4d54-9b05-b050a7d36eb6")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="738e7bb8-c42f-4b2c-bb6b-7f99d30d45c8")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="de31f30d-08ed-4a75-9224-7a0a0568ec1a")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="41c4d250-2247-4f51-954e-e608ca12ea57")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="a4399854-c23d-42cc-8211-0865b48b6578")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="a6b1aaac-1c32-488b-a910-cd45bc35084b")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="65cc8e24-d7db-494f-96e3-4e2e2dc73ddc")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="66338e3a-8a89-40fb-88a7-83099c7ba48f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="8a23a823-d86d-4f49-abbf-812c9076713b")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="b19f4c36-5e95-4ac3-a735-dcfb2a55d3ce")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="2226cd7a-9473-4d53-9fb7-b5b59503e56c")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="3580bd73-2bfc-44d0-aafb-199c95d7a2cb")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="a8bd0951-7e58-429d-8621-76536f8935e2")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="ea539ddb-1d83-4fee-86f2-adab98f53bb5")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="c13a6c42-75d8-4b92-98f7-39c72e07feb8")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="f749eece-004b-4128-b731-3b33b60f474f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="c9db8ed3-fe29-46b4-8085-ef9290cc88aa")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="23965ba5-112d-430f-8668-3f1808cbdac9")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="bec571c5-fa67-407c-9e4f-ac1bcc3fb5d3")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="96396d51-8fb6-4a11-9ac8-3269c92b5bcf")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="2732c44e-6b2a-47a6-882b-192dc259f456")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="89898c8d-4588-4551-962b-87e3191806c6")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="4a81d1f8-08c0-487c-a1ed-104ea7594f84")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="687b0d6b-ebc1-41d3-a3a5-59f790180aa9")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="a03d0e55-ba7e-4825-90aa-6d386d9a9776")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="342d50eb-c74b-4357-9af7-b53332945d84")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="4da13ab3-eac7-4b9c-b2f2-25cfb50db455")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="3d7c4f11-78a6-4f76-b615-03e1c5b43f21")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="35b871d8-1e28-4338-9c62-392abfc47a0c")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="6591c172-ee71-4984-8d11-1999b57f010f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="d585ceb9-27fd-4dea-aa8f-b837b050a10e")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="b65d2ac7-2ea3-4a36-8d65-d365269a8f2f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="e3186e2b-7749-4670-8e82-43142e9c7122")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="0a785b0a-1374-44ea-b220-80efa235c6fc")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="c2aac214-5df6-4948-be95-ff01159f1461")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="29670cea-dd6f-48be-a7d3-ee4aba8eef8a")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="2fe5cec6-9a34-4864-8ce7-9bc44c847e39")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="b054a927-871e-4c76-b204-f611fade34d1")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="a3e3aea9-1fb6-4cc5-ba82-31ee37b13018")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="e443af24-3357-4e07-936b-04dcb301f620")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="845e9795-4296-4373-ab28-ffce5659ecab")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="7ce24a33-1577-4201-8092-7b8b3cc30203")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="b97474f5-d211-46d9-b288-622bbb1001b9")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="a69bace9-9160-4a8b-b54e-878890d2206c")>,
     <selenium.webdriver.remote.webelement.WebElement (session="a776ae2e2b9e285684ac79ab5fe9c6be", element="d0abf4ed-053b-46da-967b-9c0f9f02fb8d")>]



.. code:: ipython3

    for i in Price3_tags:
        Price=i.text
        Price3_list.append(Price)
    Price3_list[0:4]




.. parsed-literal::

    ['Rs. 1649', 'Rs. 2749', 'Rs. 1502', 'Rs. 5524']



.. code:: ipython3

    next_button=driver.find_element_by_xpath("/html/body/div[2]/div/div[1]/main/div[3]/div[2]/div/div[2]/section/div[2]/ul/li[12]")
    next_button.click()

.. code:: ipython3

    P_list=[]        
    for i in range(0,2):    
        Price3_tags=driver.find_elements_by_xpath("//span[@class='product-discountedPrice']")  
        for i in Price3_tags:   
            Price=i.text     
            P_list.append(Price)   
        next_button=driver.find_element_by_xpath("/html/body/div[2]/div/div[1]/main/div[3]/div[2]/div/div[2]/section/div[2]/ul/li[12]")
        next_button.click()    
        time.sleep(5) 

.. code:: ipython3

    len(P_list)




.. parsed-literal::

    85



.. code:: ipython3

    P_list=Price3_list

.. code:: ipython3

    len(Price3_list)




.. parsed-literal::

    49



.. code:: ipython3

    df5=pd.DataFrame()
    df5["BRAND"]=Brand3_list[:41]
    df5["DESCRIPTION"]=Description3_list[:41]
    df5["PRICE"]=Price3_list[:41]
    df5




.. raw:: html

    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    
        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>BRAND</th>
          <th>DESCRIPTION</th>
          <th>PRICE</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>Puma</td>
          <td>Unisex Kent 2.0 IDP Sneakers</td>
          <td>Rs. 1649</td>
        </tr>
        <tr>
          <th>1</th>
          <td>Puma</td>
          <td>Men Running Shoes</td>
          <td>Rs. 2749</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Nike</td>
          <td>Kids Revolution 4 Running</td>
          <td>Rs. 1502</td>
        </tr>
        <tr>
          <th>3</th>
          <td>Puma</td>
          <td>Men HYBRID Fuego Running Shoes</td>
          <td>Rs. 5524</td>
        </tr>
        <tr>
          <th>4</th>
          <td>Red Tape</td>
          <td>Men Walking Shoes</td>
          <td>Rs. 1224</td>
        </tr>
        <tr>
          <th>5</th>
          <td>Skechers</td>
          <td>Men GO WALK 4 Walking Shoes</td>
          <td>Rs. 4844</td>
        </tr>
        <tr>
          <th>6</th>
          <td>Puma</td>
          <td>Men Solid Running Shoes</td>
          <td>Rs. 2249</td>
        </tr>
        <tr>
          <th>7</th>
          <td>Red Tape</td>
          <td>Kids Sports Shoes</td>
          <td>Rs. 874</td>
        </tr>
        <tr>
          <th>8</th>
          <td>Puma</td>
          <td>Women Better Foam Training</td>
          <td>Rs. 2499</td>
        </tr>
        <tr>
          <th>9</th>
          <td>Skechers</td>
          <td>ULTRA FLEX 2.0 - LITEWILDE Run</td>
          <td>Rs. 3999</td>
        </tr>
        <tr>
          <th>10</th>
          <td>PUMA Motorsport</td>
          <td>Unisex Mercedes F1 R-Cat</td>
          <td>Rs. 3374</td>
        </tr>
        <tr>
          <th>11</th>
          <td>Provogue</td>
          <td>Men Black Solid Formal Debys</td>
          <td>Rs. 899</td>
        </tr>
        <tr>
          <th>12</th>
          <td>Louis Philippe</td>
          <td>Men Solid Driving Shoes</td>
          <td>Rs. 3599</td>
        </tr>
        <tr>
          <th>13</th>
          <td>Red Tape</td>
          <td>Men Solid Leather Formal Oxfords</td>
          <td>Rs. 1724</td>
        </tr>
        <tr>
          <th>14</th>
          <td>Eego Italy</td>
          <td>Men Trekking Shoes</td>
          <td>Rs. 987</td>
        </tr>
        <tr>
          <th>15</th>
          <td>Red Tape</td>
          <td>Men Walking Shoes</td>
          <td>Rs. 1349</td>
        </tr>
        <tr>
          <th>16</th>
          <td>Lancer</td>
          <td>Men Running Shoes</td>
          <td>Rs. 1359</td>
        </tr>
        <tr>
          <th>17</th>
          <td>Louis Philippe</td>
          <td>Men Solid Driving Shoes</td>
          <td>Rs. 3249</td>
        </tr>
        <tr>
          <th>18</th>
          <td>Nike</td>
          <td>LEGEND ESSENTIAL Training Shoe</td>
          <td>Rs. 3596</td>
        </tr>
        <tr>
          <th>19</th>
          <td>Roadster</td>
          <td>Men Casual Sneakers</td>
          <td>Rs. 880</td>
        </tr>
        <tr>
          <th>20</th>
          <td>Monrow</td>
          <td>Women Sandals</td>
          <td>Rs. 1299</td>
        </tr>
        <tr>
          <th>21</th>
          <td>Skechers</td>
          <td>Women Walking Shoes</td>
          <td>Rs. 2999</td>
        </tr>
        <tr>
          <th>22</th>
          <td>Skechers</td>
          <td>Men GO WALK EVOLUTION Walking</td>
          <td>Rs. 4399</td>
        </tr>
        <tr>
          <th>23</th>
          <td>Nike</td>
          <td>Men Vapor Lite HC Tennis Shoes</td>
          <td>Rs. 5436</td>
        </tr>
        <tr>
          <th>24</th>
          <td>Nike</td>
          <td>Kids REVOLUTION 4 Shoes</td>
          <td>Rs. 1502</td>
        </tr>
        <tr>
          <th>25</th>
          <td>Red Tape</td>
          <td>Men Walking Shoes</td>
          <td>Rs. 1574</td>
        </tr>
        <tr>
          <th>26</th>
          <td>one8 x PUMA</td>
          <td>Men Fuse One8 Training Shoes</td>
          <td>Rs. 6799</td>
        </tr>
        <tr>
          <th>27</th>
          <td>Skechers</td>
          <td>Men BOUNDER-MIRKLE Sneakers</td>
          <td>Rs. 3684</td>
        </tr>
        <tr>
          <th>28</th>
          <td>PUMA Motorsport</td>
          <td>Unisex Mercedes F1 Sneakers</td>
          <td>Rs. 3599</td>
        </tr>
        <tr>
          <th>29</th>
          <td>Skechers</td>
          <td>Women Go Walk J Walking Shoes</td>
          <td>Rs. 4399</td>
        </tr>
        <tr>
          <th>30</th>
          <td>Sparx</td>
          <td>Men Running Sports Shoes</td>
          <td>Rs. 1574</td>
        </tr>
        <tr>
          <th>31</th>
          <td>San Frissco</td>
          <td>Men Solid Formal Loafers</td>
          <td>Rs. 1598</td>
        </tr>
        <tr>
          <th>32</th>
          <td>Skechers</td>
          <td>Men TRACK - KNOCKHILL Sneakers</td>
          <td>Rs. 2999</td>
        </tr>
        <tr>
          <th>33</th>
          <td>Action</td>
          <td>Men Running Shoes</td>
          <td>Rs. 1959</td>
        </tr>
        <tr>
          <th>34</th>
          <td>Nike</td>
          <td>Men KF 5 EP Basketball Shoes</td>
          <td>Rs. 6965</td>
        </tr>
        <tr>
          <th>35</th>
          <td>U.S. Polo Assn.</td>
          <td>Men Bronx Sneakers</td>
          <td>Rs. 2399</td>
        </tr>
        <tr>
          <th>36</th>
          <td>RINDAS</td>
          <td>Women Colourblocked Sneakers</td>
          <td>Rs. 895</td>
        </tr>
        <tr>
          <th>37</th>
          <td>Mactree</td>
          <td>Men Suede Loafers</td>
          <td>Rs. 898</td>
        </tr>
        <tr>
          <th>38</th>
          <td>Campus</td>
          <td>Men DRAGON Running Shoes</td>
          <td>Rs. 1624</td>
        </tr>
        <tr>
          <th>39</th>
          <td>DEAS</td>
          <td>Women Mules Flats</td>
          <td>Rs. 599</td>
        </tr>
        <tr>
          <th>40</th>
          <td>Nike</td>
          <td>Men Zoom Court Lite 3 Tennis</td>
          <td>Rs. 4556</td>
        </tr>
      </tbody>
    </table>
    </div>







.. code:: ipython3

    driver=webdriver.Edge(r"C:/Python/msedgedriver.exe")

.. code:: ipython3

    url="https://www.amazon.in/"
    driver.get(url)

.. code:: ipython3

    search_col=driver.find_element_by_xpath("//input[@class='nav-input nav-progressive-attribute']")
    search_col.send_keys('laptop')

.. code:: ipython3

    search_button=driver.find_elements_by_xpath("//input[@class='nav-input nav-progressive-attribute']")
    search_button[1].click()

.. code:: ipython3

    title8_list=[]
    Rating8_list=[]
    Price8_list=[]

.. code:: ipython3

    title_tags8=driver.find_elements_by_xpath("//span[@class='a-size-medium a-color-base a-text-normal']")
    title_tags8




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="a3e7d53e-c3a5-43c5-b578-f76eea549c9f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="2bb498fb-7ab6-40f0-bfac-724fdf17e938")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="0a5dbfcf-da53-42ac-b53b-023021336c52")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="85689779-5c61-4ee6-9995-960630384d33")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="654b240d-664a-48c4-9efc-36deb5c428ff")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="510878ce-6cff-4b60-8f0b-9d83d800372b")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="36a1830b-8ad8-46ae-a0e0-d139d04d3465")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="f104178d-a849-4e46-acbe-b6229de25ecd")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="12cfa3c7-4f28-4821-88fa-01edcf6a5307")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="176bc4d2-2c08-4660-bfc0-bdc22cf86374")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="783d39ab-5552-4c32-a4ac-2cd528b90a6c")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="885ac6e3-1ca4-4e97-8f1f-dabddbee4454")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="12ba7903-24f0-4ee2-bdb4-fd2be8f7803f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="b2c7ae4a-bcba-4895-ad86-1313d24664be")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="b5e7abfb-cf02-46d2-8af7-ccbab46ca6f3")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="a4f3ea1b-ebe5-4bd3-a717-141be43d5265")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="eaee7ad9-876c-4273-95f5-d5dbf7ba952a")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="92262748-85e8-4e1b-9583-91b529c72702")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="411fb2a0-4efa-4f92-8e58-2ad9e0c56557")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="32a9bdf9-176c-40b6-947c-d2ecd0d89a94")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="b7e4f225-cca9-4c68-afb9-416a9c8e3b90")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="cf4dba80-8b7f-4725-a9e3-1ef6de3063f4")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="828be498-adf3-4012-ba04-46a4e2ee11c2")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="4bfc57e6-32ef-4ac2-aa64-b5417c1068ab")>]



.. code:: ipython3

    for i in title_tags8:
        title=i.text
        title8_list.append(title)
    title8_list




.. parsed-literal::

    ['Microsoft Surface GO 2 STQ-00013 10.1" (26.54 cms) Laptop (Gold Processor 4425Y/8GB/128GB SSD/Windows 10 Home in S Mode/Intel UHD 615 Graphics), Platinum',
     'Microsoft Surface Pro 7 VDV-00015 12.3" (31.24 cms) Touchscreen 2-in-1 Laptop (10th Gen Intel Core i5/8GB/128GB SSD/Windows 10 Home/Intel Iris Plus Graphics), Platinum',
     'ASUS VivoBook 15 (2021), 15.6-inch (39.62 cm) HD, Dual Core Intel Celeron N4020, Thin and Light Laptop (4GB RAM/256GB SSD/Integrated Graphics/Windows 11 Home/Transparent Silver/1.8 Kg), X515MA-BR011W',
     '15.6 Inch Ultra Slim Laptop, IPS 1920x1080 HD Screen 8G RAM 128GB SSD with WiFi Backlit Keyboard for Intel J4125,2.00 GHz-2.70 GHz,Quad Core and Four Threads Windows 11(EU)',
     "Lenovo IdeaPad 3 Intel Celeron N4020 14'' HD Thin & Light Laptop (4GB/256GB SSD/Windows 11/MS Office 2021/Platinum Grey/1.5Kg), 81WH007KIN",
     'LG Gram 16 inches Intel Evo 11th Gen Core i7 Ultra-Light Laptop (16 GB RAM, 512 GB SSD, New Windows 11 Home Preload, Iris Xe Graphics, USC -C x 2 (with Power), 1.19 kg, 16Z90P-G.AH85A2, Black)',
     "Lenovo IdeaPad 1 Intel Celeron N4020 11.6'' HD Laptop (4GB/256GB SSD/Windows 11/Office 2021/Platinum Grey/1.2Kg), 81VT009UIN",
     'Dell New Vostro 3510 Laptop, Intel i3-1005G1, Win11 + Office\'21, 8GB GDDR4, 512GB SSD, 15.6" (39.62Cms) FHD WVA AG, Carbon (ICC-D585033WIN8) 1.8Kgs',
     'Lenovo IdeaPad 3 11th Gen Intel i3 15.6" FHD Thin & Light Laptop (8GB/512GB SDD/Windows 11/MS Office 2021/2 Yr Warranty/Arctic Grey/1.65Kg), 82H801L7IN',
     'HP 247 G8 Laptop (Athlon P-3045B HD/ 14" HD (35.56 cms) /8GB RAM DDR4 /1TB HDD / W11 SL)One Year Warranty, Black, 67U77PA)',
     'Lenovo IdeaPad Slim 3 11th Gen Intel Core i5 14" FHD Thin & Light Laptop (8GB/512GB SDD/Win11/Office 2021/Backlit/Fingerprint Reader/2Yr Warranty/3months Xbox Game Pass/Arctic Grey/1.41Kg), 82H701ASIN',
     'HP Victus Latest AMD Ryzen 5 5600H Processor 16.1 inch(40.9cm) FHD Gaming Laptop (8GB RAM/512GB SSD/4GB GTX 1650 Graphics/B&O Audio/Flicker Free Display/BacklitKB/Win 10/MS Office/2.48 Kg),16-E0075ax',
     'MSI Modern 14, Intel i3-10110U, 14" FHD IPS-Level Panel Laptop (4GB/256GB NVMe SSD/Windows 10 Home/Intel UHD Graphics/Carbon Grey/1.3Kg), B10MW-660IN',
     'HP Chromebook 14 Intel Celeron N4020-4GB SDRAM/64GB eMMC + 256GB Expandable Storage 14inch(35.6 cm) Thin & Light Touchscreen Laptop (Chrome OS/B&O/Google Assistant/BL Keyboard/1.46 kg),14a-na0003TU',
     'Lenovo IdeaPad Slim 3 10th Gen Intel Core i3 15.6"(39.62cm) FHD Thin & Light Laptop (8GB/256GB SSD/UHD Graphics/Windows 11/MS Office 2021/Platinum Grey/1.7Kg), 81WB018EIN',
     'ASUS TUF Gaming F15 (2021), 15.6" (39.62 cms) FHD 144Hz, Intel Core i5-10300H 10th Gen, GTX 1650 4GB Graphics, Gaming Laptop (8GB RAM/512GB NVMe SSD/Windows 11/Black/2.30 Kg), FX506LH-HN258W',
     'HP 14s 11th Gen Intel Core i3- 8GB RAM/256GB SSD 14 inch(35.6cm) FHD,Micro-Edge,Anti-Glare,IPS Display/UHD Graphics/ Win 11/ MS Office/ Alexa Built-in/ 1.46kg/ Natural Silver - 14s-dy2506TU',
     'Acer Aspire 3 AMD 3020e Dual core Processor 14 inches (35.5 cm) Laptop (4GB RAM/256GB SSD/Windows 11 Home/Black/1.9 Kg, A314-22)',
     'Lenovo ThinkBook 14 Intel Core i5 11th Gen 14" (35.56cm) FHD IPS Thin & Light Laptop (16GB RAM/512GB SSD/Windows 11 Home/MS Office 2021/FPR/Intel Iris Xe Graphics Mineral Grey/1.4 kg), 20VDA0TLIH',
     'Lenovo V14-IGL Intel Celeron N4020 4M Cache, up to 2.80 GHz Laptop with 4 GB Ram, 256 SSD, Windows 11 Home ,14" Full HD(1920x1080) Display, 1 Year Onsite Warranty',
     'HP 14s, AMD Ryzen 5-5500U 14 inches FHD, IPS, Micro-Edge Display Laptop (8GB RAM/512GB SSD /Radeon Graphics/Windows 11/Alexa/Backlit Keyboard/MS Office/1.46kg, 14s-fq1092au)',
     'HP 14s 11th Gen Intel Core i3- 8GB RAM/256GB SSD 14 inch(35.6cm) FHD,Micro-Edge,Anti-Glare,IPS Display/UHD Graphics/ Win 11/ MS Office/ Alexa Built-in/ 1.46kg/ Natural Silver - 14s-dy2506TU',
     'Lenovo IdeaPad Slim 3 11th Gen Intel Core i5 14" FHD Thin & Light Laptop (8GB/512GB SDD/Win11/Office 2021/Backlit/Fingerprint Reader/2Yr Warranty/3months Xbox Game Pass/Arctic Grey/1.41Kg), 82H701ASIN',
     'Honor MagicBook X 15, Intel Core i3-10110U / 15.6 inch (39.62 cm) FHD IPS Anti-Glare Thin and Light Laptop (8GB/256GB PCIe SSD/Windows 10/Aluminium Metal Body/1.56Kg), Silver, (BohrBR-WAI9A)']



.. code:: ipython3

    ratings_tags8=driver.find_elements_by_xpath("//span[@class='a-icon-alt']")
    ratings_tags8




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="153dcbfe-461b-4b6b-b40d-e560f9682f1f")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="ec18d212-cac6-4086-9c3f-72857c5c92c0")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="6f70da05-f702-4160-baeb-83c188fae554")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="7859326b-0d94-42f2-a648-029ca1f288b0")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="edfacff5-f2c4-42bd-b7d4-48d4348ffc2b")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="dc80c4e6-7b35-4050-9b05-86f759243303")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="99d4dffb-2760-4bd9-a145-3fa4fedeeebd")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="ee98313c-5529-4dc3-a5d1-85d31ade6bed")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="2b1054f4-91bb-4196-83e2-d7abd53a17d6")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="385976fb-e6bc-449d-be20-babfb724fea6")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="b4bb4f29-8460-4c67-b5b0-594b738abc1c")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="1261ec85-819a-4f13-89e7-defeaaacf8eb")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="82c139b2-8703-453a-8c06-c87ae51378b7")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="c1d61acd-733f-443e-b768-576f48204a5c")>]



.. code:: ipython3

    for i in ratings_tags8:
        ratings=i.text
        Rating8_list.append(ratings)
    Rating8_list




.. parsed-literal::

    ['',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '']



.. code:: ipython3

    price_tags8=driver.find_elements_by_xpath("//span[@class='a-price-whole']")
    price_tags8




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="2e2e5a71-a0dd-4062-bb31-85a5ceba7ff2")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="3831e58a-73cc-4bd7-a940-e27649316bde")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="fc59e4ce-830e-4489-aef0-a5075695b81d")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="72495a48-9ac2-4650-9a6c-170bd084a516")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="7ede6860-5ee2-4c2f-b987-e80a5fcc1ee5")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="a5b3fca5-e4b3-406d-afee-a4780dfcb7f7")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="9cb70f1d-3fa0-43ca-8f46-59591a9e41c7")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="bf8593ef-e2ef-49bc-9a71-f26cb95c3954")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="7394b78d-4323-4adf-992f-e3c24049d5d4")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="6f0621c8-f9e3-48d2-82d4-8f4c8a87d968")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="b83ddf53-05bb-47b7-9803-f228fb1943bd")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="298851a9-2e4e-4823-8e52-2f84fd3e7e6b")>,
     <selenium.webdriver.remote.webelement.WebElement (session="4371f2921df474289e96558091705f2b", element="95331436-a132-4d74-a8c8-3d26f70091a4")>]



.. code:: ipython3

    for i in price_tags8:
        price=i.text
        Price8_list.append(price)
    Price8_list




.. parsed-literal::

    ['',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '',
     '1,44,990',
     '1,44,990',
     '3,01,990',
     '3,31,990',
     '2,85,390',
     '3,99,990',
     '2,05,990',
     '2,32,364',
     '3,29,990',
     '3,79,990',
     '1,38,000',
     '2,25,000',
     '2,50,000',
     '1,44,990',
     '1,44,990',
     '3,01,990',
     '3,31,990',
     '2,85,390',
     '3,99,990',
     '2,05,990',
     '2,32,364',
     '3,29,990',
     '3,79,990',
     '1,38,000',
     '2,25,000',
     '2,50,000']



.. code:: ipython3

    import pandas as pd
    laptop_df=pd.DataFrame()
    
    laptop_df['TITLE']=title8_list[:10]
    laptop_df['RATING']=Rating8_list[:10]
    laptop_df['PRICE']=Price8_list[:10]
    
    laptop_df




.. raw:: html

    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    
        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>TITLE</th>
          <th>RATING</th>
          <th>PRICE</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>Microsoft Surface GO 2 STQ-00013 10.1" (26.54 ...</td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <th>1</th>
          <td>Microsoft Surface Pro 7 VDV-00015 12.3" (31.24...</td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <th>2</th>
          <td>ASUS VivoBook 15 (2021), 15.6-inch (39.62 cm) ...</td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <th>3</th>
          <td>15.6 Inch Ultra Slim Laptop, IPS 1920x1080 HD ...</td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <th>4</th>
          <td>Lenovo IdeaPad 3 Intel Celeron N4020 14'' HD T...</td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <th>5</th>
          <td>LG Gram 16 inches Intel Evo 11th Gen Core i7 U...</td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <th>6</th>
          <td>Lenovo IdeaPad 1 Intel Celeron N4020 11.6'' HD...</td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <th>7</th>
          <td>Dell New Vostro 3510 Laptop, Intel i3-1005G1, ...</td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <th>8</th>
          <td>Lenovo IdeaPad 3 11th Gen Intel i3 15.6" FHD T...</td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <th>9</th>
          <td>HP 247 G8 Laptop (Athlon P-3045B HD/ 14" HD (3...</td>
          <td></td>
          <td></td>
        </tr>
      </tbody>
    </table>
    </div>





.. code:: ipython3

    import selenium
    import pandas as pd
    from selenium import webdriver
    import warnings
    warnings.filterwarnings("ignore")
    import time

.. code:: ipython3

    driver=webdriver.Edge(r"C:/Python/msedgedriver.exe")

.. code:: ipython3

    driver.get('https://www.ambitionbox.com/')

.. code:: ipython3

    search_field_position=driver.find_elements_by_xpath('//div[@class="search-company"]')
    

.. code:: ipython3

    search_field_position.send_keys("Data Scientist")


::


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    ~\AppData\Local\Temp/ipykernel_15984/2012770218.py in <module>
    ----> 1 search_field_position.send_keys("Data Scientist")
    

    AttributeError: 'list' object has no attribute 'send_keys'


.. code:: ipython3

    search_button=driver.find_element_by_xpath("/html/body/div/div/div/div[2]/div[1]/div[1]/div/div/div/button/span")
    search_button.click()

.. code:: ipython3

    location_filter=driver.find_elements_by_xpath("/html/body/div/div/div/div[2]/div[1]/div[2]/div[1]/div/div/div/div[2]/div[1]/p")
    location_filter[0].click()

.. code:: ipython3

    company_name_list=[]
    Num_of_days_list=[]
    Ratings_of_Company_list=[]

.. code:: ipython3

    title_tags9=driver.find_elements_by_xpath("//div[@class='company-info']")
    title_tags9[0:4]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="b7b029f0f2468c1fc11cbebf877cb2de", element="648b118d-ac4e-40be-900c-8185241ee506")>,
     <selenium.webdriver.remote.webelement.WebElement (session="b7b029f0f2468c1fc11cbebf877cb2de", element="9c621b5b-48c6-4f30-a430-bf263506073a")>,
     <selenium.webdriver.remote.webelement.WebElement (session="b7b029f0f2468c1fc11cbebf877cb2de", element="8c8b0ea8-044e-4a4e-bfc4-a9c54313ee22")>,
     <selenium.webdriver.remote.webelement.WebElement (session="b7b029f0f2468c1fc11cbebf877cb2de", element="86dbffd9-421a-42ac-91da-8fd9bd45f276")>]



.. code:: ipython3

    for i in title_tags9:             
        title=i.text                  
        company_name_list.append(title)      
    company_name_list[0:4]




.. parsed-literal::

    ['Ericsson India Global Services Pvt. Ltd.\n · \n4.3\nbased on 4.7k Reviews',
     'Ericsson India Global Services Pvt. Ltd.\n4.3\n(4.7k Reviews)',
     'EXL Services.com ( I ) Pvt. Ltd.\n3.9\n(4.4k Reviews)',
     'GENPACT India Private Limited\n4.0\n(17.5k Reviews)']



.. code:: ipython3

    rating_tags9=driver.find_elements_by_xpath("//span[@class='body-small']")   
    rating_tags9[0:4]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="b7b029f0f2468c1fc11cbebf877cb2de", element="b84fa077-247c-4b8e-95cf-13e28b3a5387")>,
     <selenium.webdriver.remote.webelement.WebElement (session="b7b029f0f2468c1fc11cbebf877cb2de", element="c3e949ae-73d6-4fab-8bf0-1db0d65b4336")>,
     <selenium.webdriver.remote.webelement.WebElement (session="b7b029f0f2468c1fc11cbebf877cb2de", element="2ba14b3b-9dfc-49f2-a35a-556dcdf9b4e4")>,
     <selenium.webdriver.remote.webelement.WebElement (session="b7b029f0f2468c1fc11cbebf877cb2de", element="8c7686c4-cc9b-4732-80a2-7311bd8db239")>]



.. code:: ipython3

    for i in rating_tags9:             
        rating=i.text                  
        Ratings_of_Company_list.append(rating)      
    Ratings_of_Company_list[0:4]




.. parsed-literal::

    ['4.3', '3.9', '4.0', '3.9']



.. code:: ipython3

    days_tags9=driver.find_elements_by_xpath("//span[@class='body-small-l']")   
    days_tags9[0:4]




.. parsed-literal::

    [<selenium.webdriver.remote.webelement.WebElement (session="b7b029f0f2468c1fc11cbebf877cb2de", element="d86294e5-46d9-471d-abf9-2692577760ee")>,
     <selenium.webdriver.remote.webelement.WebElement (session="b7b029f0f2468c1fc11cbebf877cb2de", element="25b53ec8-f391-406d-a38c-2da85a977c7e")>,
     <selenium.webdriver.remote.webelement.WebElement (session="b7b029f0f2468c1fc11cbebf877cb2de", element="3e1e15ba-dbce-4dea-b455-e57af9902a72")>,
     <selenium.webdriver.remote.webelement.WebElement (session="b7b029f0f2468c1fc11cbebf877cb2de", element="a62167a3-a737-421c-8f6d-274d14ff1ae6")>]



.. code:: ipython3

    for i in days_tags9:             
        days=i.text                  
        Num_of_days_list.append(days)      
    Num_of_days_list[0:4]




.. parsed-literal::

    ['2d ago', 'via naukri.com', '12d ago', 'via naukri.com']



.. code:: ipython3

    import pandas as pd
    df9=pd.DataFrame()
    
    df9['COMPANY']=company_name_list[:10]
    df9['RATING']=Ratings_of_Company_list[:10]
    df9['DAYS']=Num_of_days_list[:10]
    
    df9




.. raw:: html

    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    
        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>COMPANY</th>
          <th>RATING</th>
          <th>DAYS</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>Ericsson India Global Services Pvt. Ltd.\n · \...</td>
          <td>4.3</td>
          <td>2d ago</td>
        </tr>
        <tr>
          <th>1</th>
          <td>Ericsson India Global Services Pvt. Ltd.\n4.3\...</td>
          <td>3.9</td>
          <td>via naukri.com</td>
        </tr>
        <tr>
          <th>2</th>
          <td>EXL Services.com ( I ) Pvt. Ltd.\n3.9\n(4.4k R...</td>
          <td>4.0</td>
          <td>12d ago</td>
        </tr>
        <tr>
          <th>3</th>
          <td>GENPACT India Private Limited\n4.0\n(17.5k Rev...</td>
          <td>3.9</td>
          <td>via naukri.com</td>
        </tr>
        <tr>
          <th>4</th>
          <td>TECHNIP GLOBAL BUSINESS SERVICES PRIVATE LIMIT...</td>
          <td>4.0</td>
          <td>24d ago</td>
        </tr>
        <tr>
          <th>5</th>
          <td>GENPACT India Private Limited\n4.0\n(17.5k Rev...</td>
          <td>3.8</td>
          <td>via naukri.com</td>
        </tr>
        <tr>
          <th>6</th>
          <td>Bristlecone India Limited\n3.8\n(274 Reviews)</td>
          <td>4.1</td>
          <td>10d ago</td>
        </tr>
        <tr>
          <th>7</th>
          <td>Zyoin\n4.1\n(76 Reviews)</td>
          <td>3.6</td>
          <td>via naukri.com</td>
        </tr>
        <tr>
          <th>8</th>
          <td>Newgen Software Technologies Ltd.\n3.6\n(513 R...</td>
          <td>3.7</td>
          <td>1mon ago</td>
        </tr>
        <tr>
          <th>9</th>
          <td>Ashkom Media India Private Limited\n3.7\n(22 R...</td>
          <td>4.2</td>
          <td>via naukri.com</td>
        </tr>
      </tbody>
    </table>
    </div>



