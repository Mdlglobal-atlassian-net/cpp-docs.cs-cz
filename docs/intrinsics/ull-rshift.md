---
title: __ull_rshift | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __ull_rshift
dev_langs: C++
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c0951a930ad5baec5b293aee0fe8e70c0a38a12f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ullrshift"></a>__ull_rshift
**Konkrétní Microsoft**  
  
 x64, se přesune na 64-bit hodnotu zadanou pomocí prvního parametru vpravo podle počtu bitů určeného druhý parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned __int64 __ull_rshift(   
   unsigned __int64 mask,    
   int nBit   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`mask`  
 64bitové celočíselné hodnoty posunutí doprava.  
  
 [v]`nBit`  
 Počet bitů se posunou modulo 32 na x86 a modulo 64 na x64.  
  
## <a name="return-value"></a>Návratová hodnota  
 Maska posunuty o `nBit` bits.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__ull_rshift`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Je-li druhý parametr je větší než 31 na x86 (63 na x64), který číslo je obsazené modulo 32 (64 na x64) k určení počtu bitů se posunou. `ull` v názvu označuje `unsigned long long (unsigned __int64)`.  
  
## <a name="example"></a>Příklad  
  
```  
// ull_rshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ull_rshift)  
  
int main()  
{  
   unsigned __int64 mask = 0x100;  
   int nBit = 8;  
   mask = __ull_rshift(mask, nBit);  
   cout << hex << mask << endl;  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
1  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ll_rshift](../intrinsics/ll-rshift.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)