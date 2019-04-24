---
title: /Zg (Generovat prototypy funkcí)
ms.date: 11/04/2016
f1_keywords:
- /zg
helpviewer_keywords:
- Zg compiler option [C++]
- /Zg compiler option [C++]
- function prototypes, generate function prototypes compiler option
- -Zg compiler option [C++]
- generate function prototypes compiler option
ms.assetid: c8df1b46-24ff-46f2-8356-e0a144b21dd2
ms.openlocfilehash: 684174cf46e644c22e072e3fa60f75f9434c7e54
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315895"
---
# <a name="zg-generate-function-prototypes"></a>/Zg (Generovat prototypy funkcí)

Odebrat. Vytvoří prototyp pro každou funkci definovanou ve zdrojovém souboru, ale ne kompilaci zdrojového souboru.

## <a name="syntax"></a>Syntaxe

```
/Zg
```

## <a name="remarks"></a>Poznámky

Tato možnost kompilátoru je již k dispozici. Byl odebrán v sadě Visual C++ 2015. Tato stránka zůstane uživatelům starší verze jazyka Visual C++.

Prototyp funkce obsahuje návratový typ funkce a seznam argumentů typu. Seznam argumentů typu se vytvoří z typy formálních parametrů funkce. Všechny prototypy již existuje ve zdrojovém souboru jsou ignorovány.

Seznam prototypy jsou zapsány do standardního výstupu. Tento seznam vám můžou pomoct ověřit, že jsou kompatibilní skutečné argumenty a formální parametry funkce. Uložení seznamu podle přesměrovat standardní výstup do souboru. Můžete použít **#include** k vytvoření seznamu prototypy části zdrojového souboru. To způsobí, že kompilátor provedení kontroly typů argumentů.

Pokud používáte **/Zg** možnost a váš program obsahuje formální parametry, které mají struktura, výčtu, nebo typ union (nebo ukazatele na tyto typy), prohlášení o každé, výčtu, typ struktury nebo jednoty musí mít značku (název). V následujícím příkladu je název značky `MyStruct`.

```C
// Zg_compiler_option.c
// compile with: /Zg
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```

**/Zg** možnost se přestala nabízet v sadě Visual Studio 2005 a byla odebrána v sadě Visual Studio 2015. Kompilátor MSVC odebrala podpora pro starší kód C-style. Seznam zastaralých kompilátoru možnosti najdete v tématu **zastaralé a odebrat možnosti kompilátoru** v [možnosti kompilátoru seřazené podle kategorie](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
