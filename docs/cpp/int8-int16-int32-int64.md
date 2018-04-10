---
title: __int8, __int16, __int32, __int64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- __int8_cpp
- __int16_cpp
- __int32_cpp
- __int64_cpp
dev_langs:
- C++
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 957e2483d61855c442780440ccf87441f00cb1c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="int8-int16-int32-int64"></a>__int8, __int16, __int32, __int64
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Jazyk Microsoft C/C++ obsahuje podporu pro celočíselné typy s velikostí. Deklarace 8 - 16-, 32- nebo 64bitovou celočíselnou hodnotu proměnné pomocí **__int**  *n*  zadejte specifikátor, kde  *n*  je 8, 16, 32 nebo 64.  
  
 Následující příklad deklaruje jednu proměnnou pro každý z těchto celočíselných typů s velikostí:  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 Typy `__int8`, `__int16` a `__int32` jsou synonyma pro typy ANSI stejné velikosti a jsou užitečné pro psaní přenositelného kódu, který se chová stejně na různých platformách. `__int8` Datový typ je shodný s typem `char`, `__int16` je totožná s typem **krátké**, a `__int32` je totožná s typem `int`. `__int64` Typ je shodný s typem `long long`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, že __int*xx* , bude parametr povýšen `int`:  
  
```  
// sized_int_types.cpp  
  
#include <stdio.h>  
  
void func(int i) {  
    printf_s("%s\n", __FUNCTION__);  
}  
  
int main()  
{  
    __int8 i8 = 100;  
    func(i8);   // no void func(__int8 i8) function  
                // __int8 will be promoted to int  
}  
```  
  
```Output  
func  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Základní typy](../cpp/fundamental-types-cpp.md)   
 [Rozsahy datových typů](../cpp/data-type-ranges.md)