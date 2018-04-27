---
title: indirect_array – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- valarray/std::indirect_array
dev_langs:
- C++
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6ed390aafdea4741fcfb3599a850c19d75a293fc
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="indirectarray-class"></a>indirect_array – třída

Třída interní, pomocného šablony, která podporuje objekty, které jsou podmnožiny valarray – třídy tím, že poskytuje operace mezi poli podmnožina definované zadáním podmnožinu indexy valarray – nadřazené.

## <a name="syntax"></a>Syntaxe

## <a name="remarks"></a>Poznámky

Třída popisuje objekt, který ukládá odkaz na objekt **va** třídy [valarray –](../standard-library/valarray-class.md)**\<typ >**, společně s objekt **xa**  třídy **valarray – < size_t >**, který popisuje pořadí prvků pro výběr **valarray –\<typ >** objektu.

Můžete vytvořit **indirect_array\<typ >** objekt pouze napsáním výrazu ve formátu **va [xa]**. Členské funkce tříd indirect_array pak chovat jako odpovídající funkce podpisy definované pro **valarray –\<typ >** kromě toho, že má vliv jenom pořadí vybraných elementů.

Pořadí se skládá z **xa.** [velikost](../standard-library/valarray-class.md#size) elementy, kde element `I` stane index **xa**[ `I`] v rámci **va**.

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

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
