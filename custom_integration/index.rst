Custom Integration REST Web Service Guidelines
===============================================
This document provides the necessary guidelines and few examples for creating a simple REST Web Service for a custom integration.

The examples given below assume that you have provided *https://your-domain.com* as the *Base URL* in custom integration configuration.

**\* Important: make sure you always use SSL on your domain**

User Authentication
~~~~~~~~~~~~~~~~~~~
You must use HTTP Basic Authentication for authenticating a user. The authentication credentials are the *Basic Auth Username* and *Basic Auth Password* values you provided in your custom integration configuration.

Endpoint
~~~~~~~~
You must implement the below endpoint which expects the below *required paramerters*.

GET */customers*

Finds the customer with given parameters.

**Required parameters**

+-------+--------+---------------------+
| name  | type   | description         |
+=======+========+=====================+
| email | string |  customer's email   |
+-------+--------+---------------------+
| phone | string |  customer's phone   |
+-------+--------+---------------------+


Response
~~~~~~~~~
You must return a *"Content-Type: application/json"* response with json data in the below format. You can use the *"custom_attributes"* field in the json response to specify any extra information about your customers.

::

    {
       "id": 1,
       "name": "John Watson",
       "email": "john@gmail.com",
       "phone": "123456",
       "country": "Spain",
       "city": "Madrid",
       "postal_code" : "28032",
       "address": "Baker Street, London. UK",
       "custom_attributes": [
             {"field_1": {"label": "some label", "value": "some value" }},
             {"field_2": {"label": "some label", "value": "some value" }},
             {"orders": {
                    "label": "Orders",
                    "value": {
                        "header": ["Order id", "description"],
                        "items": [
                            {"order_id": 1, "description": "product A"},
                            {"order_id": 2, "description": "product B"}
                        ]
                    }
                }
            }
       ]
    }


Examples
~~~~~~~~
* A php example can be found here_.

.. _here: https://github.com/zentio/custom-integration-rest-example/blob/master/README.md
