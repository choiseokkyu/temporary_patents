# Tutorial of Google BigQuery with Patents Public Data

## Purpose
- 우리가 이 튜토리얼을 만들어서 공개하는 이유

### What is BigQuery?
- Google BigQuery is an enterprise data warehouse that solves this problem by enabling very fast SQL queries using the processing power of Google's infrastructure. Taking advantage of big query, we can easily use patents-public-data.

### What is Patents-Public-Data?
- Patents-Public-Data is publicly accessible, connected database tables for empirical analysis of the international patent system.
----------------------------------------------------
## How To Use(Web version)  
1. Create project in your google cloud platform account.
<p></p>
2. If you use big query on web UI, you have to add ‘#standardSQL’ at the top of query in Big Query or Uncheck SQL Dialect’s <Use Legacy SQL> checkbox.  
<p></p>
<img src="https://user-images.githubusercontent.com/23125324/46584804-e9c03280-caa2-11e8-83f4-20e1f54e99ab.PNG">
<img src="https://user-images.githubusercontent.com/23125324/46584820-170ce080-caa3-11e8-8b00-5a88daf8c558.PNG">
<p></P>
3. Big query data is nested Structure(Project > Dataset > table).
You can query data like
```
`Project_name.Dataset_name.table_name`
```
There is 19 datasets in Project ‘Patents-public-data’.
```
#standardSQL
SELECT * FROM `patents-public-data.cpc.definitions`;
```
[Big query python API](https://googleapis.github.io/google-cloud-python/latest/bigquery/index.html)  
추후 자세한 사용법 작성  
<p></p>
4. If queried data is not very large, you can save it.  
<p></p>
5. But data is too large, you have to create your own dataset and save as table.  
<p></p>
<img src="https://user-images.githubusercontent.com/23125324/46584832-25f39300-caa3-11e8-9c23-dfea8029f061.png">
<img src="https://user-images.githubusercontent.com/23125324/46584835-2d1aa100-caa3-11e8-8b9b-29fd76fa5f3e.PNG">


----------------------------------------------------
## Datasets
#### 1) CPC : Cooperative Patents Classification
- Definitions of the Cooperative Patent Classification system for classifying patent documents.

#### 2) dSEP : disclosed Standard Essential Patents
- A full overview of disclosed intellectual property rights at setting organizations worldwide.

### Examples

--> 테이블 내에 어떤 컬럼이 있는지, 그 데이터는 어떻게 생겼는지 테이블 형태, 이미지로 표현해야 하는가, 대부분의 테이블들은 컬럼에 대한 설명이 없다.   
--> 쿼리하는 법은 SQL방식과 동일하므로 Query 방법을 쓰기보다는 컬럼에 대한 설명들을 기반으로 의미있는 Feature들이 무엇인지 찾는다.  
--> 의미있는 Feature들을 기반으로 Join 같은 데이터 조작을 통해 table을 만든다.  
--> dataset들 중에 table이 한개인 것도 있고 여러개인 것도 있다. 그러므로 table과 table 사이의 관계, dataset들과의 연관성을 찾는다.  
--> null 값의 개수 같은 통계정보가 필요할까? 기본적으로 table size(용량), row의 개수같은 정보는 표기되어 있다.
