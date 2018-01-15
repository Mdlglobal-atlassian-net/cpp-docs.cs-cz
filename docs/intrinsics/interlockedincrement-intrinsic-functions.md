---
title: "Vnitřní funkce _InterlockedIncrement | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _InterlockedIncrement_acq
- _InterlockedIncrement16_rel_cpp
- _InterlockedIncrement16_cpp
- _InterlockedIncrement64_rel
- _InterlockedIncrement_rel
- _InterlockedIncrement64_nf
- _InterlockedIncrement16_acq_cpp
- _InterlockedIncrement_rel_cpp
- _InterlockedIncrement64
- _InterlockedIncrement64_rel_cpp
- _InterlockedIncrement16_nf
- _InterlockedIncrement16_rel
- _InterlockedIncrement16_acq
- _InterlockedIncrement_nf
- _InterlockedIncrement_acq_cpp
- _InterlockedIncrement64_cpp
- _InterlockedIncrement64_acq_cpp
- _InterlockedIncrement
- _InterlockedIncrement_cpp
- _InterlockedIncrement64_acq
- _InterlockedIncrement16
dev_langs: C++
helpviewer_keywords:
- _InterlockedIncrement64_rel intrinsic
- _InterlockedIncrement16_rel intrinsic
- InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16 intrinsic
- _InterlockedIncrement16_acq intrinsic
- _InterlockedIncrement_nf intrinsic
- _InterlockedIncrement_rel intrinsic
- _InterlockedIncrement64_nf intrinsic
- InterlockedIncrement_rel intrinsic
- InterlockedIncrement_acq intrinsic
- _InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16_nf intrinsic
- _InterlockedIncrement intrinsic
- _InterlockedIncrement64 intrinsic
- InterlockedIncrement64_rel intrinsic
- InterlockedIncrement64 intrinsic
- InterlockedIncrement16 intrinsic
- _InterlockedIncrement_acq intrinsic
- InterlockedIncrement intrinsic
ms.assetid: 37700615-f372-438b-bcef-d76e11839482
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64866df8d2c0927e35a62b188e1f320cdd0bb2e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="interlockedincrement-intrinsic-functions"></a>_InterlockedIncrement vnitřní funkce
**Konkrétní Microsoft**  
  
 Vnitřní podporují kompilátoru Win32 [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] [InterlockedIncrement](http://msdn.microsoft.com/library/ms683614.aspx) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
long _InterlockedIncrement(  
   long * lpAddend  
);  
long _InterlockedIncrement_acq(  
   long * lpAddend  
);  
long _InterlockedIncrement_rel(  
   long * lpAddend  
);  
long _InterlockedIncrement_nf(  
   long * lpAddend  
);  
short _InterlockedIncrement16(  
   short * lpAddend  
);  
short _InterlockedIncrement16_acq(  
   short * lpAddend  
);  
short _InterlockedIncrement16_rel(  
   short * lpAddend  
);  
short _InterlockedIncrement16_nf (  
   short * lpAddend  
);  
__int64 _InterlockedIncrement64(  
   __int64 * lpAddend  
);  
__int64 _InterlockedIncrement64_acq(  
   __int64 * lpAddend  
);  
__int64 _InterlockedIncrement64_rel(  
   __int64 * lpAddend  
);   
__int64 _InterlockedIncrement64_nf(  
   __int64 * lpAddend  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [ve out]`lpAddend`  
 Ukazatel na proměnnou se zvýší.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je výsledná hodnota zvýšena.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|Záhlaví|  
|---------------|------------------|------------|  
|`_InterlockedIncrement`, `_InterlockedIncrement16`, `_InterlockedIncrement64`|x86 ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM|\<intrin.h >|  
  
## <a name="remarks"></a>Poznámky  
 Existuje několik variant na `_InterlockedIncrement` se používá verzi sémantiku nebo který lišit v závislosti na datové typy, které zahrnují a zda získat specifické pro procesor.  
  
 Když `_InterlockedIncrement` funkce se používá na 32bitové celočíselné hodnoty, `_InterlockedIncrement16` funguje na hodnoty 16bitové celé číslo a `_InterlockedIncrement64` funguje na 64bitové celočíselné hodnoty.  
  
 Na platformách ARM použít vnitřní funkce s `_acq` a `_rel` přípony, pokud potřebujete získat a vydání sémantikou, například na začátku a konci kritické části. Vnitřní funkce s `_nf` přípony ("žádné ochranná") není fungovat jako bariéry paměti.  
  
 Proměnná ukazuje `lpAddend` parametr musí být zarovnána na hranici 32-bit; jinak, tato funkce selže na s více procesory x86 a žádné jiné x86 systémy. Další informace najdete v tématu [zarovnat](../cpp/align-cpp.md).  
  
 Funkce Win32 je deklarován v `Wdm.h` nebo `Ntddk.h`.  
  
 Tyto rutiny jsou dostupné jen jako vnitřní funkce.  
  
## <a name="example"></a>Příklad  
 Příklad, jak pomocí `_InterlockedIncrement`, najdete v části [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Konflikty s kompilátorem x86](../build/conflicts-with-the-x86-compiler.md)