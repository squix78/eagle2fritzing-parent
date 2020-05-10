# eagle2fritzing-parent
Parent project for converting Eagle brd files to fritzing parts

## Dependencies
* Autodesk Eagle must be installed
* XCode
* Homebrew

## How to for Mac OS X

Clone this project with the submodules:
```
git clone --recurse-submodules https://github.com/squix78/eagle2fritzing-parent
```

Install qt libraries:
```
brew install qt
cd eagle2fritzing/brd2svg
qmake -spec macx-clang brd2svg.pro
make
```

Modify run.sh. EXEC has to point to your installation of Eagle CAD. WORKPATH is a temporary folder where you can manipulate intermidate products. And Documents/Fritzing is where Fritzing stores the parts.
```
# Location of EAGLE executable:
EXEC=/Applications/EAGLE-9.5.2/eagle.app/Contents/MacOS/eagle 

# Default brd2svg working path (override by passing argument to this script):
WORKPATH=~/Desktop/FritzingTest

# Converted parts will be copied here for testing w/Fritzing:
TESTPATH=~/Documents/Fritzing
```

Now make sure that FritzingTest/brds exists:

```
mkdir -p ~/Desktop/FritzingTest/brds
```
and put your Eagle CAD board file(s) there.

Now (while still in the brd2svg folder run:
```
./run.sh
```
This will create some new folders and files for each of your *.brd files:

```
FritzingTest
|-- brds 
|-- bins
|-- parts
    |-- contrib
    |-- svg
        |-- contrib
            |-- breadboard
            |-- pcb
            |-- schematic
            |-- icon
 |-- params
 |-- xml
 |-- descriptions
 ```
 
 Now you might have to do some manual corrections:
 * Open the file(s) under FritzingTest/params and change
   * Author
   * Url
   * Description
   * Tags
   * Family
   * Board color
   
In the default generated file the family attribute is commented out. My fritzing version seems to have problems if that attribute is not present. Once you have changed the attributes to your likings run the script again:
```
./run.sh
```
This will re-create the svgs with your new board color (in case you changed it) and also update the fritzing files. Now check the svg files with InkScape, Affinitiy Designer, Illustrator etc. Open Fritzing and search for your new part. You might have to restart fritzing if it was already open during the script run.

If you are not happy with the results right click on the part icon and choose "Edit part (new part editor)". There you can change meta information, map connectors etc.

Once you are happy with the results close the editor and choose "Export part...". Then share with your community!
