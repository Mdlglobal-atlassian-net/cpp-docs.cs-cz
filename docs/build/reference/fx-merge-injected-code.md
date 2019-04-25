---
title: /Fx (sloučení vloženého kódu)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExpandAttributedSource
- /Fx
- VC.Project.VCCLCompilerTool.ExpandAttributedSource
helpviewer_keywords:
- Fx compiler option [C++]
- -Fx compiler option [C++]
- injected code
- merging injected code
- /Fx compiler option [C++]
ms.assetid: 14f0e301-3bab-45a3-bbdf-e7ce66f20560
ms.openlocfilehash: f1a266eee4edc524fbbe49bdef31a8235f62bd3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292299"
---
# <a name="fx-merge-injected-code"></a>/Fx (sloučení vloženého kódu)

Vytvoří kopii každý zdrojový soubor s kódem sloučit do zdroje.

## <a name="syntax"></a>Syntaxe

```
/Fx
```

## <a name="remarks"></a>Poznámky

K rozlišení sloučené zdrojový soubor z původního zdrojového souboru **/Fx** přidá rozšíření .mrg mezi název souboru a příponu souboru. Například soubor s názvem MyCode.cpp obsahující kódu s atributy a vytvořené s **/Fx** vytvoří soubor s názvem MyCode.mrg.cpp obsahující následující kód:

```
//+++ Start Injected Code
[no_injected_text(true)];      // Suppress injected text, it has
                               // already been injected
#pragma warning(disable: 4543) // Suppress warnings about skipping
                               // injected text
#pragma warning(disable: 4199) // Suppress warnings from attribute
                               // providers
//--- End Injected Code
```

V souboru .mrg bude kód, který se vloží z důvodu atribut oddělených následujícím způsobem:

```
//+++ Start Injected Code
...
//--- End Injected Code
```

[No_injected_text –](../../windows/no-injected-text.md) atribut je vložený v souboru .mrg, což umožňuje pro kompilaci souboru .mrg bez textu se reinjected.

Byste měli vědět, že .mrg zdrojový soubor je určen jako reprezentace zdrojového kódu vloží kompilátorem. Soubor .mrg nemusí kompilaci či spuštění přesně jako původní zdrojový soubor.

Makra nejsou v souboru .mrg rozbaleny.

Pokud váš program zahrnuje soubor hlaviček, který používá vložený kód **/Fx** vygeneruje. mrg.h souboru pro tuto hlavičku. **/FX** neobsahuje není sloučení souborů, které nepoužívají vloženého kódu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **výstupní soubory** stránku vlastností.

1. Upravit **rozbalit zdroj s atributy** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExpandAttributedSource%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti výstupního souboru (/F)](output-file-f-options.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
