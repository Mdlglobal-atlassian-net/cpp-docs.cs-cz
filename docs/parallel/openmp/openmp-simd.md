---
title: Rozšíření SIMD
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 0a7f1142a3a432628795341f4885b76a5c144990
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366456"
---
# <a name="simd-extension"></a>Rozšíření SIMD

Visual C++ v současné době podporuje standard OpenMP 2.0, ale Visual Studio 2019 také nyní nabízí funkce SIMD.

> [!NOTE]
> Chcete-li používat SIMD, kompilujte s přepínačem, `-openmp:experimental` `-openmp` který umožňuje další funkce OpenMP, které nejsou k dispozici při použití přepínače.
>
> Přepínač `-openmp:experimental` subsumes `-openmp`, což znamená, že všechny OpenMP 2.0 funkce jsou zahrnuty v jeho použití.

Další informace najdete v tématu [ROZŠÍŘENÍ SIMD pro C++ OpenMP v sadě Visual Studio](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/).

## <a name="openmp-simd-in-visual-c"></a>OpenMP SIMD ve Visual C++

OpenMP SIMD, představený ve standardu OpenMP 4.0, se zaměřuje na vytváření vektorově přívětivých smyček. Pomocí `simd` směrnice před smyčky kompilátor usměrníte můžete ignorovat vektorové závislosti, aby smyčka jako vektorpřátelské jak je to možné, a respektovat záměr uživatelů mít více opakování smyčky spustit současně.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Visual C++ poskytuje podobné non-OpenMP `#pragma vector` smyčky `#pragma ivdep`pragmas jako a , nicméně s OpenMP SIMD, kompilátor může udělat víc, jako:

- Vždy povoleno ignorovat současné vektorové závislosti.
- `/fp:fast`je v rámci smyčky povolena.
- Vnější smyčky a smyčky s voláním funkcí jsou šetrné k vektorům.
- Vnořené smyčky mohou být splynou do jedné smyčky a provedeny vektorově přívětivé.
- Hybridní akcelerace s `#pragma omp for simd` umožňují hrubozrnné vícevláknové a jemnozrnné vektory.  

Pro vektorové smyčky kompilátor zůstane tichý, pokud nepoužijete přepínač protokolu podporující vektor:

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

U smyček, které nejsou vhodné pro vektory, kompilátor vydá každému zprávu:

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>Klauzule

Směrnice OpenMP SIMD může také přijmout následující klauzule pro zvýšení podpory vektorů:

|Směrnice|Popis|
|---|---|
|`simdlen(length)`|Zadejte počet vektorových pruhů.|
|`safelen(length)`|Zadejte vzdálenost závislosti vektoru.|
|`linear(list[ : linear-step]`)|Lineární mapování z indukční proměnné smyčky na odběr pole.|
|`aligned(list[ : alignment])`|Zarovnání dat.|
|`private(list)`|Zadejte privatizaci dat.|
|`lastprivate(list)`|Zadejte privatizaci dat s konečnou hodnotou z poslední iterace.|
|`reduction(reduction-identifier:list)`|Zadejte operace přizpůsobené redukce.|
|`collapse(n)`|Hnízdo smyčkové smyčky.|

> [!NOTE]
> Neefektivní klauzule SIMD jsou analyzovány a ignorovány kompilátorem s upozorněním.
>
> Například použití následujícího kódu vydá upozornění:
>
> ```c
>    #pragma omp simd simdlen(8)
>    for (i = 0; i < count; i++)
>    {
>        a[i] = a[i-1] + 1;
>        b[i] = *c + 1;
>        bar(i);
>    }
> ```
>
> ```Output
>    warning C4849: OpenMP 'simdlen' clause ignored in 'simd' directive
> ```

### <a name="example"></a>Příklad
  
OpenMP SIMD směrnice poskytuje uživatelům způsob, jak diktovat kompilátor, aby smyčky vektorově přívětivé. Anotací smyčky se směrnicí OpenMP SIMD mají uživatelé v úmyslu provést více iterací smyčky současně.

Například následující smyčka je anotována direktivou OpenMP SIMD. Neexistuje žádný dokonalý paralelismus mezi iterací smyčky, protože existuje zpětná závislost z [i] na [i-1], ale z důvodu směrnice SIMD je kompilátor stále povoleno zabalit po sobě jdoucí iterace prvního příkazu do jedné vektorové instrukce a spustit je paralelně.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Proto následující transformované vektorové formě smyčky je **legální,** protože kompilátor udržuje sekvenční chování každé původní opakování smyčky. Jinými `a[i]` slovy, je `a[-1]`proveden `b[i]` po `a[i]` , je `bar` po a volání se stane poslední.

```c
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        b[i:i+3] = *c + 1;
        bar(i);
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

Není **legální** přesunout odkaz `*c` na paměť ze smyčky, pokud `a[i]` `b[i]`může alias s nebo . Je také není legální přeuspořádat příkazy uvnitř jedné původní iterace, pokud přeruší sekvenční závislost. Například následující transformovaná smyčka není legální:

```c
    c = b;
    t = *c;
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        bar(i);            // illegal to reorder if bar[i] depends on b[i]
        b[i:i+3] = t + 1;  // illegal to move *c out of the loop
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

## <a name="see-also"></a>Viz také

[/openmp (Povolit podporu OpenMP 2.0)](../../build/reference/openmp-enable-openmp-2-0-support.md)<br/>
