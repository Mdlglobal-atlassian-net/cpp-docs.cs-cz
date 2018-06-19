---
title: 2.7.2.6 snížení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e7630a15-2978-4dbe-a29b-3a46371a0151
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 759a2ee50f047fbd5777481d009332be998ad359
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688801"
---
# <a name="2726-reduction"></a>2.7.2.6 reduction

Tuto klauzuli provádí skalární proměnné, které se zobrazují v snížení *seznamu proměnné*, s operátorem *op*. Syntaxe `reduction` klauzule vypadá takto:

> snížení (*op*: *seznamu proměnné*)

Snížení se obvykle zadává pro příkaz s jedním z následujících podob:

> *x* = *x* *op* *expr*  
> *x* *binop* = *expr*  
> *x* = *expr* *op* *x* (s výjimkou odčítání)  
> *x*++  
> ++*x*  
> *x*--  
> --*x*  

kde:

*x*  
Jeden z redukční proměnné zadané v `list`.

*Proměnná seznamu*  
Seznam oddělený čárkami skalární redukční proměnné.

*Expr*  
Výraz s skalární typ, který neobsahuje odkaz *x*.

*OP*  
Není přetížené operátor ale jeden z +, &#42;, -, &amp;, ^, &#124;, &amp; &amp;, nebo &#124; &#124;.

*binop*  
Není přetížené operátor ale jeden z +, &#42;, -, &amp;, ^, nebo &#124;.

Tady je příklad `reduction` klauzule:  
  
```cpp  
#pragma omp parallel for reduction(+: a, y) reduction(||: am)  
for (i=0; i<n; i++) {  
   a += b[i];  
   y = sum(y, c[i]);  
   am = am || b[i] == c[i];  
}  
```  
  
Jak je znázorněno v příkladu, může být operátor skrytý uvnitř volání funkce. Uživatel by měl dávejte pozor, aby operátor zadaný v `reduction` klauzule odpovídá snížení operaci.

I když pravý operand &#124; &#124; operátor má v tomto příkladu žádné vedlejší účinky, jsou povolené, ale by měla být používána opatrně. V tomto kontextu vedlejším účinkem, který zaručeně není dojít během sekvenční provádění smyčky může dojít během paralelní provádění. Tento rozdíl může dojít, protože neurčitém pořadí provádění iterace.

Operátor slouží k určení počáteční hodnota všechny soukromé proměnné používané kompilátor za účelem snížení a určení finalizace operátor. Příkaz snížení mimo lexikální rozsah konstruktu zadání operátor explicitně umožňuje. Libovolný počet `reduction` klauzule může být určen na direktiva, ale proměnné se mohou objevit v maximálně jeden `reduction` klauzuli pro tento – direktiva.

Privátní kopie pro každou proměnnou v *seznamu proměnné* se vytvoří, jednou pro každé vlákno, jako kdyby `private` klauzuli měl použít. Privátní kopie je inicializován podle operátor (viz následující tabulka).

Na konci oblasti, pro kterou `reduction` byla zadána klauzule, původní objekt aktualizován, aby odrážel výsledkem kombinace původní hodnotu s konečná hodnota jednotlivých privátní kopií pomocí operátoru zadán. Operátory snížení jsou všechny asociativní (s výjimkou odčítání) a kompilátor může volně přidružení výpočet konečná hodnota. (Částečné výsledky snížení odčítání se přidají k vytvoření konečná hodnota).

Hodnota původní objekt změní neurčitou, pokud první vlákno dosáhne obsahující klauzuli a tak zůstane až do dokončení snížení výpočet.  Za normálních okolností výpočet bude dokončena na konci konstrukce; ale pokud `reduction` klauzule se používá na konstrukce, ke kterému `nowait` je taky použije, původní objekt zůstává hodnota neurčitém před provedením synchronizace bariéry zajistit, že všechna vlákna dokončili `reduction`klauzule.

Následující tabulka uvádí operátory, které jsou platné a jejich hodnoty kanonický inicializace. Hodnota skutečného inicializace bude konzistentní s datovým typem redukční proměnné.

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

Omezení, které mají `reduction` klauzule jsou následující:

- Typ proměnné v `reduction` klauzule musí být platná pro operátor snížení, s tím rozdílem, že se nikdy povolené typy ukazatelů a odkazové typy.

- Proměnné, která je zadána v `reduction` nesmí být klauzule **const**-kvalifikovaný.

- Proměnné, která jsou soukromá v rámci paralelní oblasti nebo která se zobrazují `reduction` klauzuli **paralelní** – direktiva nelze zadat v `reduction` klauzule ve sdílení práce direktiva, která se sváže s paralelní konstrukce.

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
