---
title: "Vnitřní funkce _InterlockedXor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _InterlockedXor_nf
- _InterlockedXor_np
- _InterlockedXor64_HLERelease
- _InterlockedXor8_acq
- _InterlockedXor64_acq
- _InterlockedXor64_rel
- _InterlockedXor64_nf
- _InterlockedXor_acq
- _InterlockedXor16
- _InterlockedXor64_np
- _InterlockedXor64
- _InterlockedXor_HLEAcquire
- _InterlockedXor_HLERelease
- _InterlockedXor_cpp
- _InterlockedXor16_rel
- _InterlockedXor8_rel
- _InterlockedXor8
- _InterlockedXor64_HLEAcquire
- _InterlockedXor16_nf
- _InterlockedXor16_acq
- _InterlockedXor16_np
- _InterlockedXor8_fn
- _InterlockedXor8_np
- _InterlockedXor64_cpp
- _InterlockedXor_rel
- _InterlockedXor
dev_langs: C++
helpviewer_keywords:
- InterlockedXor intrinsic
- _InterlockedXor64 intrinsic
- InterlockedXor64 intrinsic
- _InterlockedXor intrinsic
ms.assetid: faef1796-cb5a-4430-b1e2-9d5eaf9b4a91
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3c0dcf83a409f949d1f6bd677d76242186cb4eb7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="interlockedxor-intrinsic-functions"></a>_InterlockedXor vnitřní funkce
**Konkrétní Microsoft**  
  
 Provedení atomic bitový exkluzivní nebo operace (XOR –) na proměnnou sdíleny více vlákny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
long _InterlockedXor(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedXor_acq(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedXor_HLEAcquire(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedXor_HLERelease(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedXor_nf(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedXor_np(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedXor_rel(  
   long volatile * Value,  
   long Mask  
);  
char _InterlockedXor8(  
   char volatile * Value,  
   char Mask  
);  
char _InterlockedXor8_acq(  
   char volatile * Value,  
   char Mask  
);  
char _InterlockedXor8_nf(  
   char volatile * Value,  
   char Mask  
);  
char _InterlockedXor8_np(  
   char volatile * Value,  
   char Mask  
);  
char _InterlockedXor8_rel(  
   char volatile * Value,  
   char Mask  
);  
short _InterlockedXor16(  
   short volatile * Value,  
   short Mask  
);  
short _InterlockedXor16_acq(  
   short volatile * Value,  
   short Mask  
);  
short _InterlockedXor16_nf (  
   short volatile * Value,  
   short Mask  
);  
short _InterlockedXor16_np (  
   short volatile * Value,  
   short Mask  
);  
short _InterlockedXor16_rel(  
   short volatile * Value,  
   short Mask  
);  
__int64 _InterlockedXor64(  
   __int64 volatile * Value,  
   __int64 Mask  
);  
__int64 _InterlockedXor64_acq(  
   __int64 volatile * Value,  
   __int64 Mask  
);   
__int64 _InterlockedXor64_HLEAcquire(  
   __int64 volatile * Value,  
   __int64 Mask  
);  
__int64 _InterlockedXor64_HLERelease(  
   __int64 volatile * Value,  
   __int64 Mask  
);   
__int64 _InterlockedXor64_nf(  
   __int64 volatile * Value,  
   __int64 Mask  
);  
__int64 _InterlockedXor64_np(  
   __int64 volatile * Value,  
   __int64 Mask  
);  
__int64 _InterlockedXor64_rel(  
   __int64 volatile * Value,  
   __int64 Mask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [ve out]`Value`  
 Ukazatel na první operand nahradit za výsledek.  
  
 [v]`Mask`  
 Druhý operand.  
  
## <a name="return-value"></a>Návratová hodnota  
 První operand původní hodnota  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|Záhlaví|  
|---------------|------------------|------------|  
|`_InterlockedXor`, `_InterlockedXor8`, `_InterlockedXor16`, `_InterlockedXor64`|x86 ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
|`_InterlockedXor_acq`, `_InterlockedXor_nf`, `_InterlockedXor_rel`, `_InterlockedXor8_acq`, `_InterlockedXor8_nf`, `_InterlockedXor8_rel`, `_InterlockedXor16_acq`, `_InterlockedXor16_nf`, `_InterlockedXor16_rel`, `_InterlockedXor64_acq`, `_InterlockedXor64_nf`, `_InterlockedXor64_rel`,|ARM|\<intrin.h >|  
|`_InterlockedXor_np`, `_InterlockedXor8_np`, `_InterlockedXor16_np`, `_InterlockedXor64_np`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
|`_InterlockedXor_HLEAcquire`, `_InterlockedXor_HLERelease`, `_InterlockedXor64_HLEAcquire`, `_InterlockedXor64_HLERelease`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h >|  
  
## <a name="remarks"></a>Poznámky  
 Číslo názvu jednotlivé funkce určuje velikost bit argumenty.  
  
 Na platformách ARM použít vnitřní funkce s `_acq` a `_rel` přípony, pokud potřebujete získat a vydání sémantikou, například na začátku a konci kritické části. ARM – vnitřní prvky s `_nf` přípony ("žádné ochranná") nefungují jako bariéry paměti.  
  
 Vnitřní funkce s `_np` operaci možné předběžné načtení z vkládání kompilátorem zabránit přípony ("žádné předběžné načtení").  
  
 Na platformách Intel, které podporují pokyny hardwaru zámku Elision (HLE), vnitřní funkce s `_HLEAcquire` a `_HLERelease` přípony zahrnují nápovědu pro procesor, které můžou urychlit výkonu odstraněním krok zápisu zámku v hardwaru. Pokud tyto – vnitřní prvky se označují jako na platformách, které nepodporují HLE, pomocný parametr bude ignorován.  
  
## <a name="example"></a>Příklad  
  
```  
// _InterLockedXor.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_InterlockedXor)  
  
int main()  
{  
        long data1 = 0xFF00FF00;  
        long data2 = 0x00FFFF00;  
        long retval;  
        retval = _InterlockedXor(&data1, data2);  
        printf_s("0x%x 0x%x 0x%x", data1, data2, retval);   
}  
```  
  
```Output  
0xffff0000 0xffff00 0xff00ff00  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Konflikty s kompilátorem x86](../build/conflicts-with-the-x86-compiler.md)