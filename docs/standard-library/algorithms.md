---
title: Algoritmy | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 369479614174e1e66d91e39e3decacaf24268a08
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="algorithms"></a>Algoritmy
Algoritmů je základní součástí standardní knihovna C++. Algoritmy nefungují s kontejnery sami, ale s iterátory. Proto stejný algoritmus lze ve většině není-li všechny kontejnery standardní knihovna C++. Tato část popisuje konvence a přehled terminologie algoritmů standardní knihovna C++.  
  
## <a name="remarks"></a>Poznámky  
 Popis funkce šablon algoritmus využít několik sdružená frází:  
  
-   Fráze "v rozsahu [*A*, *B*)" znamená pořadí nula nebo více jednotlivých hodnot počínaje *A* než s výjimkou *B*. Rozsah je platný pouze v případě *B* je dostupný z *A;* můžete ukládat *A* v objektu *N* (*N*  =  *A*), zvýší objekt vícekrát nebo (++*N*), a mít objekt porovnat rovna *B* po omezený počet kroků (N == B*).*  
  
-   Fráze "každý *N* v rozsahu [*A*, *B*)" znamená, že *N* začíná hodnotou *A* a je zvýší vícekrát nebo dokud se rovná hodnotě *B*. Tento případ *N* == *B* není v rozsahu.  
  
-   Fráze "nejnižší hodnotu *N* v rozsahu [*A*, *B*) tak, aby *X*" znamená, že podmínka *X*je určen pro každou *N* v rozsahu [*A*, *B*) až podmínku *X* splníte.  
  
-   Fráze "nejvyšší hodnotu *N* v rozsahu [*A*, *B*) tak, aby *X* znamená, že *X* je určit pro jednotlivé *N* v rozsahu [*A*, *B*). Funkce ukládá do `K` kopii *N* pokaždé, když podmínku *X* splníte. Pokud dojde k takové úložiště, funkce nahrazuje konečná hodnota *N*, které se rovná *B*, s hodnotou `K`. Obousměrné nebo iterator náhodný přístup, ale ho můžete také znamenají, že *N* začíná nejvyšší hodnotu v rozsahu a se odečte přes oblast, dokud podmínky *X* splníte.  
  
-   Výrazy, například *X* - *Y*, kde *X* a *Y* může být iterátory než iterátory náhodný přístup, jsou určené v matematickém smysl. Funkce nevyhodnocuje nutně operátor **-**  Pokud je třeba určit tuto hodnotu. Totéž platí i pro výrazy, jako *X* + *N* a *X* - *N*, kde *N*  je celočíselného typu.  
  
 Ujistěte se, několik algoritmů použití predikát, který provádí pairwise porovnání, například s `operator==`, která předá třídu `bool` výsledek. Funkce predikátu `operator==`, nebo jakékoli náhradou, nesmí změnit buď jejími operandy. Musí zaručit, stejné `bool` způsobit pokaždé, když je vyhodnocena a pokud je kopie buď operand nahradit pro operand ho musí zaručit stejný výsledek.  
  
 Ujistěte se, několik algoritmů použití predikát, který se musí použít striktní slabé řazení na páry prvků z sekvenci. Pro predikát `pr`(*X*, *Y*):  
  
-   Strict znamená, že `pr`(*X*, *X*) je hodnota false.  
  
-   Weak znamená, že *X* a *Y* mít ekvivalentní řazení Pokud!`pr` (*X*, *Y*) & &!`pr` (*Y*, *X*) (*X* == *Y* nemusí být definován).  
  
-   Řazení znamená, že `pr`(*X*, *Y*) & & `pr`(*Y*, Z) znamená `pr`(*X*, Z).  
  
 Některé z těchto algoritmů implicitně pomocí predikátu *X* \< *Y*. Jsou ostatní predikáty, které obvykle odpovídají striktní weak řazení požadavek *X* > *Y*, **menší**(*X*,  *Y*), a `greater`(*X*, *Y*). Všimněte si, ale který predikáty, jako *X* \< =  *Y* a *X* >= *Y* nesplňují Tento požadavek.  
  
 Pořadí elementů určené, které iterátory v rozsahu [`First`, `Last`) je pořadí řazení podle operátor **<**  Pokud pro každou *N* v rozsahu [0, `Last`  -  `First`) a pro každou *M* v rozsahu (N, `Last`  -  `First`) predikát! () \*(`First` + *M*) < \*(*první* + *N*)) hodnotu true. (Všimněte si, že prvky jsou seřazeny ve vzestupném pořadí.) Funkce predikátu **operátor <**, nebo jakékoli náhradou, nesmí změnit buď jejími operandy. Musí zaručit, stejné `bool` způsobit pokaždé, když je vyhodnocena a pokud je kopie buď operand nahradit pro operand ho musí zaručit stejný výsledek. Kromě toho musíte použít, striktní slabé řazení operandy, které se porovná.  
  
 Pořadí elementů určené, které iterátory v rozsahu [`First`, `Last`) je haldy seřazené podle **operátor <** Pokud pro každou *N* v rozsahu [1, `Last`  -  `First`) predikát! (\*`First` < \*(`First` + *N*)) hodnotu true. (První prvek je největší.) Jeho vnitřní struktura je známé jenom k funkcím šablony [make_heap –](../standard-library/algorithm-functions.md#make_heap), [pop_heap –](../standard-library/algorithm-functions.md#pop_heap), a [push_heap –](../standard-library/algorithm-functions.md#push_heap). Stejně jako u seřazené posloupnosti, funkce predikátu **operátor <**, nebo jakékoli náhradou, nesmí změnit buď jejími operandy, a musí použít, striktní slabé řazení u operandů porovná. Musí zaručit, stejné `bool` způsobit pokaždé, když je vyhodnocena a pokud je kopie buď operand nahradit pro operand ho musí zaručit stejný výsledek.  
  
 Standardní knihovna C++ algoritmy jsou umístěné v [ \<algoritmus >](../standard-library/algorithm.md) a [ \<číselné >](../standard-library/numeric.md) soubory hlaviček.  
  
## <a name="see-also"></a>Viz také  
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

