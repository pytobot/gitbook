---
description: All the API's in one place
---

# API

{% api-method method="post" host="https://172.17.2.10" path="/api/Movement" %}
{% api-method-summary %}
Drive
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="ID" type="integer" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="Direction" type="string" required=true %}
Forwards, Backwards, Left or Right
{% endapi-method-parameter %}

{% api-method-parameter name="Distance" type="integer" required=false %}
The distance the pytobot has to drive 1-100
{% endapi-method-parameter %}

{% api-method-parameter name="Speed" type="integer" required=false %}
The speed the pytobot has to drive 1-10
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
No error, data has been added to API
{% endapi-method-response-example-description %}

```
{"error":false,"message":"Data added"}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Something went wrong
{% endapi-method-response-example-description %}

```
{ error: true, message: "Error adding data" }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



{% api-method method="post" host="https://172.17.2.10" path="/api/camera" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="ID" type="integer" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="Position" type="integer" required=true %}
Position of the camera in the pytobot
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
No error, data has been added to API
{% endapi-method-response-example-description %}

```
{"error":false,"message":"Data added"}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Something went wrong
{% endapi-method-response-example-description %}

```
{ error: true, message: "Error adding data" }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://172.17.2.10" path="/api/distanceSensor" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="ID" type="integer" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="distance" type="integer" required=true %}
Maximum distance the robot can be from the wall in front
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
No error, data has been added to API
{% endapi-method-response-example-description %}

```
{"error":false,"message":"Data added"}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Something went wrong
{% endapi-method-response-example-description %}

```
{ error: true, message: "Error adding data" }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}







