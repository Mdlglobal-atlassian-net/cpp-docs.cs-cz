---
title: Automatická paralelizace a automatická vektorizace
ms.date: 11/04/2016
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
ms.openlocfilehash: adc0dd9346cc2850b02e01804e26044c367f2d14
ms.sourcegitcommit: fcc3aeb271449f8be80348740cffef39ba543407
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82538618"
---
# <a name="auto-parallelization-and-auto-vectorization"></a>Automatická paralelizace a automatická vektorizace

Automatické paralelizace a auto-vektorizace jsou navržené tak, aby poskytovaly automatické nárůsty výkonu pro smyčky ve vašem kódu.

## <a name="auto-parallelizer"></a>Automatické paralelizace

Přepínač kompilátoru [/Qpar](../build/reference/qpar-auto-parallelizer.md) umožňuje *Automatické paralelismuing* smyček ve vašem kódu. Při zadání tohoto příznaku beze změny stávajícího kódu kompilátor vyhodnotí kód pro hledání smyček, které by mohly těžit z paralelismu. Vzhledem k tomu, že by mohlo dojít k nalezení smyček, které nedělají spoustu práce, a proto nebude výhoda paralelního zpracování, protože každý zbytečný paralelismus může engender vytváření fondu vláken, další synchronizaci nebo jiné zpracování, které by pomohly zpomalit výkon namísto jeho vylepšení, je při výběru smyček, které parallelizes, kompilátor konzervativní. Zvažte například následující příklad, ve kterém není horní mez smyčky v době kompilace známa:

```cpp
void loop_test(int u) {
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

Vzhledem `u` k tomu, že by mohla být malá hodnota, kompilátor tuto smyčku automaticky paralelizovat. Přesto ale budete chtít, aby byl váš i stále rovnoběžný, `u` protože víte, že budou vždy velké. Chcete-li povolit automatické paralelismuing, zadejte [#pragma smyčka (hint_parallel (n))](../preprocessor/loop.md), `n` kde je počet vláken, která se mají paralelizovat napříč. V následujícím příkladu se kompilátor pokusí paralelizovat smyčku napříč 8 vlákny.

```cpp
void loop_test(int u) {
#pragma loop(hint_parallel(8))
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

Stejně jako u všech [direktiv pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)je také podporována alternativní `__pragma(loop(hint_parallel(n)))` syntaxe pragma.

Existují některé cykly, které kompilátor nemůže paralelizovat, i když chcete. Tady je příklad:

```cpp
#pragma loop(hint_parallel(8))
for (int i=0; i<upper_bound(); ++i)
    A[i] = B[i] * C[i];
```

Funkce `upper_bound()` se může změnit pokaždé, když je volána. Vzhledem k tomu, že horní mez nelze znát, kompilátor může vygenerovat diagnostickou zprávu s vysvětlením, proč nemůže tuto smyčku paralelizovat. Následující příklad ukazuje smyčku, která může být paralelní, smyčka, která nemůže být paralelní, syntaxe kompilátoru použitá na příkazovém řádku a výstup kompilátoru pro jednotlivé parametry příkazového řádku:

```cpp
int A[1000];
void test() {
#pragma loop(hint_parallel(0))
    for (int i=0; i<1000; ++i) {
        A[i] = A[i] + 1;
    }

    for (int i=1000; i<2000; ++i) {
        A[i] = A[i] + 1;
    }
}
```

Kompilace pomocí tohoto příkazu:

`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:1`

vypočítá tento výstup:

```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
```

Kompilace pomocí tohoto příkazu:

`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:2`

vypočítá tento výstup:

```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
d:\myproject\mytest.cpp(4) : loop not parallelized due to reason '1008'
```

Všimněte si rozdílu ve výstupu mezi dvěma různými možnostmi [/Qpar-Report (úroveň vytváření sestav auto-paralelizace)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md) . `/Qpar-report:1`Vytvoří výstup zpráv paralelizace jenom pro cykly, které jsou úspěšně paralelismuované. `/Qpar-report:2`Vypíše zprávy paralelizace pro úspěšné i neúspěšné parallelizations smyčky.

Další informace o kódech a zprávách důvodů naleznete v tématu [vektorizace and paralelizace Messages](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

## <a name="auto-vectorizer"></a>Automatické vektorizace

Automatické vektorizace analyzuje smyčky v kódu a používá vektorové registry a pokyny v cílovém počítači k jejich spuštění, pokud je může. To může zlepšit výkon kódu. Kompilátor cílí na instrukce SSE2, AVX a AVX2 v procesorech Intel nebo AMD nebo na procesorech ARM v závislosti na přepínači [/arch](../build/reference/arch-minimum-cpu-architecture.md) .

Automatické vektorizace můžou vygenerovat jiné pokyny, než je zadané v `/arch` přepínači. Tyto pokyny jsou chráněny pomocí kontroly za běhu, aby se zajistilo, že kód stále běží správně. Například když kompilujete `/arch:SSE2`, mohou být vygenerovány pokyny SSE 4.2. Při kontrole za běhu se ověří, jestli je v cílovém procesoru k dispozici SSE 4.2, a přejde na verzi smyčky, která není SSE 4.2, pokud procesor tyto pokyny nepodporuje.

Ve výchozím nastavení je povolená možnost auto-vektorizace. Chcete-li porovnat výkon kódu v rámci vektorování, můžete použít [#pragma smyčka (no_vector)](../preprocessor/loop.md) , chcete-li zakázat rozvektorování kterékoli dané smyčky.

```cpp
#pragma loop(no_vector)
for (int i = 0; i < 1000; ++i)
   A[i] = B[i] + C[i];
```

Stejně jako u všech [direktiv pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)je také podporována alternativní `__pragma(loop(no_vector))` syntaxe pragma.

Stejně jako u auto-paralelizace můžete zadat možnost příkazového řádku [/Qvec-Report (auto-vektorizace Reporting Level)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md) , která bude hlásit buď úspěšně vektorové smyčky,`/Qvec-report:1`nebo úspěšné i neúspěšně vektorové smyčky –`/Qvec-report:2`).

Další informace o kódech a zprávách důvodů naleznete v tématu [vektorizace and paralelizace Messages](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

Příklad ukazující, jak vektorizace funguje v praxi, najdete v tématu [Project Austin Part 2 of 6: Vystránkování stránky.](https://devblogs.microsoft.com/cppblog/project-austin-part-2-of-6-page-curling/)

## <a name="see-also"></a>Viz také

[loop](../preprocessor/loop.md)<br/>
[Paralelní programování v nativním kódu](/archive/blogs/nativeconcurrency)<br/>
[/Qpar (automatická paralelizace)](../build/reference/qpar-auto-parallelizer.md)<br/>
[/Qpar-report (úroveň generování sestav s automatickou paralelizací)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)<br/>
[/Qvec-report (Úroveň sestavy s automatickou vektorizací)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)<br/>
[Zprávy nástrojů pro vektorizaci a paralelní zpracování](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)
