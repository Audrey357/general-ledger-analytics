**getCOA**
----
  Returns an array of structured General Ledger Account available for this date in JSON format.
  
* **Version History:**

  TASS v52.5 - Method Added

* **Version:**

  3

* **Permission:**

  General Ledger > Accounts

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**

   `date [date dd/mm/yyyy]`
   
   **Optional:**

   `start_num [integer]` - `start_num` required if `flex_code` supplied

   `flex_code [string]` - `flex_code` required if `start_num` supplied

   **Conditional:**
  
   none

* **Success Response:**

    ```javascript
    {
        "accounts":[
            {
                "end_year_num":2099,
                "rpt7_code":"",
                "rpt6_desc":"",
                "rpt4_code":"",
                "rpt3_desc":"Accumulated Funds & Reserves",
                "assoc_acct_code":"",
                "end_period_num":12,
                "def_tax_code":"AC",
                "rpt5_desc":"",
                "type_ind":"E",
                "rpt8_code":"",
                "rpt2_desc":"Current",
                "acct_code":"04-1300-60-30",
                "group_code":"",
                "rpt1_code":1234,
                "rpt9_desc":"",
                "desc_text":"Stationery - Prep",
                "start_period_num":1,
                "rpt7_desc":"",
                "resp_e_mail":"",
                "rpt5_code":"",
                "rpt2_code":"03",
                "rpt8_desc":"",
                "start_year_num":2012,
                "analy_prompt_text":"",
                "rpt1_desc":"Code 1234",
                "rpt3_code":"NNN",
                "rpt4_desc":"",
                "rpt6_code":"",
                "rpt9_code":"",
                "assoc_acct_desc":"",
                "resp_name":""
            }
        ],
        "token":{
            "date":"04/10/2019",
            "flex_code":"04",
            "timestamp":"{ts '2020-06-10 09:09:43'}",
            "start_num":1
        }
    }
    ```

* **Error Response:**

    `start_num` not supplied when `flex_code` supplied
    ```javascript
    __invalid: {
      "start_num": "field is required"
    }
    ```

    `start_num` not a valid integer
    ```javascript
    __invalid: {
      "start_num": "Value is not a valid integer."
    }
    ```

    `start_num` not greater than 0
    ```javascript
    __invalid: {
      "start_num": "start_num must be greater than 0"
    }
    ```

    `flex_code` not supplied when `start_num` supplied
    ```javascript
    __invalid: {
      "flex_code": "field is required"
    }
    ```

    `date` not supplied
    ```javascript
    __invalid: {
      "date": "field is required"
    }
    ```
    
    `date` not a valid date
    ```javascript
    __invalid: {
      "date": "Value is not a valid date."
    }
    ```

    GL Period for `date` is not Set Up
    ```javascript
    __invalid: {
      "error": "GL Period for #pr_date# is not Set Up"
    }
    ```

    `date` not within the right range
    ```javascript
    __invalid: {
      "error": "Date 2018-01-01 is out of range. Date is <> CURRENT_DATE +/- 365 days"
    }
    ```
    
* **Sample Parameters:**

  ```javascript
    { 
      "date":"04/11/2019",
      "start_num":"1",
      "flex_code":"04"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getCOA&appcode=API22&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We1Gqx9%2Fzb%2BcbVFartivsDN%2FxGgAIIjtABAYfzYPqTCpLf3gb0nW3h%2FTrPFLMhAdNcVvHD0Gz4FkRj5jRAD1aAGQ
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getCOA">
       <input type="hidden" name="appcode" value="API22">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We1Gqx9/zb+cbVFartivsDN/xGgAIIjtABAYfzYPqTCpLf3gb0nW3h/TrPFLMhAdNcVvHD0Gz4FkRj5jRAD1aAGQ</textarea>
    </form>
  ```
