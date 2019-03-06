---
title: /STUB (název souboru zástupného kódu MS-DOS)
ms.date: 11/04/2016
f1_keywords:
- /stub
- VC.Project.VCLinkerTool.DosStub
helpviewer_keywords:
- Win32 [C++], attaching MS-DOS stub program
- STUB linker option
- MS-DOS stub file name linker option
- /STUB linker option
- Windows API [C++], attaching MS-DOS stub program
- -STUB linker option
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
ms.openlocfilehash: d349151654d9699bcf00aa3848798acb5104ba53
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421542"
---
# <a name="stub-ms-dos-stub-file-name"></a>/STUB (název souboru zástupného kódu MS-DOS)

```
/STUB:filename
```

## <a name="arguments"></a>Arguments

*Název souboru*<br/>
Aplikace zástupného kódu MS-DOS.

## <a name="remarks"></a>Poznámky

/ Stub připojí k programu Win32 zástupný program MS-DOS.

Program zástupné procedury je vyvolána, pokud soubor je spuštěn v systému MS-DOS. Obvykle se zobrazí odpovídající zprávu; libovolné platné zástupného kódu MS-DOS aplikace však může být program zástupné procedury.

Zadejte *filename* pro zástupný program za dvojtečkou (:) na příkazovém řádku. Linker zkontroluje *filename* a vydává chybovou zprávu, pokud soubor není spustitelný soubor. Program musí být soubor s příponou .exe; .com soubor není platný pro program zástupné procedury.

Pokud tato možnost se nepoužívá, linker připojí výchozí program zástupnou proceduru, která vydává se následující zpráva:

```
This program cannot be run in MS-DOS mode.
```

Při sestavování ovladač virtuálního zařízení *filename* umožňuje uživateli zadat název souboru, který obsahuje strukturu IMAGE_DOS_HEADER (definované v WINNT. H) pro použití v VXD, a ne výchozí záhlaví.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
