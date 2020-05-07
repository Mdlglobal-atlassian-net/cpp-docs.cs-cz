---
title: Optimalizace kódu
ms.date: 05/06/2019
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
ms.openlocfilehash: 00356cf50ca8e50c80e8a1142adf654816490c9b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078495"
---
# <a name="optimizing-your-code"></a>Optimalizace kódu

Optimalizací spustitelného souboru můžete dosáhnout rovnováhy mezi rychlostmi rychlého spuštění a malou velikostí kódu. Toto téma popisuje některé mechanismy, které poskytuje Visual Studio, které vám pomůžou s optimalizací kódu.

## <a name="language-features"></a>Jazykové funkce

Následující témata popisují některé funkce optimalizace v jazyce C/C++.

[Direktivy pragma a klíčová slova optimalizace](optimization-pragmas-and-keywords.md) \
Seznam klíčových slov a direktiv pragma, které lze použít ve svém kódu ke zvýšení výkonu.

[Možnosti kompilátoru uvedené podle kategorie](reference/compiler-options-listed-by-category.md) \
Seznam možností kompilátoru **/o** , které specificky ovlivňují rychlost spuštění nebo velikost kódu.

[Deklarátor odkazu rvalue:  &&](../cpp/rvalue-reference-declarator-amp-amp.md) \
Odkazy rvalue podporují implementaci *sémantiky přesunutí*. Pokud se k implementaci knihoven šablon používá sémantika přesunutí, výkon aplikací, které používají tyto šablony, může významně zlepšit.

### <a name="the-optimize-pragma"></a>Direktiva optimize pragma

Pokud optimalizovaná část kódu způsobí chyby nebo zpomalení, můžete použít [optimalizaci pragma pro](../preprocessor/optimize.md) vypnutí optimalizace pro tuto část.

Kód vložte mezi dvě direktivy pragma, jak je znázorněno zde:

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>Postupy programování

Pokud kompilujete kód s optimalizací, můžete si všimnout dalších varovných zpráv. Toto chování je očekáváno, protože některá upozornění se týkají pouze optimalizovaného kódu. Pokud heed tato upozornění, můžete se vyhnout mnoha problémům s optimalizací.

Paradoxically, optimalizace programu pro rychlost by mohla způsobit pomalejší běh kódu. Důvodem je to, že některé optimalizace pro zvýšení velikosti kódu zvyšují rychlost. Například funkce pro vkládání eliminují režii volání funkcí. Vložením příliš velkého množství kódu však může dojít k tomu, že váš program bude velký, že se zvyšuje počet chyb stránky virtuální paměti. Proto může být rychlost získaná z odstranění volání funkcí ztracena do vyměněné paměti.

V následujících tématech se zabýváte dobrými postupy programování.

[Tipy pro zlepšení časově kritického kódu](tips-for-improving-time-critical-code.md) \
Lepšími způsoby kódování může být lepší výkon. Toto téma navrhuje techniky kódování, které vám pomohou zajistit, že části kódu kritické pro čas fungují uspokojivě.

[Osvědčené postupy optimalizace](optimization-best-practices.md) \
Poskytuje obecné pokyny, jak nejlépe optimalizovat aplikaci.

## <a name="debugging-optimized-code"></a>Ladění optimalizovaného kódu

Vzhledem k tomu, že optimalizace může změnit kód vytvořený kompilátorem, doporučujeme ladit aplikaci a změřit její výkon a pak optimalizovat kód.

Následující témata obsahují informace o tom, jak ladit sestavení pro vydání.

- [Ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [Postupy: Ladění optimalizovaného kódu](/visualstudio/debugger/how-to-debug-optimized-code)

- [Proč čísla s plovoucí desetinnou čárkou mohou ztratit přesnost](why-floating-point-numbers-may-lose-precision.md)

Následující témata obsahují informace o tom, jak optimalizovat sestavování, načítání a spouštění kódu.

- [Zvýšení propustnosti kompilátoru](improving-compiler-throughput.md)

- [Použití názvu funkce bez závorek nevygeneruje žádný kód](using-function-name-without-parens-produces-no-code.md)

- [Optimalizace vloženého sestavení](../assembler/inline/optimizing-inline-assembly.md)

- [Zadání optimalizace kompilátoru pro projekty ATL](../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [Jaké optimalizační techniky mám použít ke zlepšení výkonu klientské aplikace při načítání?](../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="in-this-section"></a>V tomto oddílu

[Direktivy pragma a klíčová slova optimalizace](optimization-pragmas-and-keywords.md) \
[Vylepšení propustnosti kompilátoru](improving-compiler-throughput.md) \
[Proč čísla s plovoucí desetinnou čárkou můžou přijít o přesnost](why-floating-point-numbers-may-lose-precision.md) \
[Reprezentace plovoucí desetinné čárky IEEE](ieee-floating-point-representation.md) \
[Tipy pro zlepšení časově kritického kódu](tips-for-improving-time-critical-code.md) \
[Použití názvu funkce bez () negeneruje žádný kód.](using-function-name-without-parens-produces-no-code.md) \
[Osvědčené postupy optimalizace](optimization-best-practices.md) \
[Optimalizace na základě profilu](profile-guided-optimizations.md) \
[Proměnné prostředí pro optimalizace na základě profilu](environment-variables-for-profile-guided-optimizations.md) \
[PgoAutoSweep](pgoautosweep.md) \
[pgomgr](pgomgr.md) \
[pgosweep](pgosweep.md) \
[Postupy: Sloučení několika profilů PGO do jediného profilu](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)

## <a name="see-also"></a>Viz také

[Odkaz sestavení C/C++](reference/c-cpp-building-reference.md)
