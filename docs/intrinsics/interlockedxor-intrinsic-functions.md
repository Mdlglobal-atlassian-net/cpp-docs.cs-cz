---
title: Vnitřní funkce _InterlockedXor
ms.date: 09/02/2019
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
helpviewer_keywords:
- InterlockedXor intrinsic
- _InterlockedXor64 intrinsic
- InterlockedXor64 intrinsic
- _InterlockedXor intrinsic
ms.assetid: faef1796-cb5a-4430-b1e2-9d5eaf9b4a91
ms.openlocfilehash: 22cb9edd5fa4ffd8ffae7363ab07dc48f519fff0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221901"
---
# <a name="_interlockedxor-intrinsic-functions"></a>Vnitřní funkce _InterlockedXor

**Specifické pro společnost Microsoft**

Provedení atomicky vyhrazené operace OR (XOR) na proměnné sdílené více vlákny.

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Parametry

*Osa*\
[in, out] Ukazatel na první operand, který má být nahrazen výsledkem.

*Zrušit*\
pro Druhý operand.

## <a name="return-value"></a>Návratová hodnota

Původní hodnota prvního operandu.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_InterlockedXor`, `_InterlockedXor8`, `_InterlockedXor16`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedXor64`|ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedXor_acq`, `_InterlockedXor_nf`, `_InterlockedXor_rel`, `_InterlockedXor8_acq`, `_InterlockedXor8_nf`, `_InterlockedXor8_rel`, `_InterlockedXor16_acq`, `_InterlockedXor16_nf`, `_InterlockedXor16_rel`, `_InterlockedXor64_acq`, `_InterlockedXor64_nf`, `_InterlockedXor64_rel`,|ARM, ARM64|\<intrin.h>|
|`_InterlockedXor_np`, `_InterlockedXor8_np`, `_InterlockedXor16_np`, `_InterlockedXor64_np`|x64|\<intrin.h>|
|`_InterlockedXor_HLEAcquire`, `_InterlockedXor_HLERelease`|x86, x64|\<immintrin.h>|
|`_InterlockedXor64_HLEAcquire`, `_InterlockedXor64_HLERelease`|x64|\<immintrin.h>|

## <a name="remarks"></a>Poznámky

Číslo v názvu každé funkce Určuje bitovou velikost argumentů.

Pokud potřebujete sémantiku získání a vydání, jako `_acq` na `_rel` začátku a na konci kritického oddílu, používejte na platformách ARM vnitřní funkce a přípony. Vnitřní objekty ARM s `_nf` příponou (bez plotu) nefungují jako bariéra paměti.

Vnitřní objekty s `_np` příponou ("bez předběžného navýšení") brání v tom, aby kompilátor vložil možné operace předběžného načtení.

Na platformách Intel, které podporují pokyny Elizi (hardware Lock), vnitřní `_HLEAcquire` funkce a `_HLERelease` přípona obsahují nápovědu pro procesor, který může urychlit odstranění zámku v případě hardwarového zápisu. Pokud jsou tyto vnitřní objekty volány na platformách, které nepodporují HLE, bude pomocný parametr ignorován.

## <a name="example"></a>Příklad

```cpp
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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Konflikty s kompilátorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
