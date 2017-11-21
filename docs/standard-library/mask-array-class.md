---
title: "mask_array – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: valarray/std::mask_array
dev_langs: C++
helpviewer_keywords: mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2dfc6705d9d042b9a12ab84cb314d49cddc855a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="maskarray-class"></a>mask_array – třída
Třída interní, pomocného šablony, která podporuje objekty, které jsou podmnožiny nadřazené valarray – třídy, zadaný logický výraz, tím, že poskytuje operace mezi poli podmnožina.  
  
## <a name="syntax"></a>Syntaxe  
  
  
  
## <a name="remarks"></a>Poznámky  
 Třída popisuje objekt, který ukládá odkaz na objekt **va** třídy [valarray –](../standard-library/valarray-class.md)**\<typ >**, společně s objekt **ba**  třídy [valarray –\<bool >](../standard-library/valarray-bool-class.md), který popisuje pořadí prvků pro výběr **valarray –\<typ >** objektu.  
  
 Můžete vytvořit **mask_array\<typ >** objekt pouze napsáním výrazu ve formátu [va &#91; ba &#93;](../standard-library/valarray-class.md#op_at). Členské funkce tříd mask_array pak chovat jako odpovídající funkce podpisy definované pro **valarray –\<typ >**kromě toho, že má vliv jenom pořadí vybraných elementů.  
  
 Pořadí se skládá z maximálně **ba.size** elementy. Element *J* je zahrnuta pouze v případě **ba**[ *J*] hodnotu true. Proto existují libovolný počet elementů v pořadí true elementy v **ba**. Pokud `I` je index elementu nejnižší hodnotu true v **ba**, pak **va**[ `I`] je element nula ve zvolené sekvenci.  
  
## <a name="example"></a>Příklad:  
  
```  
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
  
```  
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).  
The modified operand valarray is:  (0 -1 2 -1 10 -1 10 -1 10 -1).  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<valarray – >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

