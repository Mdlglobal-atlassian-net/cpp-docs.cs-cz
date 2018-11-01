---
title: Optimalizace kódu
ms.date: 12/28/2017
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
ms.openlocfilehash: d490bd704c53a160ee36dea0fd24a52211bfdc37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525512"
---
# <a name="optimizing-your-code"></a>Optimalizace kódu

Optimalizace spustitelný soubor, můžete dosáhnout rovnováhy mezi rychlostí provádění rychlé a velikost malý kód. Toto téma popisuje některé mechanismy, které poskytuje jazyk Visual C++ pro optimalizaci kódu.

## <a name="language-features"></a>Jazykové funkce

Následující témata popisují některé optimalizace funkce v jazyce C/C++.

[Direktivy pragma a klíčová slova pro optimalizaci](../../build/reference/optimization-pragmas-and-keywords.md)<br/>
Seznam klíčová slova a pragmas, můžete použít ve vašem kódu pro zlepšení výkonu.

[Možnosti kompilátoru uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md)<br/>
Seznam **/O** – možnosti kompilátoru, které určují velikost rychlost nebo kód spuštění.

[Deklarátor odkazu r-hodnoty: &&](../../cpp/rvalue-reference-declarator-amp-amp.md)<br/>
Odkazy rvalue podporují implementaci *sémantiky přesunutí*. Pokud přesunutí sémantiky se používají k implementaci knihovny šablon, výkon aplikace, které používají tyto šablony může výrazně zlepšit.

### <a name="the-optimize-pragma"></a>Optimize – Direktiva pragma

Pokud optimalizované část kódu způsobí, že chyby nebo zpomalení, můžete použít [optimalizovat](../../preprocessor/optimize.md) – Direktiva pragma, chcete-li vypnout optimalizaci pro tuto část.

Uvést kód mezi dvěma direktiv pragma, jak je znázorněno zde:

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>Postupy pro programování

Můžete si všimnout zpráv dalších upozornění při kompilaci kódu pomocí optimalizace. Toto chování je očekávané, protože některá upozornění se týkají jenom optimalizovaný kód. Mnoho problémů optimalizace můžete vyhnout, pokud věnujte pozornost těchto upozornění.

Optimalizace programu pro rychlost paradoxically, může způsobit kód poběží pomaleji. Je to proto, že některé optimalizací pro rychlost zvýšit velikost kódu. Například vkládání funkcí eliminuje režijní náklady volání funkce. Nicméně vkládání příliš mnoho kódu by mohlo způsobit nepoužitelnost program tak velká, že číslo stránky virtuální paměti chyb zvyšuje. Proto rychlost získaných během volání funkce vyloučení může dojít ke ztrátě k záměně paměti.

Následující témata popisují funkční programovací postupy.

[Tipy pro zlepšení časově kritického kódu](../../build/reference/tips-for-improving-time-critical-code.md)<br/>
Lepší kódování techniky může přinést lepší výkon. Toto téma navrhuje kódování techniky, které vám umožňují Ujistěte se, že uspokojivě provádět náročné části kódu.

[Doporučené postupy optimalizace](../../build/reference/optimization-best-practices.md)<br/>
Obsahuje obecné pokyny o optimálním optimalizovat výkon své aplikace.

## <a name="debugging-optimized-code"></a>Ladění optimalizovaného kódu

Protože optimalizace může změnit kód vytvořený kompilátorem, doporučujeme ladit aplikaci a měřila svou výkonnost a optimalizujte váš kód.

Následující témata obsahují základní informace o tom, jak ladit.

- [Ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [Běžné problémy při vytváření sestavení pro vydání](../../build/reference/common-problems-when-creating-a-release-build.md)

Rozšířené informace o ladění naleznete v následujících tématech.

- [Postupy: Ladění optimalizovaného kódu](/visualstudio/debugger/how-to-debug-optimized-code)

- [Proč čísla s plovoucí desetinnou čárkou můžou ztratit přesnost](../../build/reference/why-floating-point-numbers-may-lose-precision.md)

Následující témata obsahují informace o tom, jak optimalizovat vytváření, načítání a spouštění vašeho kódu.

- [Zvýšení propustnosti kompilátoru](../../build/reference/improving-compiler-throughput.md)

- [Použití názvu funkce bez závorek nevygeneruje žádný kód](../../build/reference/using-function-name-without-parens-produces-no-code.md)

- [Optimalizace vloženého sestavení](../../assembler/inline/optimizing-inline-assembly.md)

- [Zadání optimalizace kompilátoru pro projekty ATL](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [Jaké optimalizační techniky mám použít ke zlepšení výkonu klientské aplikace při načítání?](../../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](../../build/reference/c-cpp-building-reference.md)
