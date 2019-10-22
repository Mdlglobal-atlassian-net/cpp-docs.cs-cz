---
title: mask_array – třída
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 12398203d61f2c3ea155b5f6e6e7b118d4a13c75
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689407"
---
# <a name="mask_array-class"></a>mask_array – třída

Interní pomocná šablona třídy, která podporuje objekty, které jsou podmnožinou nadřazených valarrays, určené s logickým výrazem, poskytnutím operací mezi poli podmnožiny.

## <a name="syntax"></a>Syntaxe

## <a name="remarks"></a>Poznámky

Třída popisuje objekt, který ukládá odkaz na objekt `va` třídy [valarray](../standard-library/valarray-class.md)  **\<Type >** , společně s objektem `ba` třídy [valarray \<bool >](../standard-library/valarray-bool-class.md), který popisuje sekvenci prvků k výběru. z objektu `valarray<Type>`.

Objekt `mask_array<Type>` vytvoříte pouze pomocí zápisu výrazu ve formátu [VA&#91;ba&#93;](../standard-library/valarray-class.md#op_at). Členské funkce třídy mask_array se pak chovají stejně jako odpovídající signatura funkce definované pro `valarray<Type>`, s tím rozdílem, že jsou ovlivněny pouze sekvence vybraných elementů.

Sekvence se skládá z nejvíce `ba.size` prvků. Prvek *J* je zahrnutý pouze v případě, že je hodnota **ba**[ *J*] true. Proto existuje tolik prvků v sekvenci, protože jsou v `ba` pravdivé prvky. Pokud `I` je index nejmenšího true elementu v `ba`, pak hodnota **VA**[`I`] je ve vybrané sekvenci nula elementu.

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

**Záhlaví:** \<valarray >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
