# AR
목표: Swift + SwiftUI + USD 를 이용한 AR앱 제작

### 참고
- 이 리포지터리는 Blender를 이용해서 AR에 활용 가능한 `.usdz` 생성 및 파이프라인 제작에 목표를 두고 있습니다.

### Xcode 셋팅
usdz_converter 명령어를 터미널에서 사용하기 위해서는 몇가지 설정이 필요합니다.

Xcode를 실행하고 상단메뉴에서 Xcode > Preferences > Locations 탭
Command Line Tools: Xcode 10.3(10GB) 로 설정을 바꾸어줍니다.

터미널을 실행하고 아래 명령어가 작동되는지 체크합니다.
```bash
$ xcrun usdz_converter
```

아래처럼 출력되면 정상입니다.
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

### .usdz 생성
Blender에서 `.obj` 이외에 `.abc`포멧을 export 할 수 있습니다.
텍스쳐로 사용하는 `.png` 이미지는 압축해서 사용하지 말아주세요. 알파채널을 포함하여 작업물의 결과를 엉망으로 만들어 버립니다.
데이터가 준비가 다 되면 usdz_converter 명령을 이용해서 `.usdz`를 만들 수 있습니다.

아래는 `.obj`와 `.png` 텍스쳐를 이용해서 `.usdz`를 만드는 예 입니다.
```bash
$ xcrun usdz_converter input.obj output.usdz
-g CubeMesh
-normal_map normal.png
-color_map color.png
-roughness_map roughness.png
-metallic_map metal.png
```

### 응 용
`.usdz` 파일을 링크하면 사파리, 아이폰에서 파일을 인식하여 AR 시뮬레이션을 실험해 볼 수 있습니다.

[아이폰에서 클릭](https://www.apple.com/105/media/us/iphone-11-pro/2019/3bd902e4-0752-4ac1-95f8-6225c32aec6d/ar/iphone-11-pro.usdz)

### Xcode Project 셋팅
- Root문서 선택 > Signing&Capabilities > Team 선택
- 아이폰 > 설정 > 일반 > 기기관리 > 개발자앱 선택 > 개발자앱 확인
