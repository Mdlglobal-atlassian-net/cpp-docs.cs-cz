---
title: vnitřní funkce _interlockedbittestandreset
ms.date: 12/17/2018
f1_keywords:
- _interlockedbittestandreset_rel
- _interlockedbittestandreset64
- _interlockedbittestandreset64_HLERelease
- _interlockedbittestandreset_HLERelease
- _interlockedbittestandreset_HLEAcquire
- _interlockedbittestandreset_acq
- _interlockedbittestandreset_cpp
- _interlockedbittestandreset_nf
- _interlockedbittestandreset64_cpp
- _interlockedbittestandreset64_HLEAcquire
- _interlockedbittestandreset
helpviewer_keywords:
- lock_btr instruction
- _interlockedbittestandreset64 intrinsic
- _interlockedbittestandreset intrinsic
ms.assetid: 9bbb1442-f2e9-4dc2-b0da-97f3de3493b9
ms.openlocfilehash: 54ea8b1ccac15eab600c91302969b606c188dc59
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263721"
---
# <a name="interlockedbittestandreset-intrinsic-functions"></a>vnitřní funkce _interlockedbittestandreset

**Microsoft Specific**

Generuje instrukce, která nastaví bit `b` adresy `a` na nulu a vrátí původní hodnotu.

## <a name="syntax"></a>Syntaxe

```
unsigned char _interlockedbittestandreset(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_acq(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_HLEAcquire(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_HLERelease(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_nf(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_rel(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset64(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_HLEAcquire(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_HLERelease(
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

Původní hodnota bit na určené pozici `b`.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_interlockedbittestandreset`|x86, ARM, x64|\<intrin.h>|
|`_interlockedbittestandreset_acq`, `_interlockedbittestandreset_nf`, `_interlockedbittestandreset_rel`|ARM|\<intrin.h>|
|`_interlockedbittestandreset_HLEAcquire`, `_interlockedbittestandreset_HLERelease`|x86, x64|\<immintrin.h>|
|`_interlockedbittestandreset64`|x64|\<intrin.h>|
|`_interlockedbittestandreset64_HLEAcquire`, `_interlockedbittestandreset64_HLERelease`|x64|\<immintrin.h>|

## <a name="remarks"></a>Poznámky

Na x86 a x64 procesory, použijte tyto vnitřní objekty `lock btr` instrukce, která čte a nastaví zadané bit na hodnotu nula atomické operace.

Na procesorech ARM, pomocí vnitřní objekty s `_acq` a `_rel` přípony pro získání a uvolnění sémantiky, jako například na začátku a konci kritický oddíl. Vnitřní objekty ARM pomocí `_nf` příponu ("žádná ohrazení") nefungují jako překážku paměti.

Na procesorech Intel, které podporují pokyny Elize zámek hardwaru (HLE), vnitřní objekty s `_HLEAcquire` a `_HLERelease` přípony zahrnují nápovědu pro procesor, který může zrychlit výkonu odstraněním kroku zámek zápisu v hardwaru. Pokud tyto vnitřní objekty jsou volány u procesorů, které nepodporují HLE, doporučení se ignoruje.

Tyto rutiny jsou dostupné jenom jako vnitřní funkce.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Konflikty s kompilátorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)