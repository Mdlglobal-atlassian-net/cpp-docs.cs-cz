---
title: vnitřní funkce _interlockedbittestandreset
ms.date: 09/02/2019
f1_keywords:
- _interlockedbittestandreset_rel
- _interlockedbittestandreset64
- _interlockedbittestandreset64_acq
- _interlockedbittestandreset64_nf
- _interlockedbittestandreset64_rel
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
ms.openlocfilehash: 419d7f800d603a8beca5c8ccb0f9c8f8b3bfcfdb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222069"
---
# <a name="_interlockedbittestandreset-intrinsic-functions"></a>vnitřní funkce _interlockedbittestandreset

**Specifické pro společnost Microsoft**

Vygeneruje instrukci pro nastavení `b` bitu adresy `a` na nulu a vrátí původní hodnotu.

## <a name="syntax"></a>Syntaxe

```C
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
unsigned char _interlockedbittestandreset64_acq(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_nf(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_rel(
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

### <a name="parameters"></a>Parametry

*určitého*\
pro Ukazatel na paměť, kterou chcete prošetřit.

*b*\
pro Bitová pozice, která se má testovat

## <a name="return-value"></a>Návratová hodnota

Původní hodnota bitu na pozici určené parametrem `b`.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_interlockedbittestandreset`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_interlockedbittestandreset_acq`, `_interlockedbittestandreset_nf`, `_interlockedbittestandreset_rel`|ARM, ARM64|\<intrin.h>|
|`_interlockedbittestandreset64_acq`, `_interlockedbittestandreset64_nf`, `_interlockedbittestandreset64_rel`|ARM64|\<intrin.h>|
|`_interlockedbittestandreset_HLEAcquire`, `_interlockedbittestandreset_HLERelease`|x86, x64|\<immintrin.h>|
|`_interlockedbittestandreset64`|x64, ARM64|\<intrin.h>|
|`_interlockedbittestandreset64_HLEAcquire`, `_interlockedbittestandreset64_HLERelease`|x64|\<immintrin.h>|

## <a name="remarks"></a>Poznámky

U procesorů x86 a x64 tyto vnitřní funkce používají `lock btr` instrukci, která čte a nastavuje v atomické operaci v zadaném bitu hodnotu nula.

Na procesorech ARM používejte vnitřní `_acq` funkce a `_rel` přípony pro získání a vydání sémantiky, jako například na začátku a konci kritické části. Vnitřní objekty ARM s `_nf` příponou (bez plotu) nefungují jako bariéra paměti.

V procesorech Intel, které podporují pokyny Elizi (hardware Lock), vnitřní `_HLEAcquire` funkce a `_HLERelease` přípony obsahují nápovědu pro procesor, který může urychlit odstranění zámku v případě hardwarového zápisu. Pokud jsou tyto vnitřní objekty volány u procesorů, které nepodporují HLE, bude pomocný parametr ignorován.

Tyto rutiny jsou k dispozici pouze jako vnitřní objekty.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Konflikty s kompilátorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
