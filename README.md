![](https://github.com/filetrust/azure-product-test-automation/workflows/Upload%20Python%20Package/badge.svg)

# azure-product-test-automation
A small package for testing Glasswall azure product endpoints

## Getting Started

```cmd
pip install glasswall-azure-product-test-automation
```

### Prerequisites

* [Python >= 3.6](https://www.python.org/downloads/)

### Usage

```cmd
p43_test_automation --product "PRODUCT" --endpoint "ENDPOINT" --api_key "API_KEY"
```

### Arguments

| Argument        | Short | Necessity | Description |
| --------------- | :---: | :-------: | :- |
| --product       | -p    | Required  | *(str)* Name of a product corresponding to a directory in [p43_test_automation/integration_tests](https://github.com/filetrust/azure-product-test-automation/tree/master/p43_test_automation/integration_tests).<br>e.g. `"rebuild"` |
| --endpoint      | -e    | Required  | *(str)* API Gateway product endpoint url.<br> e.g. `"https://8oiyjy8w63.execute-api.us-west-2.amazonaws.com/Prod/api/Rebuild"` |
| --api_key       | -a    | Required  | *(str)* An security key that grants access to the endpoint specified as well as other Glasswall product endpoints, such as the presigned url generator.<br>e.g. `"a612ciXevo7FM9UKlkaj2D27s6u7Nieb6K2z9929d"` |
| --test_files    | -t    | Optional  | **This functionality is currently disabled.**<br>*(str)* A directory containing external files to perform basic status code tests on. Defaults to `p43_test_automation/data/files/external`  |
| --logging_level | -l    | Optional  | *(str)* The logging level of the Python logging module. Defaults to `INFO`. Valid values are: `NOTSET`,`DEBUG`,`INFO`,`WARNING`,`ERROR`,`CRITICAL` |

### Example run (2020/06/15)
<details>
<summary>Click to expand</summary>
    
```cmd
p43_test_automation --product "rebuild" --endpoint "***" --api_key "***"

INFO:glasswall:Setting up Test_rebuild_base64
test_post___bmp_32kb___returns_status_code_200_protected_file (test_rebuild_base64.Test_rebuild_base64)
1Test_File submit using base64 code & less than 6mb with valid x-api key is successful ... ok
test_post___bmp_32kb_invalid_api_key___returns_status_code_401 (test_rebuild_base64.Test_rebuild_base64)
3-Test_File submit using base64 code & less than 6mb with invalid x-api key is unsuccessful ... ok      
test_post___bmp_over_6mb___returns_status_code_413 (test_rebuild_base64.Test_rebuild_base64)
2-Test_Accurate error returned for a over 6mb file submit using base64 code with valid x-api key ... skipped '6 - 10mb edge case, results in status_code 500'
test_post___doc_embedded_images_12kb_content_management_policy_allow___returns_status_code_200_identical_file (test_rebuild_base64.Test_rebuild_base64)      
4-Test_The default cmp policy is applied to submitted file using base64 code ... ok
test_post___doc_embedded_images_12kb_content_management_policy_disallow___returns_status_code_200_disallowed_json (test_rebuild_base64.Test_rebuild_base64)
4-Test_The default cmp policy is applied to submitted file using base64 code ... ok
test_post___doc_embedded_images_12kb_content_management_policy_sanitise___returns_status_code_200_sanitised_file (test_rebuild_base64.Test_rebuild_base64)
4-Test_The default cmp policy is applied to submitted file using base64 code ... ok
test_post___external_files___returns_200_ok_for_all_files (test_rebuild_base64.Test_rebuild_base64) ... skipped ''
test_post___jpeg_corrupt_10kb___returns_status_code_422 (test_rebuild_base64.Test_rebuild_base64)
12-Test_upload of files with issues and or malware using base64 code with valid x-api key ... ok
test_post___txt_1kb___returns_status_code_422 (test_rebuild_base64.Test_rebuild_base64)
10-Test_unsupported file upload using base64 code & less than 6mb with valid x-api key is unsuccessful ... ok
test_post___xls_malware_macro_48kb___returns_status_code_200_sanitised_file (test_rebuild_base64.Test_rebuild_base64)
12-Test_upload of files with issues and or malware using base64 code with valid x-api key ... ok
INFO:glasswall:Setting up Test_rebuild_file
test_post___bmp_32kb___returns_status_code_200_protected_file (test_rebuild_file.Test_rebuild_file)
1Test_File submit using file endpoint & less than 6mb with valid x-api key is successful ... ok
test_post___bmp_32kb_invalid_api_key___returns_status_code_401 (test_rebuild_file.Test_rebuild_file)
3-Test_File submit using file endpoint & less than 6mb with invalid x-api key is unsuccessful ... ok
test_post___bmp_over_6mb___returns_status_code_413 (test_rebuild_file.Test_rebuild_file)
2-Test_Accurate error returned for a over 6mb file submit using file endpoint with valid x-api key ... skipped '6 - 10mb edge case, results in status_code 500'
test_post___doc_embedded_images_12kb_content_management_policy_allow___returns_status_code_200_identical_file (test_rebuild_file.Test_rebuild_file)
4-Test_The default cmp policy is applied to submitted file using file endpoint ... ok
test_post___doc_embedded_images_12kb_content_management_policy_disallow___returns_status_code_200_disallowed_json (test_rebuild_file.Test_rebuild_file)
4-Test_The default cmp policy is applied to submitted file using file endpoint ... ok
test_post___doc_embedded_images_12kb_content_management_policy_sanitise___returns_status_code_200_sanitised_file (test_rebuild_file.Test_rebuild_file)
4-Test_The default cmp policy is applied to submitted file using file endpoint ... ok
test_post___external_files___returns_200_ok_for_all_files (test_rebuild_file.Test_rebuild_file) ... skipped ''
test_post___jpeg_corrupt_10kb___returns_status_code_422 (test_rebuild_file.Test_rebuild_file)
12-Test_upload of files with issues and or malware using file endpoint with valid x-api key ... ok
test_post___txt_1kb___returns_status_code_422 (test_rebuild_file.Test_rebuild_file)
10-Test_unsupported file upload using file endpoint & less than 6mb with valid x-api key is unsuccessful ... ok
test_post___xls_malware_macro_48kb___returns_status_code_200_sanitised_file (test_rebuild_file.Test_rebuild_file)
12-Test_upload of files with issues and or malware using file endpoint with valid x-api key ... ok
INFO:glasswall:Setting up Test_rebuild_url
INFO:glasswall:Generating presigned urls...
INFO:glasswall:File uploaded to: customer-uploaded-files/249b4faf-23df-477a-9eaa-6344612e5bf6/15-06-2020 09:06:12/bmp_32kb.bmp
INFO:glasswall:File uploaded to: customer-uploaded-files/1103a0d3-0cc3-477d-81d3-7c804968cb14/15-06-2020 09:06:14/bmp_5.93mb.bmp
INFO:glasswall:File uploaded to: customer-uploaded-files/1302beef-d463-4c42-95eb-da2d6b3e88e2/15-06-2020 09:06:15/bmp_6.12mb.bmp
INFO:glasswall:File uploaded to: customer-uploaded-files/caf68172-177a-4a1c-98d1-955e2bbcf66a/15-06-2020 09:06:16/txt_1kb.txt
INFO:glasswall:File uploaded to: customer-uploaded-files/8c5b8fda-5a83-4d56-991e-654c2871a091/15-06-2020 09:06:17/doc_embedded_images_12kb.docx
INFO:glasswall:File uploaded to: customer-uploaded-files/2482ee0a-7862-4bad-bb3c-2d16bb36d220/15-06-2020 09:06:17/CalcTest.xls
test_post___bmp_32kb___returns_status_code_200_protected_file (test_rebuild_url.Test_rebuild_url)
5-Test_File submit using pre-signed url with valid x-api key is successful ... ok
test_post___bmp_32kb_invalid_api_key___returns_status_code_401 (test_rebuild_url.Test_rebuild_url)
6b-Test_File submit using pre-signed url with invalid x-api key is unsuccessful ... ok
test_post___bmp_32kb_no_api_key___returns_status_code_401 (test_rebuild_url.Test_rebuild_url)
6a-Test_File submit using pre-signed url with no x-api key is unsuccessful ... ok
test_post___doc_embedded_images_12kb_content_management_policy_allow___returns_status_code_200_identical_file (test_rebuild_url.Test_rebuild_url)
7a-Test_The default cmp policy is applied to submitted file using pre-signed url ... ok
test_post___doc_embedded_images_12kb_content_management_policy_disallow___returns_status_code_200_disallowed_json (test_rebuild_url.Test_rebuild_url)
7c-Test_The default cmp policy is applied to submitted file using pre-signed url ... ok
test_post___doc_embedded_images_12kb_content_management_policy_sanitise___returns_status_code_200_sanitised_file (test_rebuild_url.Test_rebuild_url)
7b-Test_The default cmp policy is applied to submitted file using pre-signed url ... ok
test_post___jpeg_corrupt_10kb___returns_status_code_422 (test_rebuild_url.Test_rebuild_url)
11b-Test_upload of files with issues and or malware using presigned with valid x-api key ... skipped 'waiting for update to the presigned url lambda to allow files with no extension'
test_post___txt_1kb___returns_status_code_422 (test_rebuild_url.Test_rebuild_url)
9-Test_unsupported file upload using pre-signed url with valid x-api key is unsuccessful ... ok
test_post___xls_malware_macro_48kb___returns_status_code_200_sanitised_file (test_rebuild_url.Test_rebuild_url)
11a-Test_upload of files with issues and or malware using presigned with valid x-api key ... ok

----------------------------------------------------------------------
Ran 29 tests in 17.751s

OK (skipped=5)
```
</details>

## Built With

* [Python 3.8.1 64-bit](https://www.python.org/downloads/release/python-381/)
