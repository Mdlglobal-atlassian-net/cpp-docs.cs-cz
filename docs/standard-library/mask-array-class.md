---
title: mask_array – třída
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 9da5e3593288be02819330e11b60e306784054dc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460143"
---
# <a name="maskarray-class"></a>mask_array – třída

Interní pomocná třída šablony, která podporuje objekty, které jsou podmnožinou nadřazených valarrays, určené s logickým výrazem, poskytnutím operací mezi poli podmnožiny.

## <a name="syntax"></a>Syntaxe

## <a name="remarks"></a>Poznámky

Třída popisuje objekt, který ukládá odkaz na `va` objekt třídy [valarray](../standard-library/valarray-class.md) **\<typu >** společně s objektem [\<](../standard-library/valarray-bool-class.md) `ba` valarray bool >, který popisuje sekvence prvků, které se mají vybrat `valarray<Type>` z objektu

Objekt vytváříte pouze pomocí zápisu výrazu ve formátu [VA&#91;ba&#93;.](../standard-library/valarray-class.md#op_at) `mask_array<Type>` Členské funkce třídy mask_array se pak chovají jako odpovídající signatury funkce definované pro `valarray<Type>`, s tím rozdílem, že jsou ovlivněny pouze sekvence vybraných elementů.

Sekvence se skládá maximálně z `ba.size` prvků. Prvek *J* je zahrnutý pouze v případě, že je hodnota **ba**[ *J*] true. Proto je v sekvenci tolik prvků, jako jsou pravdivé prvky v `ba`. Pokud `I` je index nejnižšího prvku true v `ba`, pak hodnota **VA**[ `I`] je ve vybrané sekvenci nula elementu.

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

**Hlavička:** \<valarray >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
