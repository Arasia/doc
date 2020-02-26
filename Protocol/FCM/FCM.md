# FCM

[TOC]

> [Firebase Document](https://firebase.google.com/docs/cloud-messaging/http-server-ref)

## Downstream HTTP Message Syntax

### Downstream HTTP Message (JSON) 

#### Targets

##### to

- Usage
    - Required
        - Optional
    - Parameter Type 
        - String
- Description
    - The value can be
        - Device's registration token
        - A group's notification key
        - A single Topic
    - If you want multi topics, Use [condition](#condition) parameter
    - If you want message to multi device, Use [registration_ids][#registration ids] parameter

##### registration_ids

- Usage
    - Required
        - Optional
    - Parameter Type
        - Array of Strings
- Description
    - this parameter specifies the recipient of a multi cast Message
    - The array must contain at least 1 and at most 1000 registration tokens
    - If you want message to single device, Use [to](#to) parameter

##### condition

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - This parameter specifies a logical expression of conditions that determine the message target
    - Supported condition : 'your topic' in 'topics'
    - This value is case-insensitive
    - Supported operators : &&, ||
        - Maximum tow operators per topic massage

##### ~~notification_key~~

- Usage
    - Required
        - Deprecated
        - Optional
    - Parameter Type
        - String
- Description
    - This parameter is Deprecated
    - use [to](#to) to specify message recipients
    - For more information on how to send messages to multiple devices, see the documentation for your platform.

#### Options

##### collapse_key

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - This parameter identifiers a Group of messages that can be collapsed
    - Only the last message gets sent when delivery can be resumed
    - __Note that there is no guarantee of the order in which messages get sent__
    - A maximum of 4 different collapse keys is allowed at any given time

##### priority

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - Sets the priority of the message
    - Valid value
        - normal (On iOS, APNs priority 5)
            - The app may receive the message with unspecified delay
        - high (On iOS, APNs priority 10)
            - Message is send immediately

##### content_available

- Usage
    - Required
        - Optional
    - Parameter Type
        - Boolean
- Description
    - iOS
        - use this field to represent __content-available__ in the APNs payload
        - When this is set to true, an inactive client app is awoken, and the message is sent through APNs as a silent notification and not through the FCM connection server
    - Android
        - Data messages wake the app by default
    - Chrome
        - Currently not supported

##### mutable_content

- Usage
    - Required
        - Optional
    - Parameter Type
        - JSON boolean
- Description
    - iOS
        - __Currently for iOS 10+ device only__
        - Use this field to represent __mutable-content__ in the APNs payload
        - When this is set to true, the content of the notification can be modified before it is displayed, using a [Notification Service app extension](https://developer.apple.com/documentation/usernotifications/unnotificationserviceextension)
    - Android & Web
        - This parameter will be ignored

##### time_to_live

- Usage
    - Required
        - Optional
    - Parameter Type
        - Number
- Description
    - This parameter specifies how long (in seconds) the message should be kept in FCM storage if the device is offline
    - The maximum time to live supported is 4 weeks
    - Default value
        - 4 weeks
    - For more information, see [Setting the lifespan fo a message](https://firebase.google.com/docs/cloud-messaging/concept-options#ttl)

##### restricted_package_name

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - __Android Only__
    - this Parameter specifies the package name of the application where the registration tokens must match in order to receive the message

##### dry_run

- Usage
    - Required
        - Optional
    - Parameter Type
        - Boolean
- Description
    - When set to true, allows developers to test a request without actually sending a message
    - Default value
        - false

#### Payload

##### data

- Usage
    - Required
        - Optional
    - Parameter Type
        - Object
- Description
    - This parameter specifies the custom key-value pairs of the message's payload
    - __The key should not be a reserved word ("from", "message_type", or any word starting with "google" or "gcm")__
    - __Do not use any of the words defined in this table__
    - Values in string types are recommended
        - You have to convert values in objects or other non-string data types to string
    - iOS
        - If the message is sent via APNs, it represents the custom data fields
        - If the message is sent via FCM connection server, it would be represented as key value dictionary in AppDelegate application : didReceiveRemoteNotification :
    - Android
        - This would result in an intent extra named score with the string value 3 x 1

##### notification

- Usage
    - Required
        - Optional
    - Parameter Type
        - Object
- Description
    - This parameter specifies the predefined, user-visible key-value pairs of the notification payload
    - See [Notification payload support](#Notification-payload-support) for detail
    - For more information about notification message and data message options, see [Message types](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages)
    - iOS
        - If a notification payload is provided, or the [content_available](#content available) option is set the true, the message is __sent through APNs__, otherwise it is sent through the FCM connection server

---

---

### Notification payload support

#### iOS

##### title

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The notification's title
    - This field is not visible on iOS phones and tablets

##### body

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The notification's body text

##### sound

- Usage
    - Required
        - Optional
    - Parameter Type
        - String or Dictionary
- Description
    - The sound to play when the device receives the notification
    - String specifying sound files in the main bundle of the client app or in the Library/Sounds folder of the app's data container
    - See the [iOS Developer Library](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW10) for more information

##### badge

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The value of the badge on the home screen app icon
    - If not specified, the badge is not changed
    - If set to 0, the badge is removed

##### click_action

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The action associated with a user click on the notification
    - Corresponds to __category__ in the APNs payload

##### subtitle

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The notification's subtitle

##### body_loc_key

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The key to the body string in the app's String resources to use to localize the body text to the user's current localization
    - Corresponds to __loc-key__ in the APNs payload
    - See [Payload Key Reference](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/PayloadKeyReference.html) and [Localizing the Content of Your Remote Notifications](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW9) for more information

##### body_loc_args

- Usage
    - Required
        - Optional
    - Parameter Type
        - JSON array as string
- Description
    - Variable string values to be used in place of the format specifiers in [body_loc_key](#body_loc_key) to use to localize the body text to the user's current localization.
    - Corresponds to __loc-args__ in the APNs payload
    - See [Payload Key Reference](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/PayloadKeyReference.html) and [Localizing the Content of Your Remote Notifications](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW9) for more information

##### title_loc_key

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The key to the title string in the app's string resources to use to localize the title text to the user's current localization.
    - Corresponds to __title-loc-key__ in the APNs payload
    - See [Payload Key Reference](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/PayloadKeyReference.html) and [Localizing the Content of Your Remote Notifications](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW9) for more information

##### title_loc_args

- Usage
    - Required
        - Optional
    - Parameter Type
        - JSON array as string
- Description
    - Variable string values to be used in place of the format specifiers in [title_loc_key](#title_loc_key) to use to localize the body text to the user's current localization.
    - Corresponds to __title-loc-args__ in the APNs payload
    - See [Payload Key Reference](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/PayloadKeyReference.html) and [Localizing the Content of Your Remote Notifications](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW9) for more information

---

#### Android

##### title

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The notification's title

##### body

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The notification's body text

##### android_channel_id

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The [notification's channel id](https://developer.android.com/preview/features/notification-channels.html) (new in Android O)
    - The app must create a channel with this channel ID before any notification with this channel ID is received
    - If you don't send this channel ID in the request, or if the channel ID provided has not yet been created by the app, FCM uses the channel ID specified in the app manifest

##### icon

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The notification's icon
    - Set the notification icon to __myicon__ for drawable resource __myicon__
    - If you don't send this key in the request, FCM displays the launcher icon specified in your app manifest

##### sound

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The sound to play when the device receives the notification
    - Supports __"default__ or the filename of a sound resource bundled in the app
    - Sound files must reside in __/res/raw/__

##### tag

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - Identifier used to replace existing notifications in the notification drawer
    - If not specified, each request creates a new notification
    - If specified and a notification with the same tag is already being shown, the new notification replaces the existing one in the notification drawer

##### color

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The notification's icon color, expressed in __#rrggbb__ format

##### click_action

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The action associated with a user click on the notification
    - If specified, an activity with a matching intent filter is launched when a user clicks on the notification

##### body_loc_key

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The key to the body string in the app's string resources to use to localize the body text to the user's current localization
    - See [String Resources](https://developer.android.com/guide/topics/resources/string-resource.html) for more information

##### body_loc_args

- Usage
    - Required
        - Optional
    - Parameter Type
        - JSON array as string
- Description
    - Variable string values to be used in place of the format specifiers in [body_loc_key](#body_loc_key) to use to localize the body text to the user's current localization.
    - See [Formatting and Styling](https://developer.android.com/guide/topics/resources/string-resource.html#FormattingAndStyling) for more information

##### title_loc_key

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The key to the title string in the app's string resources to use to localize the title text to the user's current localization.
    - See [String Resources](https://developer.android.com/guide/topics/resources/string-resource.html) for more information

##### title_loc_args

- Usage
    - Required
        - Optional
    - Parameter Type
        - JSON array as string
- Description
    - Variable string values to be used in place of the format specifiers in [title_loc_key](#title_loc_key) to use to localize the body text to the user's current localization.
    - See [Formatting and Styling](https://developer.android.com/guide/topics/resources/string-resource.html#FormattingAndStyling) for more information

---

#### Web (JavaScript)

##### title

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The notification's title

##### body

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The notification's body text

##### icon

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The URL to use for the notification's icon

##### click_action

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - The action associated with a user click on the notification
    - For all URL values, HTTPS is required

---

---

### Interpreting a downstream message response

#### Downstream HTTP message response header

##### 200

- Message was processed successfully
- The response body will contain more details about the message status, but its format will depend whether the request was JSON or plain text
- See [Downstream HTTP message response body (JSON)](#Downstream HTTP message response body (JSON)) for more details.

##### 400

- Only applies for JSON requests
- Indicates that the request could not be parsed as JSON, or it contained invalid fields
- The exact failure reason is described in the response and the problem should be addressed before the request can be retried.

##### 401

- There was an error authenticating the sender account.

##### 5xx

- Errors in the 500-599 range (such as 500 or 503) indicate that there was an internal error in the FCM connection server while trying to process the request, or that the server is temporarily unavailable (for example, because of timeouts)
- Sender must retry later, honoring any __Retry-After__ header included in the response
- Application servers must implement exponential back-off.

---

#### Downstream HTTP message response body (JSON)

##### multicast_id

- Usage
    - Required
        - Required
    - Parameter Type
        - Number
- Description
    - Unique ID (number) identifying the multicast message

##### success

- Usage
    - Required
        - Required
    - Parameter Type
        - Number
- Description
    - Number of messages that were processed without an error

##### failure

- Usage
    - Required
        - Required
    - Parameter Type
        - Number
- Description
    - Number of messages that could not be processed

##### result

- Usage
    - Required
        - Required
    - Parameter Type
        - Array of Object
- Description
    - Array of objects representing the status of the messages processed
    - The objects are listed in the same order as the request
    - For each registration ID in the request, its result is listed in the same index in the response.
        - message_id
            - String specifying a unique ID for each successfully processed message
        - registration_id
            - Optional string specifying the registration token for the client app that the message was processed and sent to
        - error
            - String specifying the error that occurred when processing the message for the recipient. The possible values can be found in [table 9](https://firebase.google.com/docs/cloud-messaging/http-server-ref#table9)

---

#### Topic message HTTP response body (JSON)

##### message_id

- Usage
    - Required
        - Optional
    - Parameter Type
        - Number
- Description
    - The topic message ID when FCM has successfully received the request and will attempt to deliver to all subscribed devices

##### error

- Usage
    - Required
        - Optional
    - Parameter Type
        - String
- Description
    - Error that occurred when processing the message. The possible values can be found in [table 9](https://firebase.google.com/docs/cloud-messaging/http-server-ref#table9).

---

---

### Downstream message error response codes

#### Missing Registration Token

- HTTP Code
    - 200 + error:MissingRegistration
- Recommended Action
    - Check that the request contains a registration token in the [to](#to) or [registration_ids](#registration_ids) field

#### Invalid Registration Token

- HTTP Code
    - 200 + error:InvalidRegistration
- Recommended Action
    - Check the format of the registration token you pass to the server
    - Make sure it matches the registration token the client app receives from registering with Firebase Notifications
    - Do not truncate or add additional characters

#### Unregistered Device

- HTTP Code
    - 200 + error:NotRegistered
- Recommended Action
    - An existing registration token may cease to be valid in a number of scenarios
        - If the client app unregisters with FCM
        - If the client app is automatically unregistered which can happen if the user uninstalls the application
            - For example, on iOS, if the APNS Feedback Service reported the APNS token as invalid.
        - If the registration token expires
            - for example, Google might decide to refresh registration tokens, or the APNS token has expired for iOS devices
        - If the client app is updated but the new version is not configured to receive messages.
    - For all these cases, remove this registration token from the app server and stop using it to send messages

#### Invalid Package Name

- HTTP Code
    - 200 + error:InvalidPackageName
- Recommended Action
    - Make sure the message was addressed to a registration token whose package name matches the value passed in the request

#### Mismatched Sender

- HTTP Code
    - 200 + error:MismatchSenderId
- Recommended Action
    - A registration token is tied to a certain group of senders
    - When a client app registers for FCM, it must specify which senders are allowed to send messages
    - You should use one of those sender IDs when sending messages to the client app
    - If you switch to a different sender, the existing registration tokens won't work

#### Message Too Big

- HTTP Code
    - 200 + error:MessageTooBig
- Recommended Action
    - Check that the total size of the payload data included in a message does not exceed FCM limits
    - 4096 bytes for most messages, or 2048 bytes in the case of messages to topics
    - This includes both the keys and the values

#### Invalid Data Key

- HTTP Code
    - 200 + error:InvalidDataKey
- Recommended Action
    - Check that the payload data does not contain a key (such as __from__, or __gcm__, or any value prefixed by __google__) that is used internally by FCM
    - Note that some words (such as __collapse_key__) are also used by FCM but are allowed in the payload, in which case the payload value will be overridden by the FCM value

#### Invalid Time to Live

- HTTP Code
    - 200 + error:InvalidTtl
- Recommended Action
    - Check that the value used in [time_to_live](#time_to_live) is an integer representing a duration in seconds between 0 and 2,419,200 (4 weeks)

#### Device Message Rate Exceeded

- HTTP Code
    - 200 + error:DeviceMessageRateExceeded
- Recommended Action
    - The rate of messages to a particular device is too high
    - If an iOS app sends messages at a rate exceeding APNs limits, it may receive this error message
    - Reduce the number of messages sent to this device and use [exponential](https://en.wikipedia.org/wiki/Exponential_backoff) backoff to retry sending

#### Topics Message Rate Exceeded

- HTTP Code
    - 200 + error:TopicsMessageRateExceeded
- Recommended Action
    - The rate of messages to subscribers to a particular topic is too high
    - Reduce the number of messages sent for this topic and use [exponential](https://en.wikipedia.org/wiki/Exponential_backoff) backoff to retry sending.

#### Invalid APNs credentials

- HTTP Code
    - 200 + error:InvalidApnsCredential
- Recommended Action
    - A message targeted to an iOS device could not be sent because the required APNs authentication key was not uploaded or has expired
    - Check the validity of your development and production credentials.

#### Invalid JSON

- HTTP Code
    - 400
- Recommended Action
    - Check that the JSON message is properly formatted and contains valid fields

#### Invalid Parameters

- HTTP Code
    - 400 + error:InvalidParameters
- Recommended Action
    - Check that the provided parameters have the right name and type

#### Authentication Error

- HTTP Code
    - 401
- Recommended Action
    - The sender account used to send a message couldn't be authenticated
        - Authorization header missing or with invalid syntax in HTTP request
        - The Firebase project that the specified server key belongs to is incorrect
        - Legacy server keys only—the request originated from a server not whitelisted in the Server key IPs
    - Check that the token you're sending inside the Authentication header is the correct Server key associated with your project
    - See [Checking the validity of a Server key ](https://firebase.google.com/docs/cloud-messaging/auth-server#checkAPIkey)for details
    - If you are using a legacy server key, you're recommended to upgrade to a new key that has no IP restrictions.

#### Timeout

- HTTP Code
    - 5xx or 200 + error:Unavailable
- Recommended Action
    - The server couldn't process the request in time
    - Retry the same request but you must
        - Honor the __Retry-After__ header if it is included in the response from the FCM Connection Server
        - Implement exponential back-off in your retry mechanism
            - If you're sending multiple messages, delay each one independently by an additional random amount to avoid issuing a new request for all messages at the same time.
    - __Senders that cause problems risk being blacklisted__

#### Internal Server Error

- HTTP Code
    - 5xx or 200 + error:InternalServerError
- Recommended Action
    - The server encountered an error while trying to process the request
    - You could retry the same request following the requirements listed in [Timeout](#timeout)
    - If the error persists, please contact [Firebase support](https://firebase.google.com/support/)

---

---

### Device Group Management

- The following table lists the keys for creating device groups and adding and removing members
- For more information, see the guide for your platform, [iOS](https://firebase.google.com/docs/cloud-messaging/ios/device-group) or [Android](https://firebase.google.com/docs/cloud-messaging/android/device-group)

#### operation

- Usage
    - Required
        - Required
    - Parameter Type
        - String
- Description
    - The operation to run
    - Valid values
        - create
        - add
        - remove

#### notification_key_name

- Usage
    - Required
        - Required
    - Parameter Type
        - String
- Description
    - The user-defined name of the device group to create or modify

#### notification_key

- Usage
    - Required
        - Required (except for __create__)
    - Parameter Type
        - String
- Description
    - Unique identifier of the device group
    - This value is returned in the response for a successful __create__ operation, and is required for all subsequent operations on the device group.

#### registration_ids

- Usage
    - Required
        - Required
    - Parameter Type
        - Array of string
- Description
    - The device tokens to add or remove
    - If you remove all existing registration tokens from a device group, FCM deletes the device group.

