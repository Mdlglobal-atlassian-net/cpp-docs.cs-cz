---
title: "Vnitřní funkce _InterlockedOr | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _InterlockedOr8_nf
- _InterlockedOr_HLEAcquire
- _InterlockedOr16_nf
- _InterlockedOr64
- _InterlockedOr8_np
- _InterlockedOr64_cpp
- _InterlockedOr8_acq
- _InterlockedOr_nf
- _InterlockedOr64_acq
- _InterlockedOr_np
- _InterlockedOr8
- _InterlockedOr
- _InterlockedOr64_np
- _InterlockedOr_acq
- _InterlockedOr64_HLERelease
- _InterlockedOr16_np
- _InterlockedOr_cpp
- _InterlockedOr8_rel
- _InterlockedOr64_rel
- _InterlockedOr16_acq
- _InterlockedOr_rel
- _InterlockedOr16_rel
- _InterlockedOr_HLERelease
- _InterlockedOr64_HLEAcquire
- _InterlockedOr16
- _InterlockedOr64_nf
dev_langs: C++
helpviewer_keywords:
- _InterlockedOr_acq intrinsic
- InterlockedOr64 intrinsic
- _InterlockedOr_nf intrinsic
- _InterlockedOr intrinsic
- _InterlockedOr64_HLERelease intrinsic
- _InterlockedOr8_rel intrinsic
- _InterlockedOr8_np intrinsic
- _InterlockedOr64_nf intrinsic
- _InterlockedOr_HLERelease intrinsic
- _InterlockedOr16_np intrinsic
- InterlockedOr intrinsic
- _InterlockedOr8_nf intrinsic
- _InterlockedOr16_nf intrinsic
- _InterlockedOr8_acq intrinsic
- _InterlockedOr64 intrinsic
- _InterlockedOr16 intrinsic
- _InterlockedOr64_acq intrinsic
- _InterlockedOr64_HLEAcquire intrinsic
- _InterlockedOr_np intrinsic
- _InterlockedOr64_rel intrinsic
- _InterlockedOr64_np intrinsic
- _InterlockedOr_rel intrinsic
- _InterlockedOr8 intrinsic
- _InterlockedOr16_acq intrinsic
- _InterlockedOr16_rel intrinsic
- _InterlockedOr_HLEAcquire intrinsic
ms.assetid: 5f265240-7af8-44b7-b952-19f3a9c56186
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d00821b3698883933c464178a06ecffcb5b8fbd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="interlockedor-intrinsic-functions"></a>_InterlockedOr vnitřní funkce
**Konkrétní Microsoft**  
  
 Proveďte atomic bitový nebo operaci na proměnné, které jsou sdíleny více vlákny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
long _InterlockedOr(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedOr_acq(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedOr_HLEAcquire(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedOr_HLERelease(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedOr_nf(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedOr_np(  
   long volatile * Value,  
   long Mask  
);  
long _InterlockedOr_rel(  
   long volatile * Value,  
   long Mask  
);  
char _InterlockedOr8(  
   char volatile * Value,  
   long Mask  
);  
char _InterlockedOr8_acq(  
   char volatile * Value,  
   char Mask  
);  
char _InterlockedOr8_nf(  
   char volatile * Value,  
   char Mask  
);  
char _InterlockedOr8_np(  
   char volatile * Value,  
   char Mask  
);  
char _InterlockedOr8_rel(  
   char volatile * Value,  
   char Mask  
);  
short _InterlockedOr16(  
   short volatile * Value,  
   short Mask  
);  
short _InterlockedOr16_acq(  
   short volatile * Value,  
   short Mask  
);  
short _InterlockedOr16_nf(  
   short volatile * Value,  
   short Mask  
);  
short _InterlockedOr16_np(  
   short volatile * Value,  
   short Mask  
);  
short _InterlockedOr16_rel(  
   short volatile * Value,  
   short Mask  
);  
__int64 _InterlockedOr64(  
   __int64 volatile * Value,  
   __int64 Mask  
);  
__int64 _InterlockedOr64_acq(  
   __int64 volatile * Value,  
   __int64 Mask  
);   
__int64 _InterlockedOr64_HLEAcquire(  
   __int64 volatile * Value,  
   __int64 Mask  
);  
__int64 _InterlockedOr64_HLERelease(  
   __int64 volatile * Value,  
   __int64 Mask  
);   
__int64 _InterlockedOr64_nf(  
   __int64 volatile * Value,  
   __int64 Mask  
);  
__int64 _InterlockedOr64_np(  
   __int64 volatile * Value,  
   __int64 Mask  
);  
__int64 _InterlockedOr64_rel(  
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
 První parametr ukazuje původní hodnotu.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|Záhlaví|  
|---------------|------------------|------------|  
|`_InterlockedOr`, `_InterlockedOr8`, `_InterlockedOr16`, `_InterlockedOr64`|x86 ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
|`_InterlockedOr_acq`, `_InterlockedOr_nf`, `_InterlockedOr_rel`, `_InterlockedOr8_acq`, `_InterlockedOr8_nf`, `_InterlockedOr8_rel`, `_InterlockedOr16_acq`, `_InterlockedOr16_nf`, `_InterlockedOr16_rel`, `_InterlockedOr64_acq`, `_InterlockedOr64_nf`, `_InterlockedOr64_rel`|ARM|\<intrin.h >|  
|`_InterlockedOr_np`, `_InterlockedOr8_np`, `_InterlockedOr16_np`, `_InterlockedOr64_np`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
|`_InterlockedOr_HLEAcquire`, `_InterlockedOr_HLERelease`, `_InterlockedOr64_HLEAcquire`, `_InterlockedOr64_HLERelease`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h >|  
  
## <a name="remarks"></a>Poznámky  
 Číslo názvu jednotlivé funkce určuje velikost bit argumenty.  
  
 Na platformách ARM použít vnitřní funkce s `_acq` a `_rel` přípony, pokud potřebujete získat a vydání sémantikou, například na začátku a konci kritické části. ARM – vnitřní prvky s `_nf` přípony ("žádné ochranná") nefungují jako bariéry paměti.  
  
 Vnitřní funkce s `_np` operaci možné předběžné načtení z vkládání kompilátorem zabránit přípony ("žádné předběžné načtení").  
  
 Na platformách Intel, které podporují pokyny hardwaru zámku Elision (HLE), vnitřní funkce s `_HLEAcquire` a `_HLERelease` přípony zahrnují nápovědu pro procesor, které můžou urychlit výkonu odstraněním krok zápisu zámku v hardwaru. Pokud tyto – vnitřní prvky se označují jako na platformách, které nepodporují HLE, pomocný parametr bude ignorován.  
  
## <a name="example"></a>Příklad  
  
```  
// _InterlockedOr.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_InterlockedOr)  
  
int main()  
{  
        long data1 = 0xFF00FF00;  
        long data2 = 0x00FFFF00;  
        long retval;  
        retval = _InterlockedOr(&data1, data2);  
        printf_s("0x%x 0x%x 0x%x", data1, data2, retval);   
}  
```  
  
```Output  
0xffffff00 0xffff00 0xff00ff00  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Konflikty s kompilátorem x86](../build/conflicts-with-the-x86-compiler.md)