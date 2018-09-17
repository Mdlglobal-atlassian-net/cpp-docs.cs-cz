---
title: __ll_rshift | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
dev_langs:
- C++
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8df70d0ba5c0f957620ee204256b6c92ce4c01f1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722069"
---
# <a name="llrshift"></a>__ll_rshift
**Specifické pro Microsoft**  
  
 Posune 64 bitů hodnotu zadanou pomocí prvního parametru vpravo o počet bitů určený druhý parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__int64 __ll_rshift(  
   __int64 Mask,  
   int nBit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
*Maska*<br/>
[in] 64bitové celočíselné hodnoty posunutí doprava.  
  
*nBit*<br/>
[in] Počet bitů, chcete-li posunout modulo 64 na x64 a modulo 32 na x86.  
  
## <a name="return-value"></a>Návratová hodnota  
 Maska o `nBit` bits.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__ll_rshift`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Není-li druhý parametr je větší než 64 na x64 (32 na x86), toto číslo provedena modulo 64 (32 na x86) k určení počtu bitů a posunutí. `ll` Předponu označuje, že se jedná operaci na `long long`, další název `__int64`, 64-bit celočíselný typ se znaménkem.  
  
## <a name="example"></a>Příklad  
  
```  
// ll_rshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_rshift)  
  
int main()  
{  
   __int64 Mask = - 0x100;  
   int nBit = 4;  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
   Mask = __ll_rshift(Mask, nBit);  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
ffffffffffffff00  
 - 100  
fffffffffffffff0  
 - 10  
```  
  
 **Poznámka:** Pokud `_ull_rshift` byl použit, MSB hodnotu posunuta doprava by byl nula, tak v případě záporné hodnoty by byly získány požadovaný výsledek.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)