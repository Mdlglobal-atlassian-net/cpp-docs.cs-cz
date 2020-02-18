---
title: /PROFILE (profiler nástrojů výkonu)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: 678816ce455d2a982ff8218becd805a0b2cdd896
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416036"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (profiler nástrojů výkonu)

Vytvoří výstupní soubor, který se dá použít s profilerem Performance Tools.

## <a name="syntax"></a>Syntaxe

```
/PROFILE
```

## <a name="remarks"></a>Poznámky

/PROFILE implikuje následující možnosti linkeru:

- [/OPT: REF](opt-optimizations.md)

- /OPT:NOICF

- [/INCREMENTAL: NE](incremental-link-incrementally.md)

- [/FIXED: NE](fixed-fixed-base-address.md)

/PROFILE způsobí, že linker vygeneruje v imagi programu oddíl pro přemístění.  Oddíl přemístění umožňuje profileru transformovat image programu, aby získala data profilu.

**/Profile** je k dispozici pouze ve verzích Enterprise (vývoj týmu).  Další informace o tom, jak rychle, najdete v tématu [Analýza kóduC++ pro C/přehled](/cpp/code-quality/code-analysis-for-c-cpp-overview).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte uzel **Vlastnosti konfigurace** .

1. Rozbalte uzel **linker** .

1. Vyberte stránku vlastností **Upřesnit** .

1. Upravte vlastnost **Profile** .

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.

### <a name="to-set-this-linker-option-within-visual-studio-cmake-project"></a>Nastavení této možnosti linkeru v rámci projektu sady Visual Studio CMake

Projekt **cmake** neobsahuje **stránky vlastností**, Možnosti linkeru lze nastavit pomocí modifing souboru CMakeLists. txt.

1. Otevřete CMakeLists. txt v kořenovém adresáři projektu.

1. Níže přidejte kód. Podrobnosti najdete v tématu [odkazy cmake](https://cmake.org/cmake/help/v3.0/command/set_target_properties.html) .

1. Znovu sestavte své řešení.

```
SET_TARGET_PROPERTIES(${PROJECT_NAME} PROPERTIES LINK_FLAGS "/PROFILE")
```

## <a name="see-also"></a>Viz také

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)

