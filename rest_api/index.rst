========================
Zent.IO REST Service API
========================
This document provides the necessary guidelines and few examples for using the Service API.

Customers End Points
====================

Search Customers
----------------
The endpoint returns customers for the parameters specified. 

**Example**

+----------------------------------------------------------------------------------------------------------+
| GET *https://{subdomain}.zent.io/api/v1/customer/search?apikey={api_key}&name=jhon&page=1&page_size=10*  |
+----------------------------------------------------------------------------------------------------------+

**Parameters**

 =========  ========  ======================================================================================================
 Name       Required  Description
 =========  ========  ======================================================================================================
 name          yes    The customer's name.
 email         no     The customer's email.  
 phone         no     The customer's phone. 
 page          yes    The result's page. 
 page_size     no     The result's page size. Defaults to 10.   
 sorting       no     The result's sorting. Possible values are *last_created* and *last_updated*. Defaults to last_updated.   
 =========  ========  ======================================================================================================

**Response Sample**

::

    [
        {
            "id":"54652afd3896ede40a000000",
            "name":"Jhon",
            "surname":"Doe",
            "email":"jhon@gmail.com",
            "phone":"88888888888",
            "createdAt":"2014-11-13T17:04:45-05:00",
            "updatedAt":"2014-11-13T17:23:46-05:00",
            "customAttributes":[]
        },
        {
            "id":"54652f6f3896ed8018000000",
            "name":"Marissa",
            "surname":"Mayer",
            "email":"marissa@gmail.com",
            "phone":"9999999999999",
            "createdAt":"2014-11-13T17:23:43-05:00",
            "updatedAt":"2014-11-13T17:23:43-05:00",
            "customAttributes":[]
        },
        ...
    ]



Get Customer
------------
The endpoint returns a customer for the parameter specified.

**Example**

+-------------------------------------------------------------------------------------------------------+
| GET *https://{subdomain}.zent.io/api/v1/customer?apikey={api_key}&customer=54652afd3896ede40a000000*  |
+-------------------------------------------------------------------------------------------------------+

**Parameters**

 =========  ========  ======================================================================================================
 Name       Required  Description
 =========  ========  ======================================================================================================
 customer      yes    The customer's id or the customer's email.
 =========  ========  ======================================================================================================

**Response Sample**

::

    {
        "id":"54652afd3896ede40a000000",
        "name":"Jhon",
        "surname":"Doe",
        "email":"jhon@gmail.com",
        "phone":"88888888888",
        "createdAt":"2014-11-13T17:04:45-05:00",
        "updatedAt":"2014-11-13T17:23:46-05:00",
        "customAttributes":[]
    }



Get Customer Stories
--------------------
The endpoint returns the customer stories for the parameters specified.

**Example**

+----------------------------------------------------------------------------------------------------------+
| GET *https://{subdomain}.zent.io/api/v1/customer/search?apikey={api_key}&name=jhon&page=1&page_size=10*  |
+----------------------------------------------------------------------------------------------------------+

**Parameters**

 =========  ========  ======================================================================================================
 Name       Required  Description
 =========  ========  ======================================================================================================
 customer      yes    The customer's id or the customer's email.
 page          yes    The result's page.
 page_size     no     The result's page size. Defaults to 10.
 sorting       no     The result's sorting. Possible values are *last_created* and *last_updated*. Defaults to last_updated.
 =========  ========  ======================================================================================================

**Response Sample**

::

    [
        {
            "id":"546466313896ed7c21000000",
            "state":0,
            "subject":"My story subject",
            "createdAt":"2014-11-13T03:05:05-05:00"
        },
        {
            "id":"54646c653896ed1023000000",
            "state":0,
            "subject":"My story subject",
            "createdAt":"2014-11-13T03:31:33-05:00"
        },
        ...
    ]



Create Customer
---------------
The endpoint creates a customer for the parameters specified.

**Example**

+--------------------------------------------------------------------------+
| POST *https://{subdomain}.zent.io/api/v1/customer/new?apikey={api_key}*  |
+--------------------------------------------------------------------------+

**Parameters**

 =========  ========  ======================================================================================================
 Name       Required  Description
 =========  ========  ======================================================================================================
 name          yes    The customer's name.
 email         yes    The customer's email.  
 phone         yes    The customer's phone. 
 address       yes    The customer's address. 
 tags          no     The customer's tags.
 =========  ========  ======================================================================================================

**Response Sample**

::

    {
        "id":"546581583896ed8813000002"
    }



Update Customer
---------------
The endpoint updates a customer with the parameters specified.

**Example**

+-----------------------------------------------------------------------------+
| POST *https://{subdomain}.zent.io/api/v1/customer/update?apikey={api_key}*  |
+-----------------------------------------------------------------------------+

**Parameters**

 =========  ========  ======================================================================================================
 Name       Required  Description
 =========  ========  ======================================================================================================
 customer      yes    The customer's id or the customer's email.
 name          yes    The customer's name.
 email         yes    The customer's email.  
 phone         yes    The customer's phone. 
 address       yes    The customer's address. 
 tags          no     The customer's tags.
 =========  ========  ======================================================================================================

**Response Sample**

::

    {
        "id":"546581583896ed8813000002"
    }




Statistics End Points
=====================

Get Chat Statistics
-------------------
The endpoint returns chat statistics for the parameters specified. 

**Example**

+---------------------------------------------------------------------------------------------------------------------+
| GET *https://{subdomain}.zent.io/api/v1/statistic/chat/{section}?apikey={api_key}&start=2014-09-16&end=2014-09-20*  |
+---------------------------------------------------------------------------------------------------------------------+

**Parameters**

 =========  ========  ==================================================================================================================
 Name       Required  Description
 =========  ========  ==================================================================================================================
 section       yes    The section for the query. Possible values are *general*, *performance*, *quality*, *service_level* and *reviews*. 
 start         yes    The start date for the query. It must be a ISO 8601 date. For example: 2014-09-16.
 end           yes    The end date for the query. It must be a ISO 8601 date. For example: 2014-09-20.
 user          no     The user's id or email.
 =========  ========  ==================================================================================================================

**Response Sample**

::

    [
        {
            "label":"CHAT_AVERAGE_DURATION",
            "day":"2014-09-16",
            "value":329,
            "user":
            {
                "id":"5459b0ce3896ed9820000078",
                "name":"Isabella",
            }
        },
        {
            "label":"CHAT_AVERAGE_DURATION",
            "day":"2014-09-16",
            "value":257,
            "user":
            {
                "id":"5459b0ce3896ed9820000079",
                "name":"Jacob",
            }
        },
        ...
    ]



Get Email Statistics
--------------------
The endpoint returns email statistics for the parameters specified. 

**Example**

+---------------------------------------------------------------------------------------------------------------------+
| GET *https://{subdomain}.zent.io/api/v1/statistic/email/{section}?apikey={api_key}&start=2014-09-16&end=2014-09-20*  |
+---------------------------------------------------------------------------------------------------------------------+

**Parameters**

 =========  ========  ==================================================================================================================
 Name       Required  Description
 =========  ========  ==================================================================================================================
 section       yes    The section for the query. Possible values are *general*, *quality*, *service_level* and *reviews*. 
 start         yes    The start date for the query. It must be a ISO 8601 date. For example: 2014-09-16.
 end           yes    The end date for the query. It must be a ISO 8601 date. For example: 2014-09-20.
 user          no     The user's id or email.
 =========  ========  ==================================================================================================================

**Response Sample**

::

    [
        {
            "label":"EMAIL_NUMBER",
            "day":"2014-09-16",
            "value":107,
            "user":
            {
                "id":"5459b0ce3896ed9820000078",
                "name":"Isabella",
            }
        },
        {
            "label":"EMAIL_NUMBER",
            "day":"2014-09-16",
            "value":219,
            "user":
            {
                "id":"5459b0ce3896ed9820000079",
                "name":"Jacob",
            }
        },
        ...
    ]



Get Voice Statistics
--------------------
The endpoint returns voice statistics for the parameters specified. 

**Example**

+----------------------------------------------------------------------------------------------------------------------+
| GET *https://{subdomain}.zent.io/api/v1/statistic/voice/{section}?apikey={api_key}&start=2014-09-16&end=2014-09-20*  |
+----------------------------------------------------------------------------------------------------------------------+

**Parameters**

 =========  ========  ==================================================================================================================
 Name       Required  Description
 =========  ========  ==================================================================================================================
 section       yes    The section for the query. Possible values are *general*, *performance*, *quality*, *service_level* and *reviews*. 
 start         yes    The start date for the query. It must be a ISO 8601 date. For example: 2014-09-16.
 end           yes    The end date for the query. It must be a ISO 8601 date. For example: 2014-09-20.
 user          no     The user's id or email.
 =========  ========  ==================================================================================================================

**Response Sample**

::

    [
        {
            "label":"VOICE_AVERAGE_DURATION",
            "day":"2014-09-16",
            "value":501,
            "user":
            {
                "id":"5459b0ce3896ed9820000078",
                "name":"Isabella",
            }
        },
        {
            "label":"VOICE_AVERAGE_DURATION",
            "day":"2014-09-16",
            "value":342,
            "user":
            {
                "id":"5459b0ce3896ed9820000079",
                "name":"Jacob",
            }
        },
        ...
    ]




Stories End Points
==================

Search Stories
--------------
The endpoint returns stories for the parameters specified. 

**Example**

+-----------------------------------------------------------------------------------------------------------+
| GET *https://{subdomain}.zent.io/api/v1/story/search?apikey={api_key}&query=subject&page=1&page_size=10*  |
+-----------------------------------------------------------------------------------------------------------+

**Parameters**

 =========  ========  ======================================================================================================
 Name       Required  Description
 =========  ========  ======================================================================================================
 query         yes    The story's subject.
 page          yes    The result's page. 
 page_size     no     The result's page size. Defaults to 10.   
 =========  ========  ======================================================================================================

**Response Sample**

::

    [
        {
            "id":"546466313896ed7c21000000",
            "state":0,
            "subject":"My story subject",
            "createdAt":"2014-11-13T03:05:05-05:00"
        },
        {
            "id":"54646c653896ed1023000000",
            "state":0,
            "subject":"My story subject",
            "createdAt":"2014-11-13T03:31:33-05:00"
        },
        ...
    ]



Get Story
---------
The endpoint returns a story for the parameter specified.

**Example**

+-------------------------------------------------------------------------------------------------+
| GET *https://{subdomain}.zent.io/api/v1/story?apikey={api_key}&story=546466313896ed7c21000000*  |
+-------------------------------------------------------------------------------------------------+

**Parameters**

 =========  ========  ======================================================================================================
 Name       Required  Description
 =========  ========  ======================================================================================================
 story         yes    The story's id.
 =========  ========  ======================================================================================================

**Response Sample**

::

    {
        "id":"546466313896ed7c21000000",
        "state":0,
        "subject":"My story subject",
        "createdAt":"2014-11-13T03:05:05-05:00"
    }



Create Story
------------
The endpoint creates a story for the parameters specified.

**Example**

+-----------------------------------------------------------------------+
| POST *https://{subdomain}.zent.io/api/v1/story/new?apikey={api_key}*  |
+-----------------------------------------------------------------------+

**Parameters**

 =========  ========  ======================================================================================================
 Name       Required  Description
 =========  ========  ======================================================================================================
 customer      yes    The story's customer id or email.
 user          yes    The story's user id or email.  
 subject       yes    The story's subject. 
 message       yes    The story's message. 
 note          yes    The story's note. 
 =========  ========  ======================================================================================================

**Response Sample**

::

    {
        "id":"546581583896ed8813000002"
    }



Add Story Note
--------------
The endpoint creates a note for a story based on the parameters specified.

**Example**

+----------------------------------------------------------------------------+
| POST *https://{subdomain}.zent.io/api/v1/story/add_note?apikey={api_key}*  |
+----------------------------------------------------------------------------+

**Parameters**

 =========  ========  ======================================================================================================
 Name       Required  Description
 =========  ========  ======================================================================================================
 story         yes    The story's id.
 content       yes    The note's content. 
 =========  ========  ======================================================================================================

**Response Sample**

::

    {
        "id":"54652f6f3896ed8018000000"
    }



Close Story
------------
The endpoint closes a story for the parameter specified.

**Example**

+----------------------------------------------------------------------------+
| POST *https://{subdomain}.zent.io/api/v1/story/close?apikey={api_key}*  |
+----------------------------------------------------------------------------+

**Parameters**

 =========  ========  ======================================================================================================
 Name       Required  Description
 =========  ========  ======================================================================================================
 story         yes    The story's id.
 =========  ========  ======================================================================================================

**Response Sample**

::

    {
        "id":"546581583896ed8813000002"
    }



Reassign Story
--------------
The endpoint reassigns a story to another user for the parameters specified.

**Example**

+----------------------------------------------------------------------------+
| POST *https://{subdomain}.zent.io/api/v1/story/reassign?apikey={api_key}*  |
+----------------------------------------------------------------------------+

**Parameters**

 =========  ========  ======================================================================================================
 Name       Required  Description
 =========  ========  ======================================================================================================
 story         yes    The story's id.
 user          yes    The new story's user id or email.
 =========  ========  ======================================================================================================

**Response Sample**

::

    {
        "id":"546581583896ed8813000002"
    }




Streams End Points
==================

Get Streams
-----------
The endpoint returns streams for the parameters specified. 

**Example**

+---------------------------------------------------------------------------------------+
| GET *https://{subdomain}.zent.io/api/v1/stream?apikey={api_key}&page=1&page_size=10*  |
+---------------------------------------------------------------------------------------+

**Parameters**

 =========  ========  ======================================================================================================
 Name       Required  Description
 =========  ========  ======================================================================================================
 page          yes    The result's page. 
 page_size     no     The result's page size. Defaults to 10.   
 =========  ========  ======================================================================================================

**Response Sample**

::

    [
        {
            "id":"54652fd83896ed801800000a",
            "type":1,
            "message":"My stream message",
            "from":null,
            "createdAt":"2014-11-13T17:25:28-05:00",
            "user":
            {
                "id":"5459b0ce3896ed9820000078",
                "name":"Isabella"
            }
        },
        {
            "id":"54652fd43896ed8018000009",
            "type":1,
            "message":"My test stream message",
            "from":null,
            "createdAt":"2014-11-13T17:25:24-05:00",
            "user":
            {
                "id":"5459b0ce3896ed9820000078",
                "name":"Isabella"
            }
        },
        ...
    ]



Create Stream
-------------
The endpoint creates a stream for the parameters specified.

**Example**

+------------------------------------------------------------------------+
| POST *https://{subdomain}.zent.io/api/v1/stream/new?apikey={api_key}*  |
+------------------------------------------------------------------------+

**Parameters**

 =========  ========  ======================================================================================================
 Name       Required  Description
 =========  ========  ======================================================================================================
 user          yes    The stream's user id or email.  
 content       yes    The stream's content. 
 =========  ========  ======================================================================================================

**Response Sample**

::

    {
        "id":"546581583896ed8813000002"
    }



Reply Stream
-------------
The endpoint replies to a stream for the parameters specified.

**Example**

+--------------------------------------------------------------------------+
| POST *https://{subdomain}.zent.io/api/v1/stream/reply?apikey={api_key}*  |
+--------------------------------------------------------------------------+

**Parameters**

 ==========  ========  ======================================================================================================
 Name        Required  Description
 ==========  ========  ======================================================================================================
 user           yes    The stream's reply user id or email.
 message_id     yes    The stream's id to reply to.
 content        yes    The stream's reply content.
 ==========  ========  ======================================================================================================

**Response Sample**

::

    {
        "id":"546457503896ed5c20000001"
    }



