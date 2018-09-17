---
title: __ull_rshift | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __ull_rshift
dev_langs:
- C++
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ad07e225afbfe0c69b5115cfb566ef722eb81e3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722656"
---
# <a name="ullrshift"></a>__ull_rshift
**Specifické pro Microsoft**  
  
 x64, se přesune na 64 bitů hodnotu zadanou pomocí prvního parametru vpravo o počet bitů určený druhý parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned __int64 __ull_rshift(   
   unsigned __int64 mask,    
   int nBit   
);  
```  
  
#### <a name="parameters"></a>Parametry  
*Maska*<br/>
[in] 64bitové celočíselné hodnoty posunutí doprava.  
  
*nBit*<br/>
[in] Počet bitů, chcete-li posunout modulo 32 na x86 a modulo 64 na x64.  
  
## <a name="return-value"></a>Návratová hodnota  
 Maska o `nBit` bits.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__ull_rshift`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Není-li druhý parametr je větší než 31 na x86 (63 na x64), toto číslo provedena modulo 32 (64 na x64) k určení počtu bitů a posunutí. `ull` v názvu označuje `unsigned long long (unsigned __int64)`.  
  
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
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ll_rshift](../intrinsics/ll-rshift.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)