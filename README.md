# 1. SMS Service Sample Code - Java

## 개발환경
* 언어 : Java
* IDE : Eclipse
* External Library : json-simple-1.1.1.jar (JSON 라이브러리)


## 과제 수행 목표

### Sample Code 작성 및 REST API 호출 원리 파악
* Connection : HTTPURLConnection 및 JSON(PUT, POST에 한함) 활용
* Response : BufferedReader에 Connection 결과로 유입되는 데이터 추출

## Github Repository
https://github.com/ekb2011/SMS_SampleCode_Java

# 2. SMS Service Sample Code - Python

## 개발환경
* 언어 : Python
* IDE : Eclipse PyDev
* Python Ver : 3.6.8
* External Library : requests
```
$cd C:\Users\NHNEnt\AppData\Local\Programs\Python\Python36\Scripts
$pip install requests
```

## 과제 수행 목표

### Sample Code 작성 및 REST API 호출 원리 파악
* Connection & Call REST API- requests.post, requests.get, requests.put
* Response - requests.post, requests.get, requests.put의 response를 text로 출력

## Python REST API 호출 방법
* urllib, request 방법 두 가지가 있음
### requests의 장점

* JSON 디코더가 내장되어 있어 JSON 모듈을 따로 사용할 필요가 없음
* urllib 보다 간단함

## Github Repository

https://github.com/ekb2011/SMS_SampleCode_Python

# 3. SMS Service Sample Code - PHP

## 개발환경
* 언어 : PHP
* PHP Ver : 7.1.25
* IDE : Notepad++
* 실행환경 : 윈도우 상에서 Bitnami로 테스트


## REST API 호출 방식

### cURL



### Guzzle Framework 활용


## 과제 수행 목표

### Sample Code 작성 및 PHP REST API 호출 원리 파악
* Connection & Call REST API - cURL / Guzzle Framework
* Response - json

## cURL vs Guzzle

### 간편한 REST API 호출, Response Data 출력이 용이

* cURL GET 방식 호출 시

```php
//prepare REST API call
$ch=curl_init($url.$appKeys.$type.$query."&from=".$encoded_from."&to=".$encoded_to);
	
//put header with the REST API
curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
	
//call REST API and get response
$res = curl_exec($ch);
	
//print result
$header_size = curl_getinfo($ch, CURLINFO_HEADER_SIZE); //Total size of all headers received
$body = substr($res, $header_size);    
 
$body_json = json_decode($body, true);
print_r($body_json);
	
//close connection
curl_close($ch);
```
* Guzzle Framework 활용 GET 방식 호출 시

```php
//set REST API Client
$client=new GuzzleHttp\Client();
	
//call REST API
$response=$client->request('GET', $url.$appKeys.$type.$query."&from=".$encoded_from."&to=".$encoded_to, [
	'header'=>$headers
]);
	
//print result
print_r(json_encode(json_decode($response->getBody(), true)));
```
* cURL POST 방식 호출 시

```php
//prepare REST API call
$ch=curl_init($url.$appKeys.$type);
	
//put header with the REST API
curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($requestBody));
	
//call REST API and get response
$res = curl_exec($ch);
	
//print result
$header_size = curl_getinfo($ch, CURLINFO_HEADER_SIZE);
$body = substr($res, $header_size);    
 
$body_json = json_decode($body, true);
print_r($body_json);
	
//close connection
curl_close($ch);
```
* Guzzle Framework 활용 POST 방식 호출 시

```php
//set REST API Client
$client=new GuzzleHttp\Client();
	
//call REST API
$response=$client->request('POST', $url.$appKeys.$type, [	
	'header'=>$headers,
	'json'=>$requestBody
]);
	
//print result
print_r(json_encode(json_decode($response->getBody(), true)));
```

## Github Repository

https://github.com/ekb2011/SMS_SampleCode_PHP