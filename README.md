# AlliewayAudio_MMFreebies
4MS MetaModule plugin build wrapper for AlliewayAudio_freebies VCVRack plugin

This is a [4MS MetaModule](https://metamodule.4ms.info/) build wrapper for the [AlliewayAudio_Freebies VCVRack plugin](https://github.com/AlliewayAudio/AlliewayAudio_Freebies), in order to build a .mmplugin binary of the [Chilly Cheese](https://library.vcvrack.com/AlliewayAudio_Freebies/chilly_cheese) module (itself a version of the [Whimiscal Raps Cold Mac](https://www.whimsicalraps.com/products/cold-mac) Eurorack module).

![Chilly Cheese on the MetaModule](/images/ChillyCheeseOnMetaModule.png?raw=true "Chilly Cheese on the MetaModule")


## Acknowledgements

Thanks to [Allie](https://github.com/AlliewayAudio) for giving me the OK to create this MetaModule port, and for creating the [AlliewayAudio_Freebies VCVRack plugin](https://github.com/AlliewayAudio/AlliewayAudio_Freebies).  Please note this MetaModule port is not technically supported by AlliewayAudio in any way.


Thanks also to Whimsical Raps for also OK'ing me to publish this build port - of - a - port of the [Mannequins Cold Mac](https://www.whimsicalraps.com/products/cold-mac) Eurorack hardware module.   From Eurorack analog awesomeness to VCVRack software plugin to Eurorack virtual digital module!   The MetaModule port is not officially endorsed or supported in any way by Whimical Raps.

## Build Instructions

> [!NOTE]
> Setup the build prequisites as described in the VCVRack plugin porting instructions in the 4MS [MetaModule Plugin SDK](https://github.com/4ms/metamodule-plugin-sdk) repo. 

Check this repo out into a ```<projects-dir>/AlliewayAudio_MMFreebies``` folder

Update the git submodule dependencies

```
cd <project-dir>
git submodule update --recursive
```	

then clone the MetaModule Plugin SDK:

```
cd <project-dir>
git clone https://github.com/4ms/metamodule-plugin-sdk --recursive
```

NB: If pulling latest commit of ```metamodule-plugin-sdk```, run:

```
cd <project-dir>/metamodule-plugin-sdk
git submodule update --recursive
```

Make sure you now have this folder structure:

```
<project-dir>/
  +- metamodule-plugin-sdk/
  +- AlliewayAudio_MMFreebies/
     +- AlliewayAudio_Freebies/
        +- src/
        +- res/
     +- assets/
     +- metamodule-plugins/   
```

To generate PNG image from SVG:

```
cd <project-dir>/metamodule-plugin-sdk
./scripts/SvgToPng.py --input ../AlliewayAudio_MMFreebies/AlliewayAudio_Freebies/res/ --output ../AlliewayAudio_MMFreebies/asset
```

To compile, and build:
```
cd AlliewayAudio_MMFreebies
cmake -B build -G Ninja -DTOOLCHAIN_BASE_DIR=<path-to-arm64-arm-none-eabi>/bin
cmake --build build

```

This will build a new ```<project-dir>/AlliewayAudio_MMFreebies/metamodule-plugins/AlliewayAudio_Freebies.mmplugin``` plugin install file.


