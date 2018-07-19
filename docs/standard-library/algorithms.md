---
title: Algoritmy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], C++ algorithm conventions
- algorithms [C++], C++
- C++ Standard Library, algorithms
- algorithm template function C++ library conventions
- conventions [C++], C++ algorithm
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5338ddeb802d13d100e5e3026152793f866c90f6
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961022"
---
# <a name="algorithms"></a>Algoritmy

Algoritmy jsou základní součástí standardní knihovny C++. Algoritmy, nebudou fungovat s kontejnery, sami, ale s iterátory. Proto stejný algoritmus může využívat většinu není-li všechny kontejnery standardní knihovny C++. Tato část popisuje konvence a terminologie algoritmů standardní knihovny C++.

## <a name="remarks"></a>Poznámky

Popis jednotlivých funkcí šablony algoritmus využívat několik Zkrácený tvar vlastností frází:

- Fráze "v rozsahu [*A*, *B*)" znamená, že posloupnost nula nebo více jednotlivých hodnot počínaje *A* až, ale bez zahrnutí *B*. Rozsah je platný pouze tehdy, pokud *B* dosažitelný z *A;* můžete ukládat *A* v objektu *N* (*N*  =  *A*), zvýší objekt nulakrát nebo vícekrát (++*N*), a mít objekt rovnají *B* po konečné číslo navyšuje (N == B *).*

- Fráze "každý *N* v rozsahu [*A*, *B*)" znamená, že *N* začíná hodnotou *A* a je zvýší nulakrát nebo vícekrát, dokud se rovná hodnotě *B*. Tento případ *N* == *B* není v rozsahu.

- Fráze "nejnižší hodnotu *N* v rozsahu [*A*, *B*) tak, aby *X*" znamená, že podmínka *X*je určen pro každou *N* v rozsahu [*A*, *B*) až do podmínky *X* je splněna.

- Fráze "nejvyšší hodnotu *N* v rozsahu [*A*, *B*) tak, aby *X* znamená, že *X* je Určuje pro jednotlivé *N* v rozsahu [*A*, *B*). Funkce ukládá `K` kopii *N* pokaždé, když podmínka *X* je splněna. Pokud dojde k takové úložiště, funkce nahrazuje konečná hodnota *N*, které se rovná *B*, s hodnotou `K`. Obousměrné nebo iterátor s náhodným přístupem, ale může také to, který *N* začíná nejvyšší číslo v rozsahu a je snížen přes oblast, dokud se podmínka *X* je splněna.

- Výrazy, jako *X* - *Y*, kde *X* a *Y* může být iterátory než iterátory s náhodným přístupem, jsou určeny v matematickém smyslu. Funkce není nutně vyhodnocen operátor**-** Pokud je třeba určit tato hodnota. Totéž platí také pro výrazy, jako *X* + *N* a *X* - *N*, kde *N*  je typu integer.

Ujistěte se několik algoritmů využívání predikát, který provádí pairwise porovnání, například s `operator==`, pozastavit **bool** výsledek. Funkce predikátu `operator==`, nebo všechny náhražkou nesmí změnit jeden z operandů. Musí zaručit, stejné **bool** způsobit pokaždé, když je vyhodnocen, a pokud kopii některý operand je nahrazen pro operand ho musí poskytovat stejný výsledek.

Ujistěte se několik algoritmů pomocí predikátu, které musí ukládat přísné slabé seřazení na dvojice prvků z posloupnosti. Pro predikát `pr`(*X*, *Y*):

- Strict znamená, že `pr`(*X*, *X*) má hodnotu false.

- Slabé znamená, že *X* a *Y* mají ekvivalentní řazení if!`pr` (*X*, *Y*) & &!`pr` (*Y*, *X*) (*X* == *Y* nemusí být definovány).

- Řazení znamená, že `pr`(*X*, *Y*) & & `pr`(*Y*, Z) znamená `pr`(*X*, Z).

Některé z těchto algoritmů implicitně pomocí predikátů *X* \< *Y*. Jsou ostatní predikáty, které zpravidla odpovídají přísné slabé seřazení požadavek *X* > *Y*, `less`(*X*, *Y*), a `greater`(*X*, *Y*). Všimněte si, ale, který predikáty například *X* \< =  *Y* a *X* >= *Y* nesplňují Tento požadavek.

Pořadí prvků určených iterátory v rozsahu [`First`, `Last`) je sekvence seřazené podle operátor**<** if, pro každou *N* v rozsahu [0, `Last`  -  `First`) a pro každou *M* v rozsahu (N, `Last`  -  `First`) predikát! () \*(`First` + *M*) < \*(*první* + *N*)) má hodnotu true. (Všimněte si, že prvky jsou seřazeny vzestupně.) Funkce predikátu `operator<`, nebo všechny náhražkou nesmí změnit jeden z operandů. Musí zaručit, stejné `bool` způsobit pokaždé, když je vyhodnocen, a pokud kopii některý operand je nahrazen pro operand ho musí poskytovat stejný výsledek. Kromě toho musíte uložit přísné slabé seřazení operandy, které porovnává.

Pořadí prvků určených iterátory v rozsahu [`First`, `Last`) je haldu seřazené podle `operator<` if, pro každou *N* v rozsahu [1, `Last`  -  `First`) predikát! (\*`First` < \*(`First` + *N*)) má hodnotu true. (První prvek je největší.) Její vnitřní struktura je označováno pouze pro šablony funkce [make_heap –](../standard-library/algorithm-functions.md#make_heap), [pop_heap –](../standard-library/algorithm-functions.md#pop_heap), a [push_heap –](../standard-library/algorithm-functions.md#push_heap). Stejně jako v seřazené posloupnosti, funkce predikátu `operator<`, nebo všechny náhražkou nesmí změnit některý z jeho operandy a musí ukládat přísné slabé seřazení u operandů porovná. Musí zaručit, stejné **bool** způsobit pokaždé, když je vyhodnocen, a pokud kopii některý operand je nahrazen pro operand ho musí poskytovat stejný výsledek.

Algoritmy standardní knihovny C++ jsou umístěny v [ \<algoritmus >](../standard-library/algorithm.md) a [ \<číselné >](../standard-library/numeric.md) hlavičkové soubory.

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
