# bubu-followers

This is a meta-bundle for [NodeCG](http://github.com/nodecg/nodecg). It doesn't
provide any display functionality on its own, but it emits events for
new followers, and provides a Replicant variable for the latest follower
for other bundles to use.

## Dependencies

* NodeJS 4.x
* NodeCG 0.6.x
* [lfg-twitchapi](https://github.com/SupportClass/lfg-twitchapi)

## Installation

1. Install to `nodecg/bundles/bubu-followers`.
2. Configure [lfg-twitchapi](https://github.com/SupportClass/lfg-twitchapi)

## Usage
This bundle emits the `follower` event for a new follower, and registers the
`latestFollower` replicant for the latest follower. These have a payload
consisting of the [Twitch API Follower object](https://github.com/justintv/Twitch-API/blob/master/v3_resources/follows.md#get-usersuserfollowschannels).

### Example

```javascript
nodecg.on('follower', function(follower) {
  console.log(follower.user.display_name);
});
```

```javascript
var latestFollower = nodecg.Replicant('latestFollower')
latestFollwer.on('change', function(oldVal, newVal) {
  console.log(newVal.user.display_name);
})
```

## License
This project is licensed under the [MIT License](LICENSE)
