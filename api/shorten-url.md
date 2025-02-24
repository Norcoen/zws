---
description: Shorten a long URL
---

# Shorten URL

{% api-method method="get" host="https://zws.im/api" path="/shortenURL" %}
{% api-method-summary %}
Shorten URL
{% endapi-method-summary %}

{% api-method-description %}
This endpoint returns the short ID corresponding to the specified long URL.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="url" type="string" required=true %}
The long URL to shorten. Must not contain the URL shortener's hostname or exceed 500 characters in length.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The URL has already been shortened and was fetched from the database.
{% endapi-method-response-example-description %}

```javascript
{
    "short": "Short ID"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}
The URL was shortened and added to the database.
{% endapi-method-response-example-description %}

```javascript
{
    "short": "Short ID"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The URL wasn't specified, wasn't string type, was invalid, or contained the URL shortener's hostname.
{% endapi-method-response-example-description %}

{% code-tabs %}
{% code-tabs-item title="URL was not specified" %}
```javascript
{
    "error": "You must specify a URL"
}
```
{% endcode-tabs-item %}

{% code-tabs-item title="URL is invalid" %}
```javascript
{
    "error": "Not a valid URL"
}
```
{% endcode-tabs-item %}

{% code-tabs-item title="URL contains hostname" %}
```javascript
{
    "error": "Shortening a URL containing the URL shortener's hostname is disallowed"
}
```
{% endcode-tabs-item %}

{% code-tabs-item title="invalid URL type" %}
```javascript
{
    "error": "URL must be string type"
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endapi-method-response-example %}

{% api-method-response-example httpCode=413 %}
{% api-method-response-example-description %}
The URL exceeded 500 characters.
{% endapi-method-response-example-description %}

```javascript
{
    "error": "URL can not exceed 500 characters"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



