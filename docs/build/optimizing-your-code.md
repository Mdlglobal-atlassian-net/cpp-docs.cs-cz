---
title: Optimalizace kódu
ms.date: 04/23/2019
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
ms.openlocfilehash: 430ac9ef1b2946e511d04f7ce18bb0f20d727d75
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341119"
---
# <a name="optimizing-your-code"></a>Optimalizace kódu

Optimalizace spustitelný soubor, můžete dosáhnout rovnováhy mezi rychlostí provádění rychlé a velikost malý kód. Toto téma popisuje některé mechanismy, které poskytuje jazyk Visual C++ pro optimalizaci kódu.

## <a name="language-features"></a>Jazykové funkce

Následující témata popisují některé optimalizace funkce v jazyce C/C++.

[Optimalizace Pragmas a klíčových slov](optimization-pragmas-and-keywords.md) \
Seznam klíčová slova a pragmas, můžete použít ve vašem kódu pro zlepšení výkonu.

[Možnosti kompilátoru uvedené podle kategorie](reference/compiler-options-listed-by-category.md) \
Seznam **/O** – možnosti kompilátoru, které určují velikost rychlost nebo kód spuštění.

[Deklarátor odkazu hodnoty r: & &](../cpp/rvalue-reference-declarator-amp-amp.md) \
Odkazy rvalue podporují implementaci *sémantiky přesunutí*. Pokud přesunutí sémantiky se používají k implementaci knihovny šablon, výkon aplikace, které používají tyto šablony může výrazně zlepšit.

### <a name="the-optimize-pragma"></a>Optimize – Direktiva pragma

Pokud optimalizované část kódu způsobí, že chyby nebo zpomalení, můžete použít [optimalizovat](../preprocessor/optimize.md) – Direktiva pragma, chcete-li vypnout optimalizaci pro tuto část.

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

[Tipy pro zlepšení časově kritického kódu](tips-for-improving-time-critical-code.md) \
Lepší kódování techniky může přinést lepší výkon. Toto téma navrhuje kódování techniky, které vám umožňují Ujistěte se, že uspokojivě provádět náročné části kódu.

[Doporučené postupy optimalizace](optimization-best-practices.md) \
Obsahuje obecné pokyny o optimálním optimalizovat výkon své aplikace.

## <a name="debugging-optimized-code"></a>Ladění optimalizovaného kódu

Protože optimalizace může změnit kód vytvořený kompilátorem, doporučujeme ladit aplikaci a měřila svou výkonnost a optimalizujte váš kód.

Následující témata obsahují informace o tom, jak ladit verzi sestavení.

- [Ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [Postupy: Ladění optimalizovaného kódu](/visualstudio/debugger/how-to-debug-optimized-code)

- [Proč čísla s plovoucí desetinnou čárkou můžou ztratit přesnost](why-floating-point-numbers-may-lose-precision.md)


Následující témata obsahují informace o tom, jak optimalizovat vytváření, načítání a spouštění vašeho kódu.

- [Zvýšení propustnosti kompilátoru](improving-compiler-throughput.md)

- [Použití názvu funkce bez závorek nevygeneruje žádný kód](using-function-name-without-parens-produces-no-code.md)

- [Optimalizace vloženého sestavení](../assembler/inline/optimizing-inline-assembly.md)

- [Zadání optimalizace kompilátoru pro projekty ATL](../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [Jaké optimalizační techniky mám použít ke zlepšení výkonu klientské aplikace při načítání?](../build/dll-frequently-asked-questions.md#mfc_optimization)


## <a name="in-this-section"></a>V tomto oddílu

[Optimalizace Pragmas a klíčových slov](optimization-pragmas-and-keywords.md) \
[Zvýšení propustnosti kompilátoru](improving-compiler-throughput.md) \
[Proč čísla s plovoucí desetinnou čárkou mohou ztratit přesnost](why-floating-point-numbers-may-lose-precision.md) \
[Reprezentace plovoucí desetinné čárky IEEE](ieee-floating-point-representation.md) \
[Tipy pro zlepšení časově kritického kódu](tips-for-improving-time-critical-code.md) \
[Použití názvu funkce bez závorek nevygeneruje žádný kód](using-function-name-without-parens-produces-no-code.md) \
[Doporučené postupy optimalizace](optimization-best-practices.md) \
[Optimalizace na základě profilu](profile-guided-optimizations.md) \
[Proměnné prostředí pro optimalizace na základě profilu](environment-variables-for-profile-guided-optimizations.md) \
[PgoAutoSweep](pgoautosweep.md) \
[pgomgr](pgomgr.md) \
[pgosweep](pgosweep.md) \
[Postupy: Sloučení několika profilů PGO do jediného profilu](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](reference/c-cpp-building-reference.md)
