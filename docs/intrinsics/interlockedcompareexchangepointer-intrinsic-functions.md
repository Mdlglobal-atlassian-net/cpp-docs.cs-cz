---
title: Vnitřní funkce _InterlockedCompareExchangePointer | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedCompareExchangePointer_HLERelease
- _InterlockedCompareExchangePointer_rel
- _InterlockedCompareExchangePointer_acq_cpp
- _InterlockedCompareExchangePointer
- _InterlockedCompareExchangePointer_cpp
- _InterlockedCompareExchangePointer_np
- _InterlockedCompareExchangePointer_rel_cpp
- _InterlockedCompareExchangePointer_HLEAcquire
- _InterlockedCompareExchangePointer_acq
- _InterlockedCompareExchangePointer_nf
dev_langs:
- C++
helpviewer_keywords:
- InterlockedCompareExchangePointer_acq intrinsic
- _InterlockedCompareExchangePointer_rel intrinsic
- _InterlockedCompareExchangePointer_acq intrinsic
- InterlockedCompareExchangePointer_rel intrinsic
- InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_HLERelease intrinsic
- _InterlockedCompareExchangePointer_HLEAcquire intrinsic
- _InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_nf intrinsic
- _InterlockedCompareExchangePointer_np intrinsic
ms.assetid: 97fde59d-2bf9-42aa-a0fe-a5b6befdd44b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f8ab76252c355bb56a1e2157e0e025a4eddb0d8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596533"
---
# <a name="interlockedcompareexchangepointer-intrinsic-functions"></a>Vnitřní funkce _InterlockedCompareExchangePointer
**Specifické pro Microsoft**  
  
 Provádí atomické operace, která ukládá `Exchange` adresa v `Destination` řešit, pokud `Comparand` a `Destination` adresa jsou stejné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void * _InterlockedCompareExchangePointer (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_acq (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_HLEAcquire (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_HLERelease (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_nf (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_np (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
long _InterlockedCompareExchangePointer_rel (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out v] `Destination`  
 Ukazatel na ukazatel na cílové hodnoty. Znaménko se ignoruje.  
  
 [in] `Exchange`  
 Ukazatel na Exchange. Znaménko se ignoruje.  
  
 [in] `Comparand`  
 Ukazatel na porovnání do cíle. Znaménko se ignoruje.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je počáteční hodnota cíle.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|Záhlaví|  
|---------------|------------------|------------|  
|`_InterlockedCompareExchangePointer`|x86, ARM, x64|\<intrin.h >|  
|`_InterlockedCompareExchangePointer_acq`, `_InterlockedCompareExchangePointer_nf`, `_InterlockedCompareExchangePointer_rel`|ARM|\<iiintrin.h >|  
|`_InterlockedCompareExchangePointer_HLEAcquire`, `_InterlockedCompareExchangePointer_HLERelease`|x86, x64|\<immintrin.h >|  
  
## <a name="remarks"></a>Poznámky  
 `_InterlockedCompareExchangePointer` provádí atomické porovnání `Destination` se zabývat `Comparand` adresu. Pokud `Destination` adresa je rovna `Comparand` adresu, `Exchange` adresa je uložen v adrese `Destination`. V opačném případě je provedena žádná operace.  
  
 `_InterlockedCompareExchangePointer` poskytuje vnitřní podporu kompilátoru pro sadu SDK Windows Win32 [_InterlockedCompareExchangePointer](http://msdn.microsoft.com/library/ff547863.aspx) funkce.  
  
 Příklad použití `_InterlockedCompareExchangePointer`, naleznete v tématu [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).  
  
 Na platformách ARM, pomocí vnitřní objekty s `_acq` a `_rel` přípony, pokud potřebujete získat a release sémantiky, jako například na začátku a konci kritický oddíl. Vnitřní objekty ARM pomocí `_nf` příponu ("žádná ohrazení") nefungují jako překážku paměti.  
  
 Vnitřní objekty s `_np` příponu ("žádná předběžné načtení") zabránit možný předběžné načtení operace nebude vložen kompilátorem.  
  
 Na platformách Intel, které podporují pokyny Elize zámek hardwaru (HLE), vnitřní objekty s `_HLEAcquire` a `_HLERelease` přípony zahrnují nápovědu pro procesor, který může zrychlit výkonu odstraněním kroku zámek zápisu v hardwaru. Pokud tyto vnitřní objekty jsou volány na platformách, které nepodporují HLE, doporučení se ignoruje.  
  
 Tyto rutiny jsou dostupné jenom jako vnitřní funkce.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)