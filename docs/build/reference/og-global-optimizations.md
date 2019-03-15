---
title: /Og (globální optimalizace)
ms.date: 09/22/2017
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
ms.openlocfilehash: 5e45273b6b609f1bf78504a519c1fb98e2147f76
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818528"
---
# <a name="og-global-optimizations"></a>/Og (globální optimalizace)

Zastaralé Poskytuje místní a globální optimalizace, automatické registrace přidělení a optimalizace smyčky. Doporučujeme použít buď [/O1 (minimalizaci velikosti)](o1-o2-minimize-size-maximize-speed.md) nebo [/O2 (maximalizovat rychlost)](o1-o2-minimize-size-maximize-speed.md) místo.

## <a name="syntax"></a>Syntaxe

> /Og

## <a name="remarks"></a>Poznámky

**/Og** je zastaralý. Tyto optimalizace jsou nyní obecně k dispozici ve výchozím nastavení. Další informace o optimalizaci, naleznete v tématu [/O1, / O2 (minimalizovat velikost, maximální rychlost)](o1-o2-minimize-size-maximize-speed.md) nebo [/Ox (povolení většina optimalizací pro rychlost)](ox-full-optimization.md).

Tyto optimalizace jsou k dispozici v rámci **/og**:

- Místní a globální eliminace společných dílčích

   Hodnota běžné dílčí výraz tato optimalizace se vypočítává jednou. V následujícím příkladu Pokud hodnoty `b` a `c` neměňte mezi tři výrazy, kompilátor může přiřadit výpočtu `b + c` k dočasné proměnné a nahraďte proměnnou pro `b + c`:

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

   Pro místní běžné dílčí výraz optimalizace Kompilátor zkontroluje krátký části kódu pro běžné dílčích výrazů. Globální optimalizace běžné dílčí výraz kompilátor vyhledá celé funkce pro běžné dílčích výrazů.

- Automatické přidělení registru

   Tyto optimalizace umožňuje kompilátoru vytvořit úložiště často používaných proměnných a podvýrazů v registrech; `register` – klíčové slovo se ignoruje.

- Optimalizace smyčky

   Tato optimalizace odebere invariantní dílčích výrazů v těle smyčky. Optimální smyčka obsahuje pouze výrazy, jejichž hodnoty se mění prostřednictvím každým provedením smyčky. V následujícím příkladu výraz `x + y` nezmění v těle smyčky:

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

   Po optimalizaci `x + y` se počítá po ne při každém provedení smyčky je:

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

   Optimalizace smyčky je mnohem efektivnější, pokud kompilátor může převzít není zavedení aliasů, které jste nastavili [kvalifikátor __restrict](../../cpp/extension-restrict.md), [noalias](../../cpp/noalias.md), nebo [omezit](../../cpp/restrict.md).

   > [!NOTE]
   > Můžete povolit nebo zakázat globální optimalizaci na jednotlivých podle funkcí pomocí `optimize` – Direktiva pragma spolu s `g` možnost.

Související informace naleznete v tématu [/Oi (Generovat vnitřní funkce)](oi-generate-intrinsic-functions.md) a [/Ox (povolení většina optimalizací pro rychlost)](ox-full-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadáním možnosti kompilátoru v **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
