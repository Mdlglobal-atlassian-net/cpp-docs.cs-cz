---
title: vnitřní funkce _interlockedbittestandset | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _interlockedbittestandset_cpp
- _interlockedbittestandset_HLEAcquire
- _interlockedbittestandset64
- _interlockedbittestandset
- _interlockedbittestandset_rel
- _interlockedbittestandset64_HLEAcquire
- _interlockedbittestandset_HLERelease
- _interlockedbittestandset_acq
- _interlockedbittestandset_nf
- _interlockedbittestandset64_cpp
- _interlockedbittestandset64_HLERelease
dev_langs:
- C++
helpviewer_keywords:
- _interlockedbittestandset intrinsic
- _interlockedbittestandset64 intrinsic
- lock_bts instruction
ms.assetid: b1b7e334-53ea-48cf-ba60-5fa3ef51a1fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5327470057928466c1aede37205ac4f35175b899
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712215"
---
# <a name="interlockedbittestandset-intrinsic-functions"></a>vnitřní funkce _interlockedbittestandset
**Specifické pro Microsoft**  
  
 Generovat instrukce, který zkoumá vlastnost bit `b` adresy `a` a vrátí jeho aktuální hodnotu před nastavením na hodnotu 1.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char _interlockedbittestandset(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_acq(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_HLEAcquire(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_HLERelease(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_nf(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_rel(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset64(  
   __int64 *a,  
   __int64 b  
);  
unsigned char _interlockedbittestandset64_HLEAcquire(  
   __int64 *a,  
   __int64 b  
);  
unsigned char _interlockedbittestandset64_HLERelease(  
   __int64 *a,  
   __int64 b  
);  
```  
  
#### <a name="parameters"></a>Parametry  
*a*<br/>
[in] Ukazatel paměti prozkoumat.  
  
*b*<br/>
[in] Bitová pozice pro testování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota na pozici bitu `b` předtím, než je nastavena.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|Záhlaví|  
|---------------|------------------|------------|  
|`_interlockedbittestandset`|x86, ARM, x64|\<intrin.h >|  
|`_interlockedbittestandset_acq`, `_interlockedbittestandset_nf`, `_interlockedbittestandset_rel`|ARM|\<intrin.h >|  
|`_interlockedbittestandset_HLEAcquire`, `_interlockedbittestandset_HLERelease`|x86, x64|\<immintrin.h >|  
|`_interlockedbittestandset64`|x64|\<intrin.h >|  
|`_interlockedbittestandset64_HLEAcquire`, `_interlockedbittestandset64_HLERelease`|x64|\<immintrin.h >|  
  
## <a name="remarks"></a>Poznámky  
 Na x86 a x64 procesory, použijte tyto vnitřní objekty `lock bts` instrukce ke čtení a zadané bit nastaven na hodnotu 1. Je atomická operace.  
  
 Na procesorech ARM, pomocí vnitřní objekty s `_acq` a `_rel` přípony pro získání a uvolnění sémantiky, jako například na začátku a konci kritický oddíl. Vnitřní objekty ARM pomocí `_nf` příponu ("žádná ohrazení") nefungují jako překážku paměti.  
  
 Na procesorech Intel, které podporují pokyny Elize zámek hardwaru (HLE), vnitřní objekty s `_HLEAcquire` a `_HLERelease` přípony zahrnují nápovědu pro procesor, který může zrychlit výkonu odstraněním kroku zámek zápisu v hardwaru. Pokud tyto vnitřní objekty jsou volány u procesorů, které nepodporují HLE, doporučení se ignoruje.  
  
 Tyto rutiny jsou dostupné jenom jako vnitřní funkce.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Konflikty s kompilátorem x86](../build/conflicts-with-the-x86-compiler.md)