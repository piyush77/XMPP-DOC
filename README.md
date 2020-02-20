
# XMPPManager

  ## Info
   
   It is an ordinary XMPP client for iOS with Files.
   
   What can this app do:
   
   ### Group chat
   
   - [x] Authentication with server
   - [x] Create and join group with invitation request 
   - [x] Text chat to group
   - [x] Message archiving (history)
   - [x] Push notifications
   - [x] Block user in group
   - [x] Kick user from group
   - [x] Exchange group owner authority
   - [x] Remove group owner
   - [x] Get members of groups
   - [x] GetOwnerofGroup
   - [x] Unscribes from Room
   - [x] Get Room Info
   - [x] Get List of rooms
   - [x] Store and get User avtar and username

## TODO

### Planned Features For Group chat

-  Update Group avtar image
-  image sharing with preview
-  video sharing with preview
-  audio sharing with player
-  File transter 
-  Typing indicator
-  Read unread badge count

### One to one chat        

- Authentication with server
- Text chat 
- Message archiving (history)
- Store and get User avtar and username
- Sharing media -  image, video and audio 
- File transter 
- Read receipt
- Typing Indicator
- Read unread badge count



## Usage example

#### For Message Chat UI we used  following Library 

```
https://github.com/MessageKit/MessageKit
```

#### Authentication 

```swift
XMPPManager.shared.delegate = self
XMPPManager.shared.authenticateWith(userName: "<XMPP_USER_ID>", password: "<XMPP_Password>")
XMPPManager.shared.didAuthenticate = {  isAuth in
   // Authentication response
}
```

#### Authentication 

##### XMPPManagerProtocol

```swift
/// Triggered when xmpp stream connects.
///
func xmppStreamDidConnect()

/// Triggered when xmpp stream Did not connects.
///
func xmppStreamDidNotConnect()

/// Triggered when xmpp stream Disconnect.
///
func xmppStreamDidDisconnect()

/// Triggered when xmpp stream did timeout.
///
func xmppStreamDidTimeout()

/// Triggered when xmpp stream connects.
///
func xmppUserDidRegister()

/// Triggered when xmpp user fails to register.
///
func xmppUserDidNotRegister()

/// Triggered when xmpp user already registered.
func xmppUserAlreadyRegistered()

/// Triggered when xmpp user did authenticate.
///
func xmppUserDidAuthenticate()

/// Triggered when xmpp user did fail to authenticate.
///
func xmppUserDidNotAuthenticate()

/// Triggered when xmpp user status like oneline or offline.
///
func xmppUserStatus(user:String, status: BuddyStatus)

/// Triggered when xmpp did receive message.
///
func xmppDidReceiveMessage(message: USMessage)
```

#### Join or Create Room 

```swift
XMPPRoomManager.shared.delegate = self
XMPPRoomManager.shared.joinRoom(roomJID: "<RoomJID>:, shouldGetHistory: true)
```

#### Send Message to Room 

```swift
XMPPRoomManager.shared.send(message: text, to: "<roomJID>")
```

#### XMPPRoomManager Protocol

```swift
/// Triggered when xmpp did creat room.
///
func roomDidCreate()

/// Triggered when xmpp did Not creatRoom.
///
func didNotCreatRoom()

/// Triggered when room did  Configure.
///
func roomDidConfigureWith(roomID: String)

/// Triggered when user did Join Chat Room.
///
func didJoinChatRoomWith(roomID: String)

/// Triggered when user Accept request to Join Chat Room.
///
func memberDidJoinChatRoomWith()

/// Triggered when xmpp did receive message.
///
func didReceiveGroupMessage(message: USMessage)
```
#### Retrive Message History

```swift
history.addAttribute(withName: "since", stringValue: "1970-01-01T00:00:00Z") // User Requests All History
history.addAttribute(withName: "maxstanzas", stringValue: "1000") // User Requests Limit on Number of Messages in History
history.addAttribute(withName: "seconds", stringValue: "604800") // User Requests History for Last 7 days (seconds)
history.addAttribute(withName: "maxchars", stringValue: "0") // User Requests no history
```

#### Leave From Room

```swift
XMPPRoomManager.shared.xmppRoom.deactivate()
XMPPRoomManager.shared.xmppRoom.leave()
```

#### Disconnect Stream

```swift
XMPPManager.shared.disconnectXMPP()
```
