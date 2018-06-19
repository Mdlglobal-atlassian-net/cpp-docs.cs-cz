---
title: Vnitřní funkce _InterlockedExchangePointer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedExchangePointer_cpp
- _InterlockedExchangePointer_rel
- _InterlockedExchangePointer_nf
- _InterlockedExchangePointer_HLERelease
- _InterlockedExchangePointer_acq
- _InterlockedExchangePointer
- _InterlockedExchangePointer_acq_cpp
- _InterlockedExchangePointer_HLEAcquire
dev_langs:
- C++
helpviewer_keywords:
- _InterlockedExchangePointer_rel intrinsic
- _InterlockedExchangePointer_HLERelease intrinsic
- _InterlockedExchangePointer intrinsic
- _InterlockedExchangePointer_nf intrinsic
- _InterlockedExchangePointer_acq intrinsic
- _InterlockedExchangePointer_HLEAcquire intrinsic
- InterlockedExchangePointer_acq intrinsic
- InterlockedExchangePointer intrinsic
ms.assetid: 0eaca0b0-d79e-406b-892d-b3b462c50bbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8482b7d5b21c113001b702e00f406b9a3fcfd9c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334935"
---
# <a name="interlockedexchangepointer-intrinsic-functions"></a>_InterlockedExchangePointer vnitřní funkce
**Konkrétní Microsoft**  
  
 Proveďte operaci atomic exchange, který zkopíruje adresu předané jako druhý argument do první a vrátí původní adresu prvního.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void * _InterlockedExchangePointer(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_acq(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_rel(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_nf(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_HLEAcquire(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_HLERelease(  
   void * volatile * Target,  
   void * Value  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [ve out] `Target`  
 Ukazatel na ukazatel na hodnotu na exchange. Funkce nastaví na hodnotu `Value` a vrátí původní hodnotu.  
  
 [v] `Value`  
 Hodnota, která má být vyměňují s hodnotou na kterou odkazuje `Target`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí počáteční hodnotu, na kterou odkazuje `Target`.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|Záhlaví|  
|---------------|------------------|------------|  
|`_InterlockedExchangePointer`|x86 ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
|`_InterlockedExchangePointer_acq`, `_InterlockedExchangePointer_rel`, `_InterlockedExchangePointer_nf`|ARM|\<intrin.h >|  
|`_InterlockedExchangePointer_HLEAcquire`, `_InterlockedExchangePointer_HLERelease`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] s podporou HLE|\<immintrin.h >|  
  
 Na x86 architekturu, `_InterlockedExchangePointer` je makro, který volá `_InterlockedExchange`.  
  
## <a name="remarks"></a>Poznámky  
 Na 64bitovém systému parametry jsou 64bitová verze a musí být zarovnána na hranicích 64-bit; Funkce, jinak selže. Na 32bitové verzi systému parametry jsou 32bitová verze a musí být zarovnána na hranicích 32-bit. Další informace najdete v tématu [zarovnat](../cpp/align-cpp.md).  
  
 Na platformách ARM použít vnitřní funkce s `_acq` a `_rel` přípony, pokud potřebujete získat a vydání sémantikou, například na začátku a konci kritické části. Vnitřní funkce s `_nf` přípony ("žádné ochranná") není fungovat jako bariéry paměti.  
  
 Na platformách Intel, které podporují pokyny hardwaru zámku Elision (HLE), vnitřní funkce s `_HLEAcquire` a `_HLERelease` přípony zahrnují nápovědu pro procesor, které můžou urychlit výkonu odstraněním krok zápisu zámku v hardwaru. Pokud tyto – vnitřní prvky se označují jako na platformách, které nepodporují HLE, pomocný parametr bude ignorován.  
  
 Tyto rutiny jsou dostupné jen jako vnitřní funkce.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Konflikty s kompilátorem x86](../build/conflicts-with-the-x86-compiler.md)