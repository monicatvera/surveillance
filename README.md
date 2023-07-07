# Kata surveillance
A well-known manufacturer of video surveillance systems has asked us to develop software for the prototype of a new innovative product that they are developing. It is a piece of equipment that has a motion sensor and a recorder. The motion sensor has an API with a single method that returns true when it detects that something has started to move and false when it doesn't. On the other hand, the recorder has two commands: one to start recording and another to stop recording.

Our task will be to design a controller that checks every second if the sensor is detecting movement and if so, we must tell the recorder to start recording, and if not, it must stop it. Recording should also stop in case of any unexpected sensor behavior.

The main limitation is that the manufacturer does not offer us the possibility of accessing the code of the sensor or the recorder, it seems that he does not want us to copy his magnificent idea. But at least it provides us with its public interfaces:

```TypeScript
interface MotionSensor {
    isDetectingMotion(): boolean;
}
```

```TypeScript
interface VideoRecorder {
    startRecording(): void;
    stopRecording(): void;
}
```

These interfaces are all we need, since the idea is to make use of doubles of these pieces to be able to test our controller.

## Test list
  In summary, the requirements that the controller that we have to design must meet are:
  - [x] Instructs the recorder to stop recording when the sensor does not detect movement.
  - [x] Tells the recorder to start recording when the sensor detects motion.
  - [x] Tells the recorder to stop recording when the sensor throws an unexpected error.
  - [x] Check the status of the motion sensor once a second.
