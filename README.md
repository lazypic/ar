# ar

### Xcode 셋팅

Xcode를 실행하고 상단메뉴에서 Xcode > Preferences > Locations 탭
Command Line Tools: Xcode 10.3(10GB) 로 설정을 바꾼다.

터미널에서 아래 명령어가 작동되는지 체크한다.
```bash
$ xcrun usdz_converter
```

아래처럼 출력되면 정상이다.
```
usdz_converter
Version: 1.009

2019-09-14 19:11:01.470 usdz_converter[60114:15377298]


USAGE:
<inFilePath> <outFilePath> [options...]
	Options:
                -g groupName [groupNames ...]       Apply subsequent material properties to the named group(s).
                -m materialName [materialNames ...] Apply subsequent material properties to the named material(s).
                -h                                  Display help.
                -a                                  Generate a .usda intermediate file.  Default is .usdc.
                -l                                  Leave the intermediate .usd file in the source folder.
                -v                                  Verbose output.
                -f                    filePath      Read commands from a file.
                -texCoordSet          set           The name of the texturemap coordinate set to use if multiple exist (no quotes).
                -opacity              o             Floating point value 0.0 ... 1.0
                -color_map            filePath
                -normal_map           filePath
                -emissive_map         filePath
                -metallic_map         filePath
                -roughness_map        filePath
                -ao_map               filePath
                -color_default        r g b a        Floating point values 0.0 ... 1.0
                -normal_default       r g b a
                -emissive_default     r g b a
                -metallic_default     r g b a
                -roughness_default    r g b a
                -ao_default           r g b a

(*) Specify infield only with -v (Verbose) to display group information.
(*) '#' in the first character position of a line in a command file interprets the line as a comment.



asset_validation: error: No Input file specified
```

### 데이터 Publish
.obj 이외에 .abc도 지원한다.

```bash
$ xcrun usdz_converter input.obj output.usdz
-g CubeMesh
-normal_map normal.png
-color_map color.png
-roughness_map roughness.png
-metallic_map metal.png
```

### 응용
[아이폰에서 클릭](https://www.apple.com/105/media/us/iphone-11-pro/2019/3bd902e4-0752-4ac1-95f8-6225c32aec6d/ar/iphone-11-pro.usdz)
