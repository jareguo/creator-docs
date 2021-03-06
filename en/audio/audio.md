# Audio playback

- Audio loading method: [Audio resource](../asset-workflow/audio-asset.md)

## Use AudioSource component

1. Create an empty node
2. In this empty node, add an `other component -> AudioSource`
3. Add audioSource to script:

```js
cc.Class({
    properties: {
        audioSource: {
            type: cc.AudioSource,
            default: null
        },
    },
    play: function () {
        this.audioSource.play();
    },
    pause: function () {
        this.audioSource.pause();
    },
});
```

## Use AudioEngine

1. Defines a audioClip resource object within the script
2. Use cc.audioEngine.play (audio, loop, volume);

```js
cc.Class({
    properties: {
        audio: {
            default: null,
            type: cc.AudioClip
        }
    },

    onLoad: function () {
        this.current = cc.audioEngine.play(this.audio, false, 1);
    },

    onDestroy: function () {
        cc.audioEngine.stop(this.current);
    }
});
```

Audio needs an AudioClip object, not url. So we recommend avoiding url, try to use audioClip as much as possible to replace url.
