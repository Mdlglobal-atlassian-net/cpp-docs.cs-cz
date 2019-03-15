---
title: /bigobj (Zvýšit počet oddílů v souboru .Obj)
ms.date: 11/04/2016
f1_keywords:
- /bigobj
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
ms.openlocfilehash: a9685834fc3e1de246c9d9d60d206538b744ce3e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809857"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Zvýšit počet oddílů v souboru .Obj)

**/ bigobj** zvyšuje počet oddílů, které mohou obsahovat soubor objektu.

## <a name="syntax"></a>Syntaxe

```
/bigobj
```

## <a name="remarks"></a>Poznámky

Ve výchozím objektový soubor může obsahovat až 65 536 (2 ^ 16) adresovatelných sekcí. To platí bez ohledu na to, která Cílová platforma je zvolena. **/ bigobj** zvyšuje kapacitu této adresy na 4 294 967 296 (2 ^ 32).

Většina modulů nikdy nevygeneruje soubor .obj, který obsahuje více než 65 536 částí. Nicméně počítačem generovaný kód nebo kód, který značně používá knihovny šablon může vyžadovat soubory .obj, které mohou obsahovat další oddíly. **/ bigobj** je povolené ve výchozím nastavení v projektech univerzální platformy Windows (UPW), protože počítačem generovaný kód XAML obsahuje velký počet záhlaví. Pokud zakážete tuto možnost na projekt aplikace UPW budete pravděpodobně dojde k chybě kompilátoru C1128.

Linkers, které byly dodány před Visual C++ 2005 nelze číst soubory .obj, které byly vytvořeny s **/bigobj**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
