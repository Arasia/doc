# Google Authenticator

## Overview
1. Extend RFC 6238(Extend RFC 4226)
1. Use HMAC-SHA-1
1. Time-step size is 30s
1. Result of OTP is 6 length number

## Authentication Flow

1. Server generate key by user & save Key by user.
1. Server share the key to user.
1. User register the key with Google Authenticator.
1. User generate OTP with registered key and current time.
1. Server generate OTP with registered key and current time.
1. User submit the OTP to server
1. Server verifies that server's OTP is the same as the user's OTP.

## Requirement

1. Key is unique to each user
1. The time zone of server is same as user's
    - Google Authenticator uses time-step([Time-step size is 30s](https://tools.ietf.org/html/rfc6238#section-5.2))

## Reference Link
- [Google Authenticator Open Source (Github)](https://github.com/google/google-authenticator)
- [RFC 6238 (TOTP)](https://tools.ietf.org/html/rfc6238)
- [RFC 4226 (HOTP)](https://tools.ietf.org/html/rfc4226)
- [REF 2104 (HMAC)](https://tools.ietf.org/html/rfc2104)
- [Blog - Develop Google Authenticator with Java](https://zero-gravity.tistory.com/221)