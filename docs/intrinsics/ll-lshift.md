---
title: __ll_lshift | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
dev_langs: C++
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0d827b375cd382ff4f298f2933fc8a3109d2f846
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="lllshift"></a>__ll_lshift
**Konkrétní Microsoft**  
  
 Posune poskytnutá hodnota 64-bit doleva o zadaný počet bitů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned __int64 __ll_lshift(  
   unsigned __int64 Mask,  
   int nBit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`Mask`  
 64bitové celočíselné hodnoty posunutí doleva.  
  
 [v]`nBit`  
 Počet bitů se posunou.  
  
## <a name="return-value"></a>Návratová hodnota  
 Maska zapuštěno vlevo podle `nBit` bits.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__ll_lshift`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Pokud při kompilaci váš program pomocí architektury 64bitová verze a `nBit` je větší než 63, je počet bitů se posunou `nBit` modulo 64. Pokud při kompilaci váš program pomocí 32bitové architektury a `nBit` je větší než 31, je počet bitů se posunou `nBit` modulo 32.  
  
 `ll` v názvu označuje, že to je operace na `long long` (`__int64`).  
  
## <a name="example"></a>Příklad  
  
```  
// ll_lshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_lshift)  
  
int main()  
{  
   unsigned __int64 Mask = 0x100;  
   int nBit = 8;  
   Mask = __ll_lshift(Mask, nBit);  
   cout << hex << Mask << endl;  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
10000  
```  
  
 **Poznámka:** není nepodepsané verze operace posunutí doleva. Důvodem je, že `__ll_lshift` už používá nepodepsané vstupní parametr. Na rozdíl od posunutí doprava není už přihlašovací závislost pro posunutí doleva, protože nejméně významný bit ve výsledku je vždy nastaven na hodnotu nula bez ohledu na přihlášení zapuštěno hodnoty.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__ll_rshift](../intrinsics/ll-rshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)