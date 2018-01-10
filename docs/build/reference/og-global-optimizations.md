---
title: "-Og (globální optimalizace) | Microsoft Docs"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
dev_langs: C++
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 196e89a958ce49bf5e0087d98d2f40ada210cc87
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="og-global-optimizations"></a>/Og (globální optimalizace)

Zastaralé Poskytuje místní a globální optimalizace, automatické registrace přidělení a cykly optimalizace. Doporučujeme použít buď [/O1 (minimalizovat velikost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) nebo [/O2 (maximalizovat rychlost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) místo.

## <a name="syntax"></a>Syntaxe

> /Og

## <a name="remarks"></a>Poznámky

**/Og** je zastaralý. Tyto optimalizace jsou nyní obecně povolené ve výchozím nastavení. Další informace o optimalizace najdete v tématu [/O1, / O2 (velikost minimalizovat, maximalizovat rychlost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) nebo [/Ox (Povolit nejvíce rychlost optimalizace)](../../build/reference/ox-full-optimization.md).

Nejsou k dispozici v následujících optimalizace **/Og**:

- Místní a globální eliminace společných dílčích výrazů

     Hodnota běžné dílčím výrazu tato optimalizace je vypočítána jednou. V následujícím příkladu Pokud hodnoty `b` a `c` neměňte mezi tři výrazy, kompilátor můžete přiřadit výpočtu `b + c` dočasné proměnné a nahraďte proměnnou pro `b + c`:

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

     Pro místní běžné dílčím výrazu optimalizace kompilátoru prověří krátké sekcí kódu pro běžné podvýrazy. Pro globální běžné dílčím výrazu optimalizace kompilátoru vyhledá celý funkce pro běžné podvýrazy.

- Automatické přidělení registru

     Tato optimalizace umožňuje kompilátoru často používané proměnné a podvýrazy v registrech; `register` – klíčové slovo je ignorována.

- Optimalizace smyčky

     Tato optimalizace odebere invariantní podvýrazy z textu smyčku. Smyčky optimální obsahuje pouze výrazy, jejichž hodnoty změnit prostřednictvím každé spuštění smyčky. V následujícím příkladu výraz `x + y` nezmění do těla smyčky:

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

     Po optimalizace `x + y` se počítá jednou místo pokaždé, když se spustí smyčka:

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

     Optimalizace smyčky je mnohem efektivnější, pokud kompilátor můžete předpokládat žádné aliasy, které nastavíte s [__restrict](../../cpp/extension-restrict.md), [noalias](../../cpp/noalias.md), nebo [omezit](../../cpp/restrict.md).

    > [!NOTE]
    > Můžete povolit nebo zakázat globální optimalizace na jednotlivých pomocí funkcí pomocí `optimize` – Direktiva pragma společně s `g` možnost.

 Související informace najdete v tématu [/Oi (Generovat vnitřní funkce)](../../build/reference/oi-generate-intrinsic-functions.md) a [/Ox (Povolit nejvíce rychlost optimalizace)](../../build/reference/ox-full-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte **C/C++** složky.

1. Klikněte **příkazového řádku** stránku vlastností.

1. Zadejte možnost kompilátoru v **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[/O možnosti (Optimalizace kódu)](../../build/reference/o-options-optimize-code.md)

[Možnosti kompilátoru](../../build/reference/compiler-options.md)

[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)