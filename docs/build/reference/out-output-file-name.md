---
title: -OUT (název výstupního souboru) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
dev_langs:
- C++
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c4bfc79a257424820bed5f784cb0a83daf016d5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725397"
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

Tato možnost Základní název výchozí knihovny .mapfile nebo import. Podrobnosti najdete v tématu [generovat soubor mapování](../../build/reference/map-generate-mapfile.md) (/ MAP) a [/IMPLIB](../../build/reference/implib-name-import-library.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **Obecné** stránku vlastností.

1. Upravit **výstupní soubor** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)