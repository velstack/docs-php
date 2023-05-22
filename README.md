<p align="center"><a href="https://mnotify.com" target="_blank"><img src="https://dashboard.velstack.com/build/images/velstack/logo-white.png" width="200" alt="  Logo"></a></p>

<p align="center">
<a href="https://github.com/sammyfort/mNotify-laravel"><img src="https://img.shields.io/badge/%3C%2F%3E-cURL%20-blue" alt="Build Status"></a>
<a href="https://packagist.org/packages/velstack/mnotify"><img src="https://img.shields.io/github/license/sammyfort/mNotify-laravel"></a>

 

</p>
 

## Velstack [PHP] documenation.

## Introduction
Velstack APIs was made with REST and uses http verbs such as `'GET'`, `'POST'`, `'PATCH/PUT'`, `'DELETE'`. Every request to our endpoints must be restful.

Base url
```bash
  https://api.velstack.com
```

## Authentication

Velstack uses API keys to `'authenticate'` requests. You can [register](https://dashboard.velstack.com/) or login to get your API key.
Eevery request made to this endpoint requires API key to the server as a GET parameter:.   

## Responses

All http responses are in json format that's every request to our endpoint must include a header of `'Accept:application/json'` .   

 
## Send Quick SMS

```php
<?php
  $url = "https://api.velstack.com/messaging/quick/sms";

  $data = [
    'sender' => "Velstack",
    'recipient' => "0205550368",
    'message' => 'The message content'
  ];

  $fields_string = http_build_query($data);

  //open connection
  $ch = curl_init();
  
  //set the url, number of POST vars, POST data
  curl_setopt($ch,CURLOPT_URL, $url);
  curl_setopt($ch,CURLOPT_POST, true);
  curl_setopt($ch,CURLOPT_POSTFIELDS, $fields_string);
  curl_setopt($ch, CURLOPT_HTTPHEADER, array(
    "Authorization: Bearer API_KEY",
    "Accept: application/json",
  ));
  
  //So that curl_exec returns the contents of the cURL; rather than echoing it
  curl_setopt($ch,CURLOPT_RETURNTRANSFER, true); 
  
  //execute post
  $result = curl_exec($ch);
  echo $result;
?>

```
 
 
 
 

#### `Response`
```json
{
    "status": true,
    "code": 200,
    "message": "Message sent successfully",
    "data": {
        "summary": {
            "message_id": "3934ac17-25e8-46cb-ac27-4963b78f87ee",
            "type": "API Quick SMS",
            "total_contacts": 1,
            "recipients": "0205550368",
            "credit_used": 1,
            "credit_left": "253.00"
        }
    }
}

```
 
 
  
## Send Group SMS

```shell
<?php
  $url = "https://api.velstack.com/messaging/group/sms";

  $data = [
    'sender' => "Velstack",
    'group_id' => "c9e5ed73-2580-4f1a-ad17-35ceedb1cbe7",
    'message' => 'The message content'
  ];

  $fields_string = http_build_query($data);

  //open connection
  $ch = curl_init();
  
  //set the url, number of POST vars, POST data
  curl_setopt($ch,CURLOPT_URL, $url);
  curl_setopt($ch,CURLOPT_POST, true);
  curl_setopt($ch,CURLOPT_POSTFIELDS, $fields_string);
  curl_setopt($ch, CURLOPT_HTTPHEADER, array(
    "Authorization: Bearer API_KEY",
    "Accept: application/json",
  ));
  
  //So that curl_exec returns the contents of the cURL; rather than echoing it
  curl_setopt($ch,CURLOPT_RETURNTRANSFER, true); 
  
  //execute post
  $result = curl_exec($ch);
  echo $result;
?>

```
 
 
 
 

#### `Response`
```json
{
    "status": true,
    "code": 200,
    "message": "Message sent Successfully",
    "data": {
        "summary": {
            "message_id": "fa1f2a05-a7c1-4d05-b373-7b9731cf00a5",
            "type": "API Group SMS",
            "total_contacts": 2,
            "recipients": "020555XXX,0248297302",
            "credit_used": 2,
            "credit_left": "53.00"
        }
    }
}

```
  
<p align="center">
  Sammy Fort ©2023. Powered by <a href="https://velstack.com/">Velstack</a>
</p>
