# eagle2fritzing-parent
Parent project for converting Eagle brd files to fritzing parts

## Dependencies
* Autodesk Eagle must be installed

## How to for Mac OS X

Clone this project with the submodules:
```
git clone --recurse-submodules https://github.com/squix78/eagle2fritzing-parent
```

Install qt libraries:
```
brew install qt
cd eagle2fritzing/brd2svg
qmake -spec macx-g++ brd2svg.pro
make
```

Modify run.sh:
```

```
