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
ms.openlocfilehash: 46399dc0c1ff552b4fc963b686ac6aa6df8b6f71
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508712"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Zvýšit počet oddílů v souboru .Obj)

**/ bigobj** zvyšuje počet oddílů, které mohou obsahovat soubor objektu.

## <a name="syntax"></a>Syntaxe

> **/bigobj**

## <a name="remarks"></a>Poznámky

Ve výchozím objektový soubor může obsahovat až 65 279 (téměř 2 ^ 16) adresovatelných sekcí. Toto omezení platí bez ohledu na to, které se zaměřují platforma je zvolena. **/ bigobj** zvyšuje kapacitu této adresy na 4 294 967 296 (2 ^ 32).

Většina modulů nikdy nevygeneruje soubor .obj, který obsahuje více než 65,279 oddíly. Nicméně počítačem generovaný kód nebo kód, který značně používá knihovny šablon, může vyžadovat soubory .obj, které mohou obsahovat další oddíly. **/ bigobj** je povolené ve výchozím nastavení v projektech univerzální platformy Windows (UPW), protože počítačem generovaný kód XAML obsahuje velký počet záhlaví. Pokud zakážete tuto možnost na projekt aplikace UPW, váš kód může generovat chybě kompilátoru C1128.

Informace o formátu souboru objektu PE COFF najdete v tématu [formátu PE](/windows/desktop/debug/pe-format) v dokumentaci k Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Zadejte **/bigobj** – možnost kompilátoru v **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
