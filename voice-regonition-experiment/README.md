
## JUAN's R&D SPACE

##  VOICE RECOGNITION

<details>
<summary><h4>React-Speech-Recognition</h4></summary>

## React-Speech-Recognition
A React hook that converts speech from the microphone to text and makes it available to your React components.

How it works
useSpeechRecognition is a React hook that gives a component access to a transcript of speech picked up from the user's microphone. SpeechRecognition manages the global state of the Web Speech API, exposing functions to turn the microphone on and off. Under the hood, it uses Web Speech API. Note that browser support for this API is currently limited, with Chrome having the best experience - see supported browsers for more information. This version requires React 16.8 so that React hooks can be used. If you're used to version 2.x of react-speech-recognition or want to use an older version of React, you can see the old README here. If you want to migrate to version 3.x, see the migration guide here. [npm link] (https://github.com/zihangdai/xlnet)

Installation
To install:
```sh
npm install --save react-speech-recognition
```
To import in your React code:
```sh
import SpeechRecognition, { useSpeechRecognition } from 'react-speech-recognition'
```
Basic Example
The most basic example of a component using this hook would be:
```sh
import React from 'react';
import SpeechRecognition, { useSpeechRecognition } from 'react-speech-recognition';

const Dictaphone = () => {
  const {
    transcript,
    listening,
    resetTranscript,
    browserSupportsSpeechRecognition
  } = useSpeechRecognition();

  if (!browserSupportsSpeechRecognition) {
    return <span>Browser doesn't support speech recognition.</span>;
  }

  return (
    <div>
      <p>Microphone: {listening ? 'on' : 'off'}</p>
      <button onClick={SpeechRecognition.startListening}>Start</button>
      <button onClick={SpeechRecognition.stopListening}>Stop</button>
      <button onClick={resetTranscript}>Reset</button>
      <p>{transcript}</p>
    </div>
  );
};
export default Dictaphone;
```
</details>

<details>
<summary><h4>Problem Encountered</h4></summary>

## Problem Encountered 1

Error occurred while rendering the code above using Next.js framework. According to Next.js documentation, this issue is caused by using a specific library or application code that is relying on something that could differ between pre-rendering and the browser. [Next.js documentation Link] (https://nextjs.org/docs/messages/react-hydration-error) In order to fix the problem, I added 'useEffect' and 'useState' hooks.

Added code snippets:
```sh
import { useEffect, useState } from 'react'
```
```sh
const [listening, setListening] = useState(false)
useEffect(() => setListening(true), [])
```

## Problem Encountered 2

By default, the microphone stop listening when the user stops speaking. This may be a problem for someone who want the microphone to listen continuously. The code snippet below can make the microphone to continue listening even after the user has stopped speaking.

```sh
const startListening = () => SpeechRecognition.startListening({ continuous: true });
```

# Problem Encountered 3

The microphone can pick up multiple languages including Korean. However, this presents an issue because when a user says "Hi" in English, it prints out "하이", which is Korean. As a result, it makes hard for a user to switch between speaking Korean and English.

![Captuer Image](https://google.com)

In order to solve this issue, the language is set to English for this project.


</details>


<details>
<summary><h4>Things to consider before implmenting</h4></summary>

A. Is there a better way to convert text to speech?
B. In terms of performance, there are better speech recognition tools such as the AudioGPT(Recently released).


Q. What is the API is not supported by a web browser?
A. As of 2021, the API is supported by all major web browsers except IE and Opera. No need to worry.




