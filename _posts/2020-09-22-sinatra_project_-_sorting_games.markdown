---
layout: post
title:      "Sinatra Project - Sorting Games"
date:       2020-09-23 00:57:19 +0000
permalink:  sinatra_project_-_sorting_games
---


Sinatra Project *Check!* 

GameSleeve was really fun to work on, especially considering my idea was based off something that a lot of us self-proclaimed gamers used to have before downloadable games existed (Game-sleeves). With that being said, one of the more difficult parts of completing the project was giving Users of GameSleeve their games (and only their games) to display; so I wrote about it.

Since I'd created models for both Users and Games, I knew immediately that I needed to establish a connection between the two. I went back to review the specifics of has_many / belongs_to relationships and had initially decided to add an additional model, UserGames, and use has_many :through to connect the join table both other models to make the connection

![Diagram (w/ Usergames)](http://doc-0o-6k-apps-viewer.googleusercontent.com/viewer/secure/pdf/rkpnv4jjeo0ntos6rh2dirfnh978feen/mnig7lf968fadqv17irj63ca88gclbll/1600822350000/drive/03669428428783454625/ACFrOgAXslWZZsOJiCr2Ok90JmOfhv_B0Nkmg7tZrMI8tA2vA4zHwHxdwLqetjvpr7NvGG2aNlP0zUy00MbI-ICHa_tpwEBhAgJ9XwgFu7amjcOSC7V1pjHwn7lu-ffnm-EcjKAIC9IxnpHZwrRp?print=true&nonce=d4enotn7hpaso&user=03669428428783454625&hash=p4spt4d80ifb26q7o8qbqco212kgkt57)

My thinking in doing so was that I'd have the Games table act as a storage area for all games created by any User, the User table would store users and the UserGames table would store games that belong to the user currently signed in. Connecting the models in this way would work, but something about it didn't sit right with me; it seemed to over-complicate things unnecessarily, especially when I read through the methods that accompanied the relationship. There was almost too much functionality in comparison to what I wanted to accomplish.

So I went back to the drawing board to simplify the relationship and get what I wanted out of the connection.

Having read up on the has_many / belongs_to relationship once more I decided to proceed with a basic has_many / belongs to relationship. 

![Diagram w/o Usergames)](http://doc-14-6k-apps-viewer.googleusercontent.com/viewer/secure/pdf/rkpnv4jjeo0ntos6rh2dirfnh978feen/hd0j0gd1eaq72nfqc9qb05mlq824hs33/1600822350000/drive/03669428428783454625/ACFrOgA43FpJc0pXv1fd5U13v57iVUvXkQSbA6kbaLor4UG3jSm5ZzM-nbcr9pMCSQ6xJTeyjArIeZNgPImRqh3U1MzowoFca70E-I1xzta2eFpAJHfPqg0X2Gw8gqxs3LltihVsT2iDDINTWFQk?print=true)

Here I'm able to do everything I was wanted to do with the other (has_many :through) relationship, however with the has_many  :through I'd get an extra bit of functionality; which is what I found interesting! If I had used this method to form the relationship between my models I could give Users access to all games created by anyone using GameSleeve through my UserGames (Game storage). This could be really useful if I was planning on doing something like, for example, creating a homepage for non-logged-in users that displayed examples of games created by users with accounts. 

This was a decision that took me a good while to come to but, strangely enoigh, I enjoyed the process of deciding what type of functionality I want and adjusting the different model/table relationships accordingly. 

Below there's a photo that helped me out a lot in understanding when it's necessesary to use the join table and when to just use has_many/belongs/to.

![has_many/has_many :through](http://i.stack.imgur.com/lr4RB.png)


