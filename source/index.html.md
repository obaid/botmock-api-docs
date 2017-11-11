---
title: Botmock API (Early Preview) Reference

language_tabs:
  - shell

toc_footers:
  - <a href='https://botmock.com/settings#/api'>Sign Up for a Developer Key</a>

includes:
  - errors

search: false
---

# Introduction

Welcome to Botmock API (early preview). You can use our API to access your Botmock projects and get details like messages payload, boards etc.

Please note that this *early preview* of our API. In coming months we will be updating our API to provide more robust information. For specific requests please email at [support@botmock.com](mailto:support@botmock.com).

# Overview

In Botmock everyone must belong to a team. Each team can have multiple projects under it and each project can be of one of two types:

- Conversation **Flow**
- Conversation **Mock**

## Conversation Flows

As the name suggests, conversation flows represent an entire conversation tree where each node can have multiple outgoing connections. Each node is called a **message**. Messages can be of different types. See [message types](#message-types) for more details.

## Conversation Mocks

Another way to visualize a single conversation path is to build a conversation mock. This type of project has multiple __boards__ that represent a conversation screen based on the [project type](#project-types). In a mock project, a user can create multiple boards but each board can only have one chain of linked messages. In other words, each message can only have *one* previous and *one* next possible message.

## Project Types

## Message Types

### Facebook Messenger
Message Type | Key | Description
-------------- | -------------- | --------------
User Reply | user_reply | Represents an input from a user
Text | text | Represents what your bot says to the user
Image | image | Represents an image template. Can be shown as a user input
Typing | typing_indicator | Shows typing bubble
Button | button | Represents the button template
Quick Replies | quick_replies | Represents the quick replies template
Generic | generic | Represents the generic card template. Turns into **carousel** if multiple cards are added
List | list | Represents the list template
Location | location | Represents the location template
Webview | webview | Represents the webview template
Receipt | receipt | Represents the receipt template

### Amazon Alexa 

Message Type | Key | Description
-------------- | -------------- | --------------
User Reply | user_reply | Represents an input from a user
Text | text | Represents what your bot says to the user

### Actions on Google

Message Type | Key | Description
-------------- | -------------- | --------------
User Reply | user_reply | Represents an input from a user
Text | text | Represents what your bot says to the user
Suggestion Chips | suggestion_chips | Represents the suggestion chips template
Card | card | Represents the card template
Carousel | carousel | Represents the carousel template
List | list | Represents the list template


# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.botmock.com/api/teams"
  -H "Authorization: Bearer YOUR-API-TOKEN"
```

> Make sure to replace `YOUR-API-TOKEN` with your API token.

Botmock uses API tokens to grant access to the API.  You can register a new Botmock API token at our [account settings](https://botmock.com/settings#/api). Please note that tokens are only shown once and are as important as your account login details.

Botmock expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer YOUR-API-TOKEN`

<aside class="notice">
You must replace <code>YOUR-API-TOKEN</code> with your personal API token.
</aside>

# Teams

## Get All Teams

> To get all teams, use this code:

```shell
curl "https://api.botmock.com/api/teams"
  -H "Authorization: YOUR-API-TOKEN"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 38881,
        "name": "First Team",
        "photo": "https://www.gravatar.com/avatar/00f062fb089de61b9a7e8033bc40109a.jpg?s=200&d=identicon",
        "created_at": {
            "date": "2017-01-10 20:45:21.000000",
            "timezone_type": 3,
            "timezone": "UTC"
        }
    },
    {
        "id": 133244,
        "name": "Second team",
        "photo": "https://www.gravatar.com/avatar/1c5a10ff164629b4da3be8ef5f7fe18d.jpg?s=200&d=identicon",
        "created_at": {
            "date": "2017-07-07 19:22:50.000000",
            "timezone_type": 3,
            "timezone": "UTC"
        }
    },
    {
        "id": 183331,
        "name": "Third Team",
        "photo": "https://www.gravatar.com/avatar/7c507a4e30c13b100a7175f494647e83.jpg?s=200&d=identicon",
        "created_at": {
            "date": "2017-08-12 03:38:19.000000",
            "timezone_type": 3,
            "timezone": "UTC"
        }
    }
]
```

This endpoint retrieves all teams.

Response:

Attribute  |  Type  |  Description
----------  | ---------------- | -------------
id          | int | a unique id that represents this team
name        | string | name of the team
photo       | url | URL representing the image for the team
created_at  | object | date this team was created

### HTTP Request

`GET https://api.botmock.com/api/teams`



## Get a Specific Team

```shell
curl "https://api.botmock.com/api/teams/38881"
  -H "Authorization: YOUR-API-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
    "id": 38881,
    "name": "First Team",
    "photo": "https://www.gravatar.com/avatar/00f062fb089de61b9a7e8033bc40109a.jpg?s=200&d=identicon",
    "created_at": {
        "date": "2017-01-10 20:45:21.000000",
        "timezone_type": 3,
        "timezone": "UTC"
    }
}
```

This endpoint retrieves a specific team.

### HTTP Request

`GET https://api.botmock.com/teams/<TEAM-ID>`

### URL Parameters

Parameter | Description
--------- | -----------
TEAM-ID | The ID of the team to retrieve


# Projects

## Get All Projects

```shell
curl "https://api.botmock.com/api/teams/38881/projects"
  -H "Authorization: YOUR-API-TOKEN"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": "8063ca00-8877-11e7-a797-4f95526152d6",
        "name": "Google Actions Sample Project",
        "created_at": "2017-08-24 02:54:09",
        "updated_at": "2017-11-08 05:21:23",
        "type": "flow",
        "platform": "google-actions"
    },
    {
        "id": "1935e1c0-4638-11e7-a11b-cd5cada6e9c1",
        "name": "Facebook Conversation Flow",
        "created_at": "2017-05-31 19:34:01",
        "updated_at": "2017-11-08 05:19:11",
        "type": "flow",
        "platform": "facebook"
    },
    {
        "id": "06855dd0-3923-11e7-be67-1174531b58f7",
        "name": "Facebook Mock Project",
        "created_at": "2017-05-15 04:00:25",
        "updated_at": "2017-07-19 21:20:57",
        "type": "mock",
        "platform": "facebook"
    }
]
```

This endpoint retrieves all projects for a team.

### HTTP Request

`GET https://api.botmock.com/api/teams/<TEAM-ID>/projects`

### URL Parameters

Parameter | Description
--------- | -----------
TEAM-ID | The ID of the team to retrieve

## Get Specific Project

```shell
curl "https://api.botmock.com/api/teams/38881/projects/16f1c520-05c6-11e7-bc31-5554df9b496b"
  -H "Authorization: YOUR-API-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
    "id": "16f1c520-05c6-11e7-bc31-5554df9b496b",
    "name": "Kindly",
    "created_at": "2017-03-10 19:16:40",
    "updated_at": "2017-09-15 14:15:59",
    "type": "mock",
    "platform": "facebook"
}
```

This endpoint retrieves a single project for a team.

### HTTP Request

`GET https://api.botmock.com/api/teams/<TEAM-ID>/projects/<PROJECT-ID>`

### URL Parameters

Parameter | Description
--------- | -----------
TEAM-ID | The ID of the team to retrieve
PROJECT-ID | The ID of the project you want to retreive

## Get Project Boards

```shell
curl "https://api.botmock.com/api/teams/38881/projects/16f1c520-05c6-11e7-bc31-5554df9b496b/boards"
  -H "Authorization: YOUR-API-TOKEN"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": "16f212e0-05c6-11e7-a955-8d23fe368669",
        "created_at": "2017-03-10 19:16:40",
        "updated_at": "2017-05-25 20:28:13",
        "name": "Your Charity",
        "is_private": false,
        "avatar": "",
        "project_id": "16f1c520-05c6-11e7-bc31-5554df9b496b"
    },
    {
        "id": "5b810a20-3505-11e7-a0b2-2bc799a132cf",
        "created_at": "2017-05-09 22:17:58",
        "updated_at": "2017-05-09 22:17:58",
        "name": "Untitled",
        "is_private": false,
        "avatar": "",
        "project_id": "16f1c520-05c6-11e7-bc31-5554df9b496b"
    },
    {
        "id": "618bdc40-9a20-11e7-b4a3-95d634181268",
        "created_at": "2017-09-15 14:15:52",
        "updated_at": "2017-09-15 14:15:59",
        "name": "Your Charity",
        "is_private": false,
        "avatar": "",
        "project_id": "16f1c520-05c6-11e7-bc31-5554df9b496b"
    }
]
```

This endpoint retrieves all boards for a single project. Boards are similar to canvas, as they are what contains all your messages. For projects for `flow` type, there is only 1 board at any given time. For `mock` projects, you can have multiple boards.

### HTTP Request

`GET https://api.botmock.com/api/teams/<TEAM-ID>/projects/<PROJECT-ID>/boards`

### URL Parameters

Parameter | Description
--------- | -----------
TEAM-ID | The ID of the team to retrieve
PROJECT-ID | The ID of the project you want to retreive

## Get Specific Board

```shell
curl "https://api.botmock.com/api/teams/38881/projects/16f1c520-05c6-11e7-bc31-5554df9b496b/boards/16f212e0-05c6-11e7-a955-8d23fe368669"
  -H "Authorization: YOUR-API-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
    "board": {
        "root_messages": [
            "6af54577-593a-436a-866f-11be95c55b64"
        ],
        "messages": [
            {
                "message_id": "6af54577-593a-436a-866f-11be95c55b64",
                "message_type": "user_reply",
                "next_message_ids": [
                    "c728f3be-218f-40d0-bc83-d92bfca96022"
                ],
                "previous_message_ids": [],
                "is_root": true,
                "payload": {
                    "text": "Search Flights"
                }
            },
            {
                "message_id": "c728f3be-218f-40d0-bc83-d92bfca96022",
                "message_type": "text",
                "next_message_ids": [
                    "e18708cb-2dcf-4545-8c14-7f8c39a7f9f0"
                ],
                "previous_message_ids": [
                    "6af54577-593a-436a-866f-11be95c55b64"
                ],
                "is_root": false,
                "payload": {
                    "text": "Sweet! I love finding people the least agonizing flights! Say something like \"non-stop flight on United from SFO to YOW 10/02 to 10/09\""
                }
            },
            ...
        ]
    },
    "created_at": {
        "date": "2017-09-20 23:47:47.000000",
        "timezone_type": 3,
        "timezone": "UTC"
    },
    "updated_at": {
        "date": "2017-09-20 23:47:47.000000",
        "timezone_type": 3,
        "timezone": "UTC"
    }
}
```

This endpoint retrieves a specific board that you requests. Each board contains a `root_messages` property that is an array of `message ids` that act as a starting point (i.e. they have no connections coming into them) and a `messages` property that is an `Array` of `messages` that have the following attributes:

Attribute  |  Type  |  Description
----------  | ---------------- | -------------
message_id | string | a unique id that represents this message
message_type | string | type of message (see [Message Types](#message-types) for details)
next_message_ids | array | an array representing a list of possible messages that you can go to from here
previous_message_ids | array | an array representing a list of possible messages that lead to this message
is_root | boolean | a boolean is this a root message
payload | object | a data structure that represents the JSON representation of what the message looks like. *NOTE* this might not be a complete payload that you can send to the platform. 

### HTTP Request

`GET https://api.botmock.com/api/teams/<TEAM-ID>/projects/<PROJECT-ID>/boards/<BOARD-ID>`

### URL Parameters

Parameter | Description
--------- | -----------
TEAM-ID | The ID of the team to retrieve
PROJECT-ID | The ID of the project you want to retreive
BOARD-ID | The ID of the specific board you want to retreive

## Platform Payloads (Coming Soon)

In near future we will be giving you access to get platform ready JSON payload for any given message within the board. 
