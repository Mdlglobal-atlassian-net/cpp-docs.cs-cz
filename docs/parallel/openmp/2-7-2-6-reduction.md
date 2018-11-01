---
title: 2.7.2.6 reduction
ms.date: 11/04/2016
ms.assetid: e7630a15-2978-4dbe-a29b-3a46371a0151
ms.openlocfilehash: 54b326feb4e4ccf1f1da5c8152ffc8d1e4bd13b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456014"
---
# <a name="2726-reduction"></a>2.7.2.6 reduction

Tato klauzule provádí snížení na skalární proměnné, které se zobrazují v *seznamu proměnné*, spolu s operátorem *op*. Syntaxe `reduction` klauzule vypadá takto:

> snížení (*op*: *seznamu proměnné*)

Snížení se obvykle zadává pro příkaz s jedním z následujících forem:

> *x* = *x* *op* *expr*
> *x* *binop* = *expr*
> *x* = *expr* *op* *x* (s výjimkou pro odčítání) *x*++
> ++*x*
> *x*--
> --*x*

kde:

*x*<br/>
Jedna z proměnných snížení podle `list`.

*Proměnná list*<br/>
Čárkou oddělený seznam proměnných snížení skaláru.

*výraz*<br/>
Výraz s skalárního typu, který neodkazuje na *x*.

*OP*<br/>
Není přetíženého operátoru, ale jeden z +, &#42;, -, &amp;, ^, &#124;, &amp; &amp;, nebo &#124; &#124;.

*binop*<br/>
Není přetíženého operátoru, ale jeden z +, &#42;, -, &amp;, ^, nebo &#124;.

Následující je příkladem `reduction` klauzule:

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

Jak je znázorněno v příkladu, mohou být skryty operátor uvnitř funkce volání. Uživatel by měl být opatrní, že operátor podle `reduction` klauzule odpovídá operaci snížení.

I když bude pravý operand &#124; &#124; operátor v tomto příkladu nemá žádné vedlejší účinky, jsou povolené, ale by měla být používána opatrně. V tomto kontextu vedlejší účinek, který je zaručeno, že ke kterým dojde během sekvenční provádění smyčky může dojít během paralelního provádění. Tento rozdíl situace může nastat, vzhledem k tomu, že je neurčité, pořadí spuštění iterace.

Operátor, který se používá k určení počáteční hodnoty žádné soukromé proměnné, které kompilátor použije pro snížení a na zjištění operátor finalizace. Odstranit explicitním zadáním operátor, který umožňuje snížení příkazu mimo lexikální rozsah konstrukce. Libovolný počet `reduction` klauzule může být určen v direktivě, ale proměnná se může vyskytovat nejvýše jedna `reduction` klauzule pro tuto direktivu.

Soukromou kopii každou proměnnou v *seznamu proměnné* vytvořen, jednou pro každé vlákno, jako kdyby `private` klauzule nepoužilo. Podle operátor, který je inicializován soukromou kopii (viz následující tabulka).

Na konci oblasti, pro kterou `reduction` byla zadána klauzule, původní objekt aktualizován, aby odrážel výsledek, který spojuje s konečnou hodnotu každého soukromé kopie pomocí operátoru zadán původní hodnotu. Operátory snížení jsou všechny asociativní (s výjimkou odčítání) a kompilátor může volně znovu přidružit výpočtu konečnou hodnotu. (Částečných výsledků snížení odčítání jsou přidány do formuláře konečná hodnota).

Při první vlákno dosáhne obsahující klauzuli a tak zůstane až do dokončení výpočtu snížení se stane neurčité hodnotě původního objektu.  Za normálních okolností bude dokončena na konci konstrukce; výpočtu ale pokud `reduction` na konstrukce, ke kterému se používá klauzuli `nowait` je také použít původní objekt zůstává hodnota neurčitý dokud barrier synchronizace byla provedena Ujistěte se, že všechna vlákna dokončila `reduction`klauzuli.

Následující tabulka uvádí, které jsou platné operátory a jejich hodnoty canonical inicializace. Hodnota vlastní inicializaci bude konzistentní s datovým typem redukční proměnná.

|Operátor|Inicializace|
|--------------|--------------------|
|+|0|
|&#42;|1|
|-|0|
|&amp;|~0|
|&#124;|0|
|^|0|
|&amp;&amp;|1|
|&#124;&#124;|0|

Omezení týkající `reduction` klauzule jsou následující:

- Typ proměnné `reduction` klauzule musí být platná pro operátor snížení, s tím rozdílem, že nikdy povolené typy ukazatele a typy odkazů.

- Proměnná, která je zadána v `reduction` nesmí mít klauzuli **const**-kvalifikovaný.

- Proměnné, které jsou v rámci paralelní oblasti privátní nebo které se objeví v `reduction` klauzuli **paralelní** směrnice nelze zadat v `reduction` klauzuli direktivy sdílení práce, s vazbou na paralelní konstrukce.

   ```cpp
   #pragma omp parallel private(y)
   { /* ERROR - private variable y cannot be specified
                in a reduction clause */
      #pragma omp for reduction(+: y)
      for (i=0; i<n; i++)
         y += b[i];
   }

   /* ERROR - variable x cannot be specified in both
              a shared and a reduction clause */
   #pragma omp parallel for shared(x) reduction(+: x)
   ```
