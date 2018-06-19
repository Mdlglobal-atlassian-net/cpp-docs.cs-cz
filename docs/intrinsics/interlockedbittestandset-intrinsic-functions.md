---
title: vnitřní funkce _interlockedbittestandset | Microsoft Docs
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
ms.openlocfilehash: 6789a8e602fded02d4d521be74e602557ebdaefe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340330"
---
# <a name="interlockedbittestandset-intrinsic-functions"></a>_interlockedbittestandset vnitřní funkce
**Konkrétní Microsoft**  
  
 Generovat instrukci, který zkoumá bit `b` adresy `a` a vrátí jeho aktuální hodnotu před jeho nastavení na hodnotu 1.  
  
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
 [v] `a`  
 Ukazatel na paměť pro zjištění.  
  
 [v] `b`  
 Bit pozice pro testování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota bit na pozici `b` předtím, než je nastavený.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|Záhlaví|  
|---------------|------------------|------------|  
|`_interlockedbittestandset`|x86 ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
|`_interlockedbittestandset_acq`, `_interlockedbittestandset_nf`, `_interlockedbittestandset_rel`|ARM|\<intrin.h >|  
|`_interlockedbittestandset_HLEAcquire`, `_interlockedbittestandset_HLERelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h >|  
|`_interlockedbittestandset64`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
|`_interlockedbittestandset64_HLEAcquire`, `_interlockedbittestandset64_HLERelease`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h >|  
  
## <a name="remarks"></a>Poznámky  
 Na x86 a [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] procesory, tyto vnitřní funkce používají `lock bts` instrukce ke čtení a nastaví zadaný bit na 1. Operace je atomic.  
  
 Použijte na procesory ARM – vnitřní prvky s `_acq` a `_rel` přípony pro získání a verze sémantikou, například na začátku a konci kritické části. ARM – vnitřní prvky s `_nf` přípony ("žádné ochranná") nefungují jako bariéry paměti.  
  
 Na procesory Intel, které podporují pokyny hardwaru zámku Elision (HLE), vnitřní funkce s `_HLEAcquire` a `_HLERelease` přípony zahrnují nápovědu pro procesor, které můžou urychlit výkonu odstraněním krok zápisu zámku v hardwaru. Pokud tyto – vnitřní prvky se označují jako u procesorů, které nepodporují HLE, pomocný parametr bude ignorován.  
  
 Tyto rutiny jsou dostupné jen jako vnitřní funkce.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Konflikty s kompilátorem x86](../build/conflicts-with-the-x86-compiler.md)