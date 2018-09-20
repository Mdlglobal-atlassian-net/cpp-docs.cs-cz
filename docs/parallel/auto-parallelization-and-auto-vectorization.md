---
title: Automatická paralelizace a Automatická vektorizace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1deed05b4f64e6817af68af7fc726e21d752cf7f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380773"
---
# <a name="auto-parallelization-and-auto-vectorization"></a>Automatická paralelizace a automatická vektorizace

Automatický Paralelizér a automatický Vektorizér jsou navržená k poskytování zvýšení výkonu automatické smyčky ve vašem kódu.

## <a name="auto-parallelizer"></a>Automatický Paralelizér

[/Qpar](../build/reference/qpar-auto-parallelizer.md) umožňuje přepínač kompilátoru *automatickou paralelizaci* smyček ve vašem kódu. Při zadání tohoto příznaku beze změny stávajícího kódu, vyhodnotí kompilátor kód a nalezení smyček, které by mohly mít prospěch z paralelního zpracování. Protože může najít smyček, které nechcete provést mnoho práce a nebude proto těžit z paralelizace a vzhledem k tomu, že všechny nepotřebné paralelizace může způsobit vytváření podřízeného procesu vlákna fondu, další synchronizace, nebo jiné zpracování, která by obvykle ke zpomalení výkon místo jeho vylepšení kompilátoru je konzervativní při výběru smyček, které ho parallelizes. Zvažte například následující příklad, ve kterém horní mez smyčky není znám v době kompilace:

```cpp
void loop_test(int u) {
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

Protože `u` může být malou hodnotu, kompilátor nebude automaticky paralelizovat tuto smyčku. Nicméně stále můžete paralelizovaná protože víte, že `u` bude vždy velké. Chcete-li povolit Automatická paralelizace, zadejte [#pragma loop(hint_parallel(n))](../preprocessor/loop.md), kde `n` je počet vláken pro paralelní zpracování napříč. V následujícím příkladu kompilátor se pokusí paralelizovat smyčku napříč 8 vlákny.

```cpp
void loop_test(int u) {
#pragma loop(hint_parallel(8))
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

Stejně jako u všech [direktivy pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), syntaxi alternativní – Direktiva pragma `__pragma(loop(hint_parallel(n)))` je také podporována.

Existují některé smyček, které kompilátor nemůže paralelní zpracování i v případě, že chcete, aby. Tady je příklad:

```cpp
#pragma loop(hint_parallel(8))
for (int i=0; i<upper_bound(); ++i)
    A[i] = B[i] * C[i];
```

Funkce `upper_bound()` může změnit pokaždé, když je volána. Protože je známa horní mez, kompilátor může vysílat diagnostickou zprávu, která vysvětluje, proč ho nemůžete paralelizovat tuto smyčku. Následující příklad znázorňuje smyčku, která může být paralelizována, smyčku, která nemůže být paralelizována, použijte na příkazovém řádku ve výstupu kompilátoru pro jednotlivé možnosti příkazového řádku kompilátoru syntaxi:

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

Kompilování pomocí tohoto příkazu:

`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:1`

poskytuje tento výstup:

```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
```

Kompilování pomocí tohoto příkazu:

`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:2`

poskytuje tento výstup:

```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
d:\myproject\mytest.cpp(4) : loop not parallelized due to reason '1008'
```

Všimněte si, že ve výstupu rozdíl mezi dvě různé [/Qpar-report (úroveň sestav automatický Paralelizér)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md) možnosti. `/Qpar-report:1` Vypíše automatickou paralelizací zprávy pouze pro smyčky, které jsou úspěšně paralelizována. `/Qpar-report:2` zprávy nástrojů pro obě smyčky úspěšné a neúspěšné parallelizations výstupů.

Další informace o kódech příčiny a zprávy v tématu [zprávy nástrojů pro vektorizaci a](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

## <a name="auto-vectorizer"></a>Automatický Vektorizér

Automatický Vektorizér analyzuje smyčky ve vašem kódu a používá vektorové registry a pokynů v cílovém počítači ke spouštění, pokud je to možné. Tím lze vylepšit výkon kódu. Kompilátor zaměřuje na pokyny SSE2, AVX a AVX2 u procesorů Intel nebo AMD nebo pokynů NEON na ARM procesorech podle [/arch](../build/reference/arch-minimum-cpu-architecture.md) přepnout.

Automatický Vektorizér mohou generovat různé pokyny, než je zadáno v `/arch` přepnout. Tyto pokyny jsou strážený kontroly za běhu, abyste měli jistotu, že kód stále běží správně. Například pokud kompilujete `/arch:SSE2`, může být vygenerován SSE4.2 pokyny. Kontroly za běhu ověří, zda je k dispozici na cílový procesor SSE4.2 a přejde na verzi jiné SSE4.2 smyčky, pokud procesor nepodporuje tyto pokyny.

Ve výchozím nastavení je automatický Vektorizér zapnutý. Pokud chcete porovnat výkon kódu v rámci vektorizace, můžete použít [#pragma loop(no_vector)](../preprocessor/loop.md) zakázat vektorizace jakékoli dané smyčky.

```cpp
#pragma loop(no_vector)
for (int i = 0; i < 1000; ++i)
   A[i] = B[i] + C[i];
```

Stejně jako u všech [direktivy pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), syntaxi alternativní – Direktiva pragma `__pragma(loop(no_vector))` je také podporována.

Podobně jako u na automatický Paralelizér, můžete zadat [/Qvec-report (úroveň sestav automatickou vektorizací)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md) možnost příkazového řádku, buď sestavy úspěšně vektorizovaná smyčky pouze –`/Qvec-report:1`– nebo oba úspěšně a neúspěšně vektorizovaná smyčky –`/Qvec-report:2`).

Další informace o kódech příčiny a zprávy v tématu [zprávy nástrojů pro vektorizaci a](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

Příklad znázorňující, jak automatickou vektorizací funguje v praxi, najdete v části [projektu Austin část 2 ze 6: kulmy stránky](http://blogs.msdn.com/b/vcblog/archive/2012/09/27/10348494.aspx)

## <a name="see-also"></a>Viz také

[loop](../preprocessor/loop.md)<br/>
[Paralelní programování v nativním kódu](http://go.microsoft.com/fwlink/p/?linkid=263662)<br/>
[/Qpar (automatická paralelizace)](../build/reference/qpar-auto-parallelizer.md)<br/>
[/Qpar-report (úroveň generování sestav s automatickou paralelizací)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)<br/>
[/Qpar-report (úroveň generování sestav s automatickou vektorizací)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)<br/>
[Zprávy nástrojů pro vektorizaci a paralelní zpracování](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)