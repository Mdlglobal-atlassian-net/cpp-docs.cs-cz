---
title: /OUT (Název výstupního souboru)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
ms.openlocfilehash: be5fe929bdcf52be19955a5bc2d7aa093e194f45
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812418"
---
# <a name="out-output-file-name"></a>/OUT (Název výstupního souboru)

```
/OUT:filename
```

## <a name="arguments"></a>Arguments

*Název souboru*<br/>
Uživatelem zadaný název výstupního souboru. Nahradí výchozí název.

## <a name="remarks"></a>Poznámky

Parametr/out přepisuje výchozí název a umístění programu, který vytvoří linker.

Ve výchozím nastavení linker tvoří název souboru pomocí základní název první zadaný soubor .obj a příslušné rozšíření (.exe nebo .dll).

Tato možnost Základní název výchozí knihovny .mapfile nebo import. Podrobnosti najdete v tématu [generovat soubor mapování](map-generate-mapfile.md) (/ MAP) a [/IMPLIB](implib-name-import-library.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **Obecné** stránku vlastností.

1. Upravit **výstupní soubor** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
