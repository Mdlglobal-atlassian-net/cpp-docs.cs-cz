---
title: indirect_array – třída
ms.date: 11/04/2016
f1_keywords:
- valarray/std::indirect_array
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
ms.openlocfilehash: 5db5f2ce60038267b70ae8e77d9dd929d972af6a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456328"
---
# <a name="indirectarray-class"></a>indirect_array – třída

Interní pomocná třída šablony, která podporuje objekty, které jsou podmnožinou valarrays, poskytováním operací mezi poli podmnožiny, které jsou definovány určením podmnožiny indexů nadřazené valarray.

## <a name="syntax"></a>Syntaxe

## <a name="remarks"></a>Poznámky

Třída popisuje objekt, který ukládá odkaz na `va` objekt třídy [valarray](../standard-library/valarray-class.md) **\<typu >** společně s objektem `xa` třídy `valarray<size_t>`, který popisuje sekvenci prvků, ze kterých lze vybírat. `valarray<Type>` objekt.

Objekt vytvoříte pouze pomocí zápisu výrazu formuláře `va[xa]`. `indirect_array<Type>` Členské funkce třídy indirect_array se pak chovají jako odpovídající signatury funkce definované pro `valarray<Type>`, s tím rozdílem, že jsou ovlivněny pouze sekvence vybraných elementů.

Sekvence se skládá z protokolu **XA.** prvky [velikosti](../standard-library/valarray-class.md#size) , kde se `I` element změní na index XA `I`[] `va`v rámci.

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

**Hlavička:** \<valarray >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
