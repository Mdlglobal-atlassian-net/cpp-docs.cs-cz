---
title: indirect_array – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::indirect_array
dev_langs:
- C++
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 676cc8ea493d113e9ef8a6f85108fdf3bad6ce5f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959504"
---
# <a name="indirectarray-class"></a>indirect_array – třída

Třída interní, pomocné šablony, která podporuje objekty, které jsou podmnožinou tohoto valarrays tím, že poskytuje operace mezi dílčí pole definovaná zadáním podmnožinu indexy valarray nadřazené.

## <a name="syntax"></a>Syntaxe

## <a name="remarks"></a>Poznámky

Tato třída popisuje objekt, který uchovává odkaz na objekt `va` třídy [valarray](../standard-library/valarray-class.md)**\<typ >**, spolu s objektem `xa` třídy `valarray<size_t>`, která popisuje řadu prvků, můžete vybírat z `valarray<Type>` objektu.

Vytvoření `indirect_array<Type>` pouze v případě, že napíšeme výrazu v podobě `va[xa]`. Členské funkce třídy indirect_array – potom chovají jako odpovídající funkce podpisy definované pro `valarray<Type>`, s tím rozdílem, že má vliv jenom pořadí vybraných elementů.

Sekvence se skládá z **xa.** [velikost](../standard-library/valarray-class.md#size) prvků, kde element `I` stane index **xa**[ `I`] v rámci `va`.

## <a name="example"></a>Příklad:

```cpp
// indirect_array.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      va [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 2 )
      va [ i ] =  -1;

   cout << "The initial operand valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   // Select 2nd, 4th & 6th elements
   // and assign a value of 10 to them
   valarray<size_t> indx ( 3 );
   indx [0] = 2;
   indx [1] = 4;
   indx [2] = 6;
   va[indx] = 10;

   cout << "The modified operand valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;
}
```

### <a name="output"></a>Výstup

```cpp
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<valarray – >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
