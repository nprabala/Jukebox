# Jukebox
An app for party playlists


# Project Status

## Infrastructure

* User Music Service: Spotify
* Language: iOS native (Swift 4)
* Communication Channel: Bluetooth

## Build Guest Side: (Unassigned)

* Make an app that can read user profile from Spotify
* Extract top songs, artists, and genres from profile
* Convert extracted items into some combination of Spotify API track features (ie, danceability) and explicit song/artist names.

Nice To Have:

* Allow users to request specific songs for the queue. 

## Build Host Side: (Unassigned)

* Accomplish same work as guest side for Jukebox Host.
* Match Preferencs to the user profile that generated them (beginning with host)
* Compile all Preferences into one seed.
* Generate a Playlist from seed using Spotify API.
* Create remove button to remove a user and their Preferences from the collection.

Nice To Have:

* Make playlist features visible to and adjustable by host.


## Build Host-Guest Communications: (Unassigned)

* Hosts are listening for guests.
* Guests can send Preferences to specific host.
* Create leave button for guests to remove themselves from the collection on this Jukebox





### Relevant Links

Spotify iOS sdk:

https://github.com/spotify/ios-sdk

Other Spotify (Web) Apps:

https://developer.spotify.com/community/showcase/

App Credentials and Data Management:

https://developer.spotify.com/dashboard/applications

Track Features For Developing Group Preferences:

https://developer.spotify.com/documentation/web-api/reference/tracks/get-audio-features/

Get recommendations based on Track Features:

https://developer.spotify.com/documentation/web-api/reference/browse/get-recommendations/

React Native Spotify API package:

https://github.com/lufinkey/react-native-spotify


Info on Mobile Bluetooth Connections:

* This post comes from the mobile game Spaceteam, which does continuous Bluetooth connections (while we only need quick transfers of data), so not all limitations apply equally.

http://spaceteamadmirals.club/blog/the-spaceteam-networking-post/


* This post comes from someone who made an iOS app for communicating between many phones. This will likely be a good source of guidance moving forward.

https://itnext.io/whos-there-simple-swift-app-for-chatting-with-colleagues-around-a88ff765736f


# Event Planner


### Problem with group messages
Don’t wanna keep texting a group message over and over saying you’re free or offering events. Could get annoying or could seem desperate (social stigma). 

### Problem with other apps
Don’t want an app just telling you who is free. Could lead to different friend groups and individuals outside of those groups being interested in which case you probably wouldn’t want to merge the groups/individuals nor respond to every individual response saying “I’m going with x instead”.  Also, when thinking about events, you generally know what group or groups you’d be willing to go with. Also don’t want an app that informs everyone of your free time, whether that be you pushing a free button or reading from you calendar. You may not want everyone to know you are free. 

Ideally this app is built around groups, not individuals. An individual A could mark themselves as flexible/free (to all groups they are a part of or to a certain few that they indicate). Person B would see that A is available only if B and A are in the same group and A has chosen that group to indicate that they are free. For instance, the home screen could be a list of group banners, and a little note in each banner could indicate how many people in that group are free. Users could then use this to suggest events. (Note: we may not want this at all, since it bloats the app a little. If we just want to focus on suggested events, we will already know who is free by who responds)

### Suggesting events
In groups, users can also suggest events. Obviously not everyone will constantly be on the app updating whether or not they are free (this would probably be ideal), so suggesting events to specific groups would be a way to notify the members of that group that someone wants to hang out. This suggested event should be emphasized to be more of an interest survey, not something that is set in stone. Users can respond whether they are interested or not, and based on these responses,  the suggester can decide to plan the event or to drop it. This should also allow for sending a suggested event to multiple groups since some groups may allow for more people to go than others. Since this is just an interest survey kinda of deal, it’s no big deal for the suggester to drop the event for one group and but plan it for the other group. Likewise, it could be cool for the option to merge groups in specific cases if the suggester would like. 

Suggested events will come as a banner saying “X from Coworkers is interested in doing Y. Would you be interested in joining?”. To deal with the stigma around being annoying/desperate, the initial suggestion can be anonymous. “Someone from Coworkers would like to grab a beer”. Checking interested would put you on the interested list for the suggester to see. If they decide to go through with the event, it’ll add everyone on the interested lists into a group chat, sending notifications to. 

### Misc
Once an event is for sure and the group chat is formed, there could also be an option to add additional people. Choosing to do so will send the same initial interest request (but perhaps with a more defined event name/time/location) and the receiving user can say interested (adding them to the chat) or no. 

You can maybe also suggest events to a group of individual people that may not be in an already defined group (which is good for surprise parties without revealing plans to the person who might be in the same groups as you).  This would depend on knowing a user’s username or having them saved as a friend in the app. 

Connections: If we use facebook, no need to really create profiles on the app or two add friends. Should be able to just search users through a Facebook API. Also, if we use facebook, no need to actually create a group chat. Once the suggester decides to create the event, we should be able to make an API call to create a group message on facebook messenger, send an initial message specified by the user, and redirect the user to the messenger app. The limitation to this is that we won’t be able to add new users who respond late or who are added additionally to the message. Therefore we might need our own group message. 

