# Byte-Track Integration with Deepstream 7.1

This code is based on the [official code](https://github.com/ifzhang/ByteTrack).

Integrating Byte-Track C++ code with the Deepstream-7.1.

Features:
* Only support for DeepStream 7.1. For other verions, Change set(DS_ROOT_DIR /opt/nvidia/deepstream/deepstream-7.1) in CMAKE
.
* Support multi-streams
* The [memory leak issue](https://github.com/ifzhang/ByteTrack/issues/276) should be resolved.



## Build Instructions
```
$mkdir build && cd build

$cmake ..

$make ByteTracker
```

This will create ./lib/libByteTracker.so file which can be passed as the custom low level tracker library to deepstream.
To do so just add it to the folder 
```
/opt/nvidia/deepstream/deepstream/lib/
```

In your deepstream_app_config.txt add the tracker.
```
[tracker]
enable=1
tracker-width=640
tracker-height=384
gpu-id=0
ll-lib-file=//opt/nvidia/deepstream/deepstream/lib/libByteTracker.so
enable-batch-process=1
```



## References
1. [How to Implement a Custom Low-Level Tracker Library in Deepstream](https://docs.nvidia.com/metropolis/deepstream/dev-guide/text/DS_plugin_gst-nvtracker.html#how-to-implement-a-custom-low-level-tracker-library)
2. [Byte-Track](https://github.com/ifzhang/ByteTrack)
