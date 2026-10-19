# iOS SDKs

iPhoneOS SDKs, one per branch, for building iOS code on the device itself.
This repository is the default SDK source of
[Apelin](https://github.com/owngoal-dev/Apelin), the on-device IDE for
jailbroken iOS.

## Credit

Every SDK up to iPhoneOS 27.0 comes from
[xybp888/iOS-SDKs](https://github.com/xybp888/iOS-SDKs), which collected
them; thank you. This repository started as a copy of it and is kept
separately, laid out one SDK per branch. iPhoneOS 27.1 was added from
Xcode 27.1.

## The SDKs are Apple's

The files on the `sdk/` branches are Apple's iPhoneOS SDKs, unchanged.
They are Apple's work under Apple's terms. Nothing in this repository
grants, or claims, any license to them; this README is the only file of
our own.

## Branches

Each branch `sdk/iPhoneOS<version>` holds exactly one folder,
`iPhoneOS<version>.sdk`, named for the `CanonicalName` in that SDK's own
`SDKSettings.json`. The branches share no history with each other or with
`main`, so cloning one branch fetches one SDK.

| Branch | SDK | From |
| --- | --- | --- |
| `sdk/iPhoneOS13.0` | iPhoneOS 13.0 | xybp888 `iPhoneOS13.0.sdk` |
| `sdk/iPhoneOS13.4` | iPhoneOS 13.4 | xybp888 `iPhoneOS13.4.sdk` |
| `sdk/iPhoneOS13.5` | iPhoneOS 13.5 | xybp888 `iPhoneOS13.5.sdk` |
| `sdk/iPhoneOS13.6` | iPhoneOS 13.6 | xybp888 `iPhoneOS13.6.sdk` |
| `sdk/iPhoneOS13.7` | iPhoneOS 13.7 | xybp888 `iPhoneOS13.7.sdk` |
| `sdk/iPhoneOS14.0` | iPhoneOS 14.0 | xybp888 `iPhoneOS14.0.sdk` |
| `sdk/iPhoneOS14.1` | iPhoneOS 14.1 | xybp888 `iPhoneOS14.1.sdk` |
| `sdk/iPhoneOS14.2` | iPhoneOS 14.2 | xybp888 `iPhoneOS14.2.sdk` |
| `sdk/iPhoneOS14.4` | iPhoneOS 14.4 | xybp888 `iPhoneOS14.4.sdk` |
| `sdk/iPhoneOS14.5` | iPhoneOS 14.5 | xybp888 `iPhoneOS14.5.sdk` |
| `sdk/iPhoneOS15.2` | iPhoneOS 15.2 | xybp888 `iPhoneOS15.2.sdk` |
| `sdk/iPhoneOS15.5` | iPhoneOS 15.5 | xybp888 `iPhoneOS15.5.sdk` |
| `sdk/iPhoneOS16.1` | iPhoneOS 16.1 | xybp888 `iPhoneOS16.1.sdk` |
| `sdk/iPhoneOS16.2` | iPhoneOS 16.2 | xybp888 `iPhoneOS16.2.sdk` |
| `sdk/iPhoneOS16.4` | iPhoneOS 16.4 | xybp888 `iPhoneOS16.4.sdk` |
| `sdk/iPhoneOS17.0` | iPhoneOS 17.0 | xybp888 `iPhoneOS17.0.sdk` |
| `sdk/iPhoneOS17.2` | iPhoneOS 17.2 | xybp888 `iPhoneOS17.2.sdk` |
| `sdk/iPhoneOS17.4` | iPhoneOS 17.4 | xybp888 `iPhoneOS17.4.sdk` |
| `sdk/iPhoneOS17.5` | iPhoneOS 17.5 | xybp888 `iPhoneOS17.5.sdk` |
| `sdk/iPhoneOS18.0` | iPhoneOS 18.0 | xybp888 `iPhoneOS18.0.sdk` |
| `sdk/iPhoneOS18.1` | iPhoneOS 18.1 | xybp888 `iPhoneOS18.1.sdk` |
| `sdk/iPhoneOS18.2` | iPhoneOS 18.2 | xybp888 `iPhoneOS18.2.1.sdk` |
| `sdk/iPhoneOS18.4` | iPhoneOS 18.4 | xybp888 `iPhoneOS18.4.sdk` |
| `sdk/iPhoneOS18.5` | iPhoneOS 18.5 | xybp888 `iPhoneOS18.5.sdk` |
| `sdk/iPhoneOS18.6` | iPhoneOS 18.6 | xybp888 `iPhoneOS18.6.sdk` |
| `sdk/iPhoneOS26.0` | iPhoneOS 26.0 | xybp888 `iPhoneOS26.0.sdk` |
| `sdk/iPhoneOS26.1` | iPhoneOS 26.1 | xybp888 `iPhoneOS26.1.sdk` |
| `sdk/iPhoneOS26.2` | iPhoneOS 26.2 | xybp888 `iPhoneOS26.2.sdk` |
| `sdk/iPhoneOS26.4` | iPhoneOS 26.4 | xybp888 `iPhoneOS26.4.sdk` |
| `sdk/iPhoneOS26.5` | iPhoneOS 26.5 | xybp888 `iPhoneOS26.5.sdk` |
| `sdk/iPhoneOS27.0` | iPhoneOS 27.0 | xybp888 `iPhoneOS27.0.sdk` |
| `sdk/iPhoneOS27.1` | iPhoneOS 27.1 | Xcode 27.1 (27A9275) |

Where xybp888 kept several folders whose `SDKSettings.json` names the same
SDK (`iPhoneOS17.0.2.sdk`, `iPhoneOS17.1.sdk` and others are all
iPhoneOS 17.0), the branch takes the folder named for that version, or
the first one that starts with it. The folders for iPhoneOS 9.3 to 12.4
have no `SDKSettings.json`, which Apelin reads an SDK's identity from,
so they have no branch here.

## How Apelin uses them

Apelin lists the branches under `sdk/` without fetching anything, shows the
ones not installed yet, and imports one by a shallow clone of that single
branch over HTTPS. It checks the tree before registering it: the identity
from `SDKSettings.json`, `Foundation.tbd` and the Swift interfaces, every
link resolving inside the SDK, and no executable Mach-O. Setting up a
toolchain fetches the newest SDK its Command Line Tools read when none of
the installed ones fits.

To fetch one by hand:

```sh
git clone --depth 1 --single-branch --branch sdk/iPhoneOS18.5 \
    https://github.com/owngoal-dev/iOS-SDKs.git iOS-SDK-18.5
```
