<!---------------------------------------------------------------------------->
<!-- STOP, LOOK & LISTEN!                                                   -->
<!-- ====================                                                   -->
<!-- Do NOT edit this file directly since it's generated from a template    -->
<!-- file, using https://github.com/IonicaBizau/node-blah                   -->
<!--                                                                        -->
<!-- If you found a typo in documentation, fix it in the source files       -->
<!-- (`lib/*.js`) and make a pull request.                                  -->
<!--                                                                        -->
<!-- If you have any other ideas, open an issue.                            -->
<!--                                                                        -->
<!-- Please consider reading the contribution steps (CONTRIBUTING.md).      -->
<!-- * * * Thanks! * * *                                                    -->
<!---------------------------------------------------------------------------->

# youtube-api [![Donate now][donate-now]][paypal-donations]

A Node.JS module, which provides an object oriented wrapper for the Youtube v3 API.

[![NPM](https://nodei.co/npm/youtube-api.png?downloads=true)](https://nodei.co/npm/youtube-api/)

## Installation

```sh
$ npm i youtube-api
```

## Example

You may be interested to download [this test application](https://github.com/IonicaBizau/test-youtube-api)
and play with the YouTube API resources there. Below you see an example how to use the library.

```js
// Dependencies
var Youtube = require("youtube-api");

// Authenticate using an access token
Youtube.authenticate({
    type: "oauth"
  , token: "your access token"
});

// List your subcribers
Youtube.subscriptions.list({
    "part": "id"
  , "mySubscribers": true
  , "maxResults": 50
}, function (err, data) {
    console.log(err || data);
});

// Add a Video to a playlist
Youtube.playlistItems.insert({
    "part": "snippet"
  , "resource": {
        "snippet": {
            "playlistId": "YouTube Playlist ID"
          , "resourceId": {
                "kind" : "youtube#video"
              , "videoId" : "YouTube Video ID"
            }
        }
    }
}, function (err, data) {
    console.log(err || data);
});

```

## Documentation

The [official Youtube documentation](https://developers.google.com/youtube/v3/docs/) is a very useful resource.

 - [Activities](https://developers.google.com/youtube/v3/docs/activities)
 - [ChannelBanners](https://developers.google.com/youtube/v3/docs/channelBanners)
 - [Channels](https://developers.google.com/youtube/v3/docs/channels)
 - [GuideCategories](https://developers.google.com/youtube/v3/docs/guideCategories)
 - [PlaylistItems](https://developers.google.com/youtube/v3/docs/playlistItems)
 - [Playlists](https://developers.google.com/youtube/v3/docs/playlists)
 - [Search](https://developers.google.com/youtube/v3/docs/search)
 - [Subscriptions](https://developers.google.com/youtube/v3/docs/subscriptions)
 - [Thumbnails](https://developers.google.com/youtube/v3/docs/thumbnails)
 - [VideoCategories](https://developers.google.com/youtube/v3/docs/videoCategories)
 - [Videos](https://developers.google.com/youtube/v3/docs/videos)

If you have any questions, just [open an issue](https://github.com/IonicaBizau/youtube-api/issues/new).

### Authentication

#### OAuth (Access Token)
```js
Youtube.authenticate({
    type: "oauth"
  , token: "your access token"
});
```

#### OAuth (Refresh Token)
```js
Youtube.authenticate({
    type: "oauth"
  , refresh_token: "your refresh token"
  , client_id: "your client id"
  , client_secret: "your client secret"
  , redirect_url: "your refresh url"
});
```

#### Server Key
```js
Youtube.authenticate({
    type: "key"
  , key: "your server key"
});
```

#### JWT
Just perfect for server side only authentication. It does not require
client side interaction.

```js
Youtube.authenticate({
    type: "jwt"
  , email: "77....3vv@developer.gserviceaccount.com"
  , keyFile: "... auth.pem"
  , key: "fb....d50"
  , subject: "you@gmail.com" // optional
  , scopes: ["https://www.googleapis.com/auth/youtube"]
}).authorize(function (err, data) {
    if (err) { throw err; }
    /* Access resources */
});
```

## How to contribute
Have an idea? Found a bug? See [how to contribute][contributing].

## License
[KINDLY][license] © [Ionică Bizău][website]–The [LICENSE](/LICENSE) file contains
a copy of the license.

[license]: http://ionicabizau.github.io/kindly-license/?author=Ionic%C4%83%20Biz%C4%83u%20%3Cbizauionica@gmail.com%3E&year=2015
[contributing]: /CONTRIBUTING.md
[website]: http://ionicabizau.net
[docs]: /DOCUMENTATION.md
[paypal-donations]: https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=MG98D7NPFZ3MG
[donate-now]: http://i.imgur.com/jioicaN.png