#Basics

###Variables
* $JOB: directory that project is based on
* $HIP: where current houdini file is saved

###Hotkeys
* w - wireframe / shaded toggle

* e - scale
* r - rotate
* t - move / translate
* enter - handle tool
* y - circulate through handle tools

* " - change pivot
* esc - view tool
* space - temporarily enable view tool

* tab - tool menu

* cmd + b - maximize pane

* selection
    - 1: object
    - 2: point 
    - 3: edges
    - 4: primitives
    - 5: vertices

    - a + mmb edge: select edge loop

###Transformation tools
* Houdini's default translation is in object coordinates. To toggle between object and world: right click >> align handle >> world.

* Increase size of transformation handles using multiply/divide keys: * or /

###Handle Tool
A tool that gives access in viewport to specialized functionality of whatever tool is being used.

###View tool
* mouse buttons
    - left: tumble
    - middle: pan
    - right: dolly

* h - home
* f - frame selected object

* camera view
    - 1: perspective
    - 2: top
    - 3: front
    - 4: right
    - 5: uv

###Viewport
* cmd+1 : single view
* cmd+2 : four views

###Network View
* i : move *in* to selected node
* u : move out of node, *up* one level

* p : toggle parameters window
* d : toggle display options

* mmb : information about clicked node

###Contexts
* objs
* ch (chops, channel operators)
    - manipulating raw data (movement, audio...)
* img (images, cops, compositing operators)
* out (rops, rendering operators)
    - allow setup of various renders / exports
* shop (shading operators)
* vex (vops, vex operators)

* pops (particle operators)
* dops (dynamic operators)

###Scene scale
* Edit -> Preferences -> Hip File Options >>> to view units in scene
* The scale affects pipeline and simulation results!

###Parameter view
* Value Ladder -> MMB on any value

###Object Ghosting
* "selected" object in Houdini is the object on the network view
* Can select between show / ghost / hide other objects in the top bar of scene view



