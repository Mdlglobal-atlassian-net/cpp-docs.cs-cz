---
title: Algoritmy
ms.date: 10/18/2018
helpviewer_keywords:
- libraries [C++], C++ algorithm conventions
- algorithms [C++], C++
- C++ Standard Library, algorithms
- algorithm template function C++ library conventions
- conventions [C++], C++ algorithm
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
ms.openlocfilehash: d363dc3f06222121ac5efc79b30516ebd55ff539
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456490"
---
# <a name="algorithms"></a>Algoritmy

Algoritmy jsou základní součástí C++ standardní knihovny. Algoritmy nefungují s vlastními kontejnery, ale spíše pomocí iterátorů. Proto je možné stejný algoritmus použít většinou v případě, že ne všechny C++ standardní kontejnery knihovny. Tato část popisuje konvence a terminologie C++ standardních algoritmů knihovny.

## <a name="remarks"></a>Poznámky

Popisy funkcí šablon algoritmu používají několik zkratek:

- Fráze "v \[rozsahu *a*, *B*)" označuje sekvenci nula nebo více diskrétních hodnot, které *začínají až,* ale ne včetně *B*. Rozsah je platný pouze v případě, že je *B* dosažitelný z *A;* můžete *Uložit v* objektu *n* (*n* = *a*), zvýšit počet objektů nula nebo vícekrát (+ +*N*) a nechat objekt porovnat se rovná *B* po konečném počtu přírůstcích (*N* == *B*).

- Fráze "každé *n* v rozsahu \[ *A*, *B*)" znamená, že *N* začíná hodnotou *a* a je zvýšena nula nebo vícekrát, dokud se nerovná hodnotě *B*. Případ *N* == *B* není v rozsahu.

- Fráze "nejnižší hodnota *N* v rozsahu \[ *a*, *b*) tak, že *x*" znamená, že podmínka *x* je určena pro každý *N* v rozsahu \[ *a*, *b*) až do podmínka *X* je splněná.

- Fráze "nejvyšší hodnota *N* v \[rozsahu *a*, *b*) tak, že *x* znamená, že *x* je určeno pro každý *N* v \[rozsahu *a*, *b*). Funkce ukládá do *k* a kopii *N* pokaždé, když je splněna podmínka *X* . Pokud takové úložiště dojde, funkce nahradí konečnou hodnotu *N*, která se rovná *B*, s hodnotou *K*. U iterátoru obousměrného nebo náhodného přístupu ale může také znamenat, že *N* začíná nejvyšší hodnotou v rozsahu a bude snížena nad rozsah, dokud není splněna podmínka *X* .

- Výrazy jako *x* - *Y*, kde *x* a *Y* můžou být iterátory jiné než iterátory náhodného přístupu, jsou určené matematickému smyslu. Funkce nemusí nutně vyhodnotit operátor **-** , pokud musí určit takovou hodnotu. Totéž platí také pro výrazy jako *X* + *n* a *x* - *N*, kde *N* je typ Integer.

Několik algoritmů používá predikát, který provádí srovnávací porovnání, jako je například s `operator==`, pro zajištění **logického** výsledku. Funkce `operator==`predikátu, nebo jakákoli náhrada, nesmí měnit žádný z jeho operandů. Musí vracet stejný **logický** výsledek pokaždé, když je vyhodnocen a musí vracet stejný výsledek, pokud je pro operand nahrazena kopie jednoho operandu.

Několik algoritmů používá predikát, který musí způsobit striktní slabé řazení párů prvků z sekvence. Pro predikát *před*(*X*, *Y*):

- Striktní znamená, že *před*(*x*, *x*) je NEPRAVDA.

- Slabý znamená, že *X* a *Y* mají ekvivalentní řazení, \!Pokud *před*(*X*, *Y*) & \!& *před*(*Y*, *X*) (*x* == *y* ). musí být definována).

- Řazení znamená, že *před*(*x*, *Y*) & *& před*(*y*, *z*) implikuje *před*(*x*, *z*).

Některé z těchto algoritmů implicitně používají predikát *X* \< *Y*. Další predikáty, které obvykle odpovídají přísně slabému požadavku na řazení, `less`jsou *x* > *Y*, (*X*, `greater` *Y*) a (*x*, *y*). Všimněte si ale, že predikáty jako *x* \< =  *y* a *x* >= *y* nesplňují tento požadavek.

Sekvence prvků určených \[iterátory v rozsahu *First*, *Last*) je sekvence seřazená podle operátoru **<** , pokud pro každý *N* v rozsahu \[0, *nakonec* - jako*první.* ) a pro každý *M* v rozsahu (*N*, *nakonec* - *nejdříve* \!) predikát (\*(*první* + *m*) < \*(First + *N*)) má hodnotu true. (Všimněte si, že prvky jsou seřazené ve vzestupném pořadí.) Funkce `operator<`predikátu, nebo jakákoli náhrada, nesmí měnit žádný z jeho operandů. Musí vracet stejný **logický** výsledek pokaždé, když je vyhodnocen a musí vracet stejný výsledek, pokud je pro operand nahrazena kopie jednoho operandu. Kromě toho musí být pro operandy, které porovnává, přísně slabé řazení.

Sekvence prvků, které jsou určeny iterátory \[v rozsahu \[ `Last` `First`,) je halda seřazená podle `operator<` if, pro každou *N* v rozsahu 1, *Poslední* - *první*). predikát \!(\*_First_ *(First*N))má hodnotu true. +  < \* (První prvek je největší.) Jeho interní struktura je jinak známá pouze pro šablony funkce [make_heap](../standard-library/algorithm-functions.md#make_heap), [pop_heap](../standard-library/algorithm-functions.md#pop_heap)a [push_heap](../standard-library/algorithm-functions.md#push_heap). Stejně jako u seřazených sekvencí, funkce `operator<`predikátu nebo jakékoli náhrady pro ni nesmí měnit žádný z jeho operandů a musí pro ně způsobit striktní slabé řazení u operandů, které porovnávají. Musí vracet stejný **logický** výsledek pokaždé, když je vyhodnocen a musí vracet stejný výsledek, pokud je pro operand nahrazena kopie jednoho operandu.

C++ Standardní algoritmy knihovny se nacházejí v [ \<> algoritmu](../standard-library/algorithm.md) a [ \<číselné >](../standard-library/numeric.md) hlavičkových souborů.

## <a name="see-also"></a>Viz také:

[C++Odkaz na standardní knihovnu](../standard-library/cpp-standard-library-reference.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
