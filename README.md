Send coordinates from eye tracker to chrome extension. Currently uses lightly filtered gaze data settings (as opposed to unfiltered gaze or fixation data). Most of this app is the MinimalGazeDataStream example from the Tobii SDK (they have some [documentation](http://developer.tobii.com/c-sample-walk-minimalgazedatastream/) for this example in particular on their website). Additionally on startup it initializes a websocket server for the chrome extension to connect to. Once connected it builds a JSON string out of the coordinates and sends it over the websocket in the OnGazeDataEvent handler.

Building:

Depends on [websocketpp](https://github.com/zaphoyd/websocketpp) (which depends on [Boost](http://www.boost.org/)) and the [Tobii SDK](http://developer.tobii.com/eyex-sdk/c-cplusplus/)
The websocketpp documentation says it can depend on C++11 STL or Boost, I built using Boost (which itself needs to be [built](http://www.boost.org/doc/libs/1_64_0/more/getting_started/windows.html#simplified-build-from-source)) and Visual Studio. Doing so required adding the root websocketpp and boost directories, and the tobii sdk\include directory to includes (Configuration Properties > C/C++ > General > Additional Include Diretories). Also adding the boost libs (boost root\stage\lib) and tobii libs (tobii sdk\lib\x86) to libraries (Configuration Properties > Linker > General > Additional Library Dependencies).

Running the exe requires the Tobii.EyeX.Client.dll file. Presumably it can be added to an environment varaible/path, I just had it in the same folder as the exe.

## Meta comments

This is mostly tutorial/example code with some websockets jammed in. Doesn't do much but it did what it needed to.
