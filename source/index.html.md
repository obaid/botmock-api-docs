---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: false
---

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: Bearer YOUR-API-TOKEN"
```

> Make sure to replace `YOUR-API-TOKEN` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: YOUR-API-TOKEN`

<aside class="notice">
You must replace <code>YOUR-API-TOKEN</code> with your personal API key.
</aside>

# Teams

## Get All Teams

> To get all teams, use this code:

```shell
curl "http://example.com/api/teams"
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

### HTTP Request

`GET http://example.com/api/teams`


## Get a Specific Team

```shell
curl "http://example.com/api/teams/38881"
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

`GET http://example.com/teams/<TEAM-ID>`

### URL Parameters

Parameter | Description
--------- | -----------
TEAM-ID | The ID of the team to retrieve


# Projects

## Get All Projects

```shell
curl "http://example.com/api/teams/38881/projects"
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

`GET http://example.com/api/teams/<TEAM-ID>/projects`

### URL Parameters

Parameter | Description
--------- | -----------
TEAM-ID | The ID of the team to retrieve

## Get Specific Project

```shell
curl "http://example.com/api/teams/38881/projects/16f1c520-05c6-11e7-bc31-5554df9b496b"
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

`GET http://example.com/api/teams/<TEAM-ID>/projects/<PROJECT-ID>`

### URL Parameters

Parameter | Description
--------- | -----------
TEAM-ID | The ID of the team to retrieve
PROJECT-ID | The ID of the project you want to retreive

## Get Project Boards

```shell
curl "http://example.com/api/teams/38881/projects/16f1c520-05c6-11e7-bc31-5554df9b496b/boards"
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

`GET http://example.com/api/teams/<TEAM-ID>/projects/<PROJECT-ID>/boards`

### URL Parameters

Parameter | Description
--------- | -----------
TEAM-ID | The ID of the team to retrieve
PROJECT-ID | The ID of the project you want to retreive

## Get Specific Board

```shell
curl "http://example.com/api/teams/38881/projects/16f1c520-05c6-11e7-bc31-5554df9b496b/boards/16f212e0-05c6-11e7-a955-8d23fe368669"
  -H "Authorization: YOUR-API-TOKEN"
```

> The above command returns JSON structured like this:

```json
{
    "id": "16f212e0-05c6-11e7-a955-8d23fe368669",
    "created_at": "2017-03-10 19:16:40",
    "updated_at": "2017-05-25 20:28:13",
    "data": [
        {
            "id": "12915881-85b3-4780-9b1a-f09b8c8545bb",
            "board_id": "16f212e0-05c6-11e7-a955-8d23fe368669",
            "component_type": "generic",
            "index": 0,
            "elements": [
                {
                    "image_url": "https://1.bp.blogspot.com/-rwxm61gCRWI/V2GEaVotrcI/AAAAAAAC0LU/jElINxZzmPocj8JaAtUJJDr0-GmjxCj6ACLcB/s1600/charity-search.png",
                    "title": "Welcome to charity:demo",
                    "subtitle": "We believe in a world where everyone is happy",
                    "item_url": "http://charity-demo.com",
                    "buttons": [
                        {
                            "title": "Join Us",
                            "selected": true
                        },
                        {
                            "title": "About Us"
                        }
                    ]
                }
            ],
            "show_for": 1000
        },
        {
            "id": "a9d8854d-5b0b-4951-96a8-d7c9120107ab",
            "board_id": "16f212e0-05c6-11e7-a955-8d23fe368669",
            "component_type": "button",
            "index": 0,
            "text": "Thanks for joining our mission! Super aweosme\nasdf\n\nHow would you like to help?",
            "buttons": [
                {
                    "title": "Give Monthly",
                    "selected": false
                },
                {
                    "title": "Give Once",
                    "selected": true
                }
            ],
            "show_for": 1000
        },
        {
            "id": "e0f1df75-c363-4e4c-a40b-b8913036b40e",
            "board_id": "16f212e0-05c6-11e7-a955-8d23fe368669",
            "component_type": "user_reply",
            "index": 1,
            "text": "Give Once",
            "show_for": 1000
        },
        {
            "id": "ed66532a-5f2c-4b9e-88db-c9a368cec775",
            "board_id": "16f212e0-05c6-11e7-a955-8d23fe368669",
            "component_type": "generic",
            "index": 1,
            "elements": [
                {
                    "image_url": "https://placeimg.com/300/179/tech/grayscale",
                    "title": "Give $60",
                    "subtitle": "$60 can help two people out",
                    "item_url": "",
                    "buttons": [
                        {
                            "title": "Give Now"
                        }
                    ]
                },
                {
                    "image_url": "https://placeimg.com/300/179/tech/grayscale",
                    "title": "Give $30",
                    "subtitle": "$30 can help one person out",
                    "buttons": [
                        {
                            "title": "Give Now"
                        }
                    ]
                },
                {
                    "image_url": "https://placeimg.com/300/179/tech/grayscale",
                    "title": "Custom Donation",
                    "subtitle": "100% of your donation brings happiness to people",
                    "buttons": [
                        {
                            "title": "Give Now",
                            "selected": true
                        }
                    ]
                }
            ],
            "show_for": 1000
        },
        {
            "id": "391e4f6f-973d-46f9-a5e6-814cc8c95e0e",
            "board_id": "16f212e0-05c6-11e7-a955-8d23fe368669",
            "component_type": "typing_indicator",
            "index": 3,
            "show_for": 1000
        },
        {
            "id": "d2fcfa18-03fa-49f0-b2f6-11fa98744b37",
            "board_id": "16f212e0-05c6-11e7-a955-8d23fe368669",
            "component_type": "user_reply",
            "index": 2,
            "text": "Give Now",
            "show_for": 1000
        },
        {
            "id": "4d4f40dc-1b25-44ed-adb2-0173466ae38b",
            "board_id": "16f212e0-05c6-11e7-a955-8d23fe368669",
            "component_type": "text",
            "index": 2,
            "text": "How much would you like to donate?",
            "buttons": [],
            "show_for": 1000
        },
        {
            "id": "3147882b-bbf4-4b3b-bb81-ecd490414f71",
            "board_id": "16f212e0-05c6-11e7-a955-8d23fe368669",
            "component_type": "user_reply",
            "index": 3,
            "text": "$10",
            "show_for": 1000
        },
        {
            "id": "e62393e1-7674-4599-8d3d-b17be2e1a432",
            "board_id": "16f212e0-05c6-11e7-a955-8d23fe368669",
            "component_type": "button",
            "index": 3,
            "text": "Your $10 donation will be processed securely using our payment provider.",
            "buttons": [
                {
                    "title": "Pay Now",
                    "selected": true
                },
                {
                    "title": "Changed my mind"
                }
            ],
            "show_for": 1000
        },
        {
            "id": "8d332c76-f4ae-48d8-a133-ceca3d74940a",
            "board_id": "16f212e0-05c6-11e7-a955-8d23fe368669",
            "component_type": "user_reply",
            "index": 7,
            "text": "Pay Now",
            "show_for": 1000
        }
    ],
    "name": "Your Charity",
    "is_private": false,
    "avatar": "",
    "project_id": "16f1c520-05c6-11e7-bc31-5554df9b496b"
}
```

This endpoint retrieves all boards for a single project. Boards are similar to canvas, as they are what contains all your messages. For projects for `flow` type, there is only 1 board at any given time. For `mock` projects, you can have multiple boards.

### HTTP Request

`GET http://example.com/api/teams/<TEAM-ID>/projects/<PROJECT-ID>/boards/<BOARD-ID>`

### URL Parameters

Parameter | Description
--------- | -----------
TEAM-ID | The ID of the team to retrieve
PROJECT-ID | The ID of the project you want to retreive
BOARD-ID | The ID of the specific board you want to retreive
## Get Messages 
