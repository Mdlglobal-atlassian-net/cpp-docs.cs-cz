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
ms.openlocfilehash: d2deaf7b3e248dd1269d9f04037c9d38651a5b56
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649706"
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

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)