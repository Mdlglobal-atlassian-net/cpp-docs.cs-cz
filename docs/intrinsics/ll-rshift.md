---
title: __ll_rshift | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e404375eefaf456ae22d2eca5cb66a13dd6a72ae
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="llrshift"></a>__ll_rshift
**Microsoft Specific**  
  
 Posune 64 bitů hodnotu zadanou pomocí prvního parametru vpravo podle počtu bitů určeného druhý parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__int64 __ll_rshift(  
   __int64 Mask,  
   int nBit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Mask`  
 64bitové celočíselné hodnoty posunutí doprava.  
  
 [in] `nBit`  
 Počet bitů se posunou modulo 64 na x64 a modulo 32 na x86.  
  
## <a name="return-value"></a>Návratová hodnota  
 Maska posunuty o `nBit` bits.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__ll_rshift`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Je-li druhý parametr je větší než 64 na x64 (32 na x86), který číslo je obsazené modulo 64 (32 na x86) k určení počtu bitů se posunou. `ll` Předponu označuje, že to je operace na `long long`, jiný název pro `__int64`, 64bitové celočíselné typ se znaménkem.  
  
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
  
 **Poznámka:** Pokud `_ull_rshift` byl používá, znaků zapuštěno pravé hodnoty by byl nula, takže požadovaný výsledek by byly získány v případě zápornou hodnotu.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)