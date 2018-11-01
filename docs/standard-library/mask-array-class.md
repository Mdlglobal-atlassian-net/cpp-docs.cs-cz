---
title: mask_array – třída
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 108c942bef33e44b515d46e953c9d99274e3ce8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475816"
---
# <a name="maskarray-class"></a>mask_array – třída

Třída interní, pomocné šablony, která podporuje objekty, které jsou podmnožinou tohoto nadřazeného valarrays zadaným logický výraz, tím, že poskytuje operace mezi podmnožinu polí.

## <a name="syntax"></a>Syntaxe

## <a name="remarks"></a>Poznámky

Tato třída popisuje objekt, který uchovává odkaz na objekt `va` třídy [valarray](../standard-library/valarray-class.md)**\<typ >**, spolu s objektem `ba` třídy [ valarray –\<bool >](../standard-library/valarray-bool-class.md), která popisuje řadu prvků, můžete vybírat z `valarray<Type>` objektu.

Můžete vytvořit `mask_array<Type>` pouze v případě, že napíšeme výrazu v podobě [posouzení ohrožení zabezpečení&#91;ba&#93;](../standard-library/valarray-class.md#op_at). Členské funkce třídy mask_array – potom chovají jako odpovídající funkce podpisy definované pro `valarray<Type>`, s tím rozdílem, že má vliv jenom pořadí vybraných elementů.

Sekvence se skládá z maximálně `ba.size` elementy. Element *J* je zahrnuta, pouze pokud **ba**[ *J*] má hodnotu true. Proto existují libovolný počet prvků v sekvenci jsou true prvky v `ba`. Pokud `I` je index elementu nejnižší hodnota true v `ba`, pak **posouzení ohrožení zabezpečení**[ `I`] je element nula ve zvolené sekvenci.

## <a name="example"></a>Příklad

```cpp
// mask_array.cpp
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

   // Use masked subsets to assign a value of 10
   // to all elements grrater than 3 in value
   va [va > 3 ] = 10;
   cout << "The modified operand valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;
}
```

### <a name="output"></a>Výstup

```Output
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 2 -1 10 -1 10 -1 10 -1).
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<valarray – >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
