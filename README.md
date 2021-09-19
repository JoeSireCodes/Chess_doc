# Chess_doc
Documentation for Zuri chess plugin on "allowing a user watch a game" 
# Allows a user to watch existing game play

###### A user can join a game directly by registering on the Core API Auth as a spectator while a game is on. Simply put; puts a player into a gaming room as spectator.

-------------------------------------------------------------------------------------------------------------------

Method: PATCH

``` sh

 // game spectators

    spectators: Joi.array()

      .items(

         Joi.object({

          user_id: Joi.string().required(),

          user_name: Joi.string().required(),

          image_url: Joi.string(),

         })

      )

        .allow(null),

```

Endpoint: /Watch

##### Request body

-	Application/json

##### Parameters

-	Accepts a integer as the user_id

-	Accepts a string as the user_name

-	Accepts a string as the image_url

```sh

{

    “user_id”: 2,

     “user_name”: "John Doe",

     "user_id": "string",

     "image_url": "string"

}

```

> Once you click on Watch game, It takes an array of spectators by recoding their user_id, user_name and image_url

> All parameters will be inputed and you receive a response.

> When spectators leave, they are automatically removed from the array of spectators. 

### Responses with description

``` sh

Code: 200

Means you’ve been successfully registered as a spectator in the game.

Code: 500

Means an error has occured and your request to watch the game as a spectator failed.

{ 

    “message”: “Game not found”,

    “data”: null,

    “success”: false

}

```

## Message as a Spectator

This allows spectators to be able to drop comments/messages while watching an existing live game

``` sh

 \\messages

       messages: Joi.array()

       .items(

           Joi.object({

               user_name: Joi.string().required(),

               text: Joi.string().required(),

               image_url: Joi.string(),           

            })

       )

       .allow(null),

```

> Its accepts a user_id (in integer) text (in string) in JSON format

##### url link [https://chess.zuri.chat/game/watch]
