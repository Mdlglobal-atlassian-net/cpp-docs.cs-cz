---
title: /bigobj (Zvýšit počet oddílů v souboru .Obj)
ms.date: 03/26/2019
f1_keywords:
- /bigobj
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
ms.openlocfilehash: 30c02c72496e3bb91da3b39e1870f1dc5a2c040a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493104"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Zvýšit počet oddílů v souboru .Obj)

**/bigobj** zvyšuje počet oddílů, které může soubor objektu obsahovat.

## <a name="syntax"></a>Syntaxe

> **/bigobj**

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení může soubor objektu obsahovat až 65 279 (téměř 2 ^ 16) adresované oddíly. Toto omezení platí bez ohledu na to, která cílová platforma je určena. **/bigobj** zvyšuje kapacitu této kapacity na 4 294 967 296 (2 ^ 32).

Většina modulů nikdy negeneruje soubor. obj, který obsahuje více než 65 279 oddílů. Nicméně strojově generovaný kód nebo kód, který vytváří těžké použití knihoven šablon, může vyžadovat soubory. obj, které mohou obsahovat další oddíly. **/bigobj** je ve výchozím nastavení povolená v projektech Univerzální platforma Windows (UWP), protože strojově GENEROVANÝ kód XAML obsahuje velký počet hlaviček. Pokud tuto možnost zakážete v projektu aplikace pro UWP, váš kód může generovat chybu kompilátoru C1128.

Informace o formátu souboru objektu PE-COFF naleznete v dokumentaci k systému Windows ve [formátu PE](/windows/win32/debug/pe-format) .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností **Konfigurace** > **C/C++**  > **příkazový řádek** .

1. Do pole **Další možnosti** zadejte možnost kompilátoru **/bigobj** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
