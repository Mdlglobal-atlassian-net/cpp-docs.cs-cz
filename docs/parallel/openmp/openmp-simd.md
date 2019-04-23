---
title: Rozšíření SIMD
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 52402aa553c6d68d3073aba26ecac7b784522ee9
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "60125161"
---
# <a name="simd-extension"></a>Rozšíření SIMD

Vizuální C++ však Visual Studio 2019 nyní také nabízí funkce SIMD v současné době podporuje standard OpenMP 2.0.

> [!NOTE]
> Pokud chcete použít SIMD, proveďte kompilaci s `-openmp:experimental` přepínač, který povolí další funkce OpenMP není k dispozici při použití `-openmp` přepnout.
>
> `-openmp:experimental` Přepínač zahrnuje `-openmp`, to znamená všechny OpenMP 2.0 funkce jsou zahrnuté v jeho použití.

Další informace najdete v tématu [rozšíření SIMD C++ OpenMP ve Visual Studiu](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/).

## <a name="openmp-simd-in-visual-c"></a>OpenMP – SIMD ve VizuáluC++

OpenMP – SIMD, počínaje OpenMP 4.0 standard, provádění smyčky vektoru vhodných cílů. S použitím `simd` direktiv před smyčku, kompilátor může ignorovat závislosti vektorů, proveďte smyčky jako vektor přívětivá nejrychleji a dodržovat uživatelů v úmyslu mít současné vykonávání více iterací smyčky.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Vizuální C++ poskytuje podobné pragma smyčky-OpenMP – například `#pragma vector` a `#pragma ivdep`, ale s OpenMP SIMD, může kompilátor zavést další, jako jsou:

- Ignorovat k dispozici závislosti vektorů je vždycky povolená.
- `/fp:fast` je povolen v rámci smyčky.
- Vnější smyčky a smyčky pomocí volání funkce jsou přívětivá vektoru.
- Vnořené smyčky může sloučené do jedné smyčky a provedené přívětivá vektoru.
- Akcelerace hybridní s `#pragma omp for simd` umožňující hrubých ukryta a podrobné vektorů.  

Vektor přívětivá smyček for zůstává kompilátor tiché Pokud nepoužijete přepínač protokolu vektorové podpory:

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

Vektor vhodných smyček for kompilátor vyvolá každá zpráva:

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>Klauzule

Direktiva OpenMP SIMD můžete taky využít následující klauzule k vylepšení vektorové podpory:

|– Direktiva|Popis|
|---|---|
|`simdlen(length)`|Zadejte počet procesu vektoru.|
|`safelen(length)`|Určete vzdálenost závislost vektoru.|
|`linear(list[ : linear-step]`)|Lineární mapování indukční proměnná smyčky do předplatného pole.|
|`aligned(list[ : alignment])`|Zarovnání dat|
|`private(list)`|Zadejte privatizace data.|
|`lastprivate(list)`|Zadejte data privatizace s konečnou hodnotu od poslední iterace.|
|`reduction(reduction-identifier:list)`|Zadejte vlastní redukční operace.|
|`collapse(n)`|Sloučení vnoření smyčky.|

> [!NOTE]
> Klauzule SIMD non-effective jsou analyzovány a ignorováno kompilátory s upozorněním.
>
> Například použijte následující kód problémů upozornění:
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
  
Direktiva OpenMP SIMD poskytuje uživatelům způsob, jak určovat smyčky zkontrolujte kompilátoru vector – popisný. Anotací smyčky pomocí direktivy OpenMP SIMD, uživatelé v úmyslu mít současné vykonávání více iterací smyčky.

Například následující zacyklení, je opatřen poznámkou OpenMP SIMD – direktiva. Protože zpětné závislost z [i] [i-1], ale z důvodu směrnice SIMD, které kompilátor přesto je umožněno pack po sobě následujících iterací první příkaz do jedné instrukce vektoru a spusťte neexistuje žádné ideální paralelismu mezi průchod cyklem je paralelně.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Proto je následující formulář transformovaný vektoru smyčky **právní** vzhledem k tomu, že kompilátor udržuje sekvenční chování každého původní průchodu cyklem. Jinými slovy `a[i]` se spustí až po `a[-1]`, `b[i]` po `a[i]` a volání `bar` se stane poslední.

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

Má **právní** přesunout odkaz na paměť `*c` ze smyčky, pokud může alias s `a[i]` nebo `b[i]`. Také není platný mění pořadí příkazů uvnitř jedné iterace původní, pokud to naruší sekvenční závislostí. Například následující transformovaný smyčky není platný:

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

## <a name="see-also"></a>Viz také:

[/openmp (povolení podpory OpenMP 2.0)](../../build/reference/openmp-enable-openmp-2-0-support.md)<br/>
