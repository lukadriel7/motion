# Transition Properties

Transition properties are represented by an object containing all transition parameters of a variant.

They are one of the two parts that compose a [**Variant**](/variants), with [**Motion Properties**](/motion-properties).

## Orchestration

### Delay

You can specify a delay which will be added every time the transition is pushed.

```vue
<div
  v-motion
  :initial="{
    scale: 1,
  }"
  :enter="{
    scale: 2,
    transition: {
      delay: 1000,
    },
  }"
/>
```

##### _This animation will be throttled of 1 second._ ☝️

### Repeat

The native [**Popmotion Repeat**](https://popmotion.io/#quick-start-animation-animate-options-repeat) feature is supported.

Three parameters are available:

- `repeat` that is the number of times the animation will be repeated. Can be set to `Infinity`.

- `repeatDelay`, a duration in milliseconds to wait before repeating the animation.

- `repeatType` that supports `loop`, `mirror`, `reverse`. The default is `loop`.

```vue
<div
  v-motion
  :initial="{
    scale: 1,
  }"
  :enter="{
    scale: 2,
    transition: {
      repeat: Infinity,
      repeatType: 'mirror',
    },
  }"
/>
```

##### _Zboing!._ ☝️

## Transition Types

Two types of animations are supported.

For the most [**Common Animatable Properties**](https://github.com/vueuse/motion/blob/main/src/utils/defaults.ts#L43), it will uses generated spring transitions.

The rest of the properties might be using keyframes.

### Spring

Springs are used to create dynamic and natural animations.

It supports multiple parameters:

- `stiffness`

A higher stiffness will result in a snappier animation.

- `damping`

The opposite of stiffness. The lower it is relative to sitffness, the bouncier the animation will get.

- `mass`

The mass of the object, heavier objects will take longer to speed up and slow down.

### Keyframes

Keyframes ared used mainly for color related animations as springs are not designed for that.

It also works with numbers though.

It supports multiple parameters:

- `duration`

The duration of the animation, in milliseconds.

Defaults to `800`.

- `ease`

Supports multiples types:

- An easing name
- Array of easing names
- Easing function
- Array of easing
- A cubic bezier definition using a 4 numbers array

Supported easing names:

- **linear**
- **easeIn**, **easeOut**, **easeInOut**
- **circIn**, **circOut**, **circInOut**
- **backIn**, **backOut**, **backInOut**
- **anticipate**

## Per-key transition definition

Transition properties supports per-key transition definition.

It allows you to create complex animations without using the `apply` function.

To do so, you have to define key-specific transition inside your transition definition.

```vue
<div
  v-motion
  :initial="{
    y: 100,
    opacity: 0,
  }"
  :enter="{
    y: 0,
    opacity: 1,
    transition: {
      y: {
        delay: 1600,
      },
      opacity: {
        duration: 1600,
      },
    },
  }"
/>
```

##### _The `y` transition will start when the `opacity` one is over._ ☝️
