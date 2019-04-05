---
title: Vnitřní funkce _InterlockedExchangeAdd
ms.date: 12/17/2018
f1_keywords:
- _InterlockedExchangeAdd64_nf
- _InterlockedExchangeAdd64_rel
- _InterlockedExchangeAdd16_rel
- _InterlockedExchangeAdd_acq
- _InterlockedExchangeAdd_nf
- _InterlockedExchangeAdd_rel
- _InterlockedExchangeAdd8_acq
- _InterlockedExchangeAdd16_nf
- _InterlockedExchangeAdd_acq_cpp
- _InterlockedExchangeAdd64_acq_cpp
- _InterlockedExchangeAdd16_acq
- _InterlockedExchangeAdd_HLERelease
- _InterlockedExchangeAdd64_cpp
- _InterlockedExchangeAdd64_HLERelease
- _InterlockedExchangeAdd64_acq
- _InterlockedExchangeAdd8
- _InterlockedExchangeAdd64
- _InterlockedExchangeAdd8_nf
- _InterlockedExchangeAdd16
- _InterlockedExchangeAdd64_rel_cpp
- _InterlockedExchangeAdd_cpp
- _InterlockedExchangeAdd8_rel
- _InterlockedExchangeAdd_HLEAcquire
- _InterlockedExchangeAdd64_HLEAcquire
- _InterlockedExchangeAdd
helpviewer_keywords:
- _InterlockedExchangeAdd8_nf intrinsic
- InterlockedExchangeAdd64_acq intrinsic
- _InterlockedExchangeAdd8_acq intrinsic
- _InterlockedExchangeAdd64 intrinsic
- _InterlockedExchangeAdd intrinsic
- _InterlockedExchangeAdd8_rel intrinsic
- _InterlockedExchangeAdd_acq intrinsic
- _InterlockedExchangeAdd_HLEAcquire intrinsic
- _InterlockedExchangeAdd8 intrinsic
- _InterlockedExchangeAdd_rel intrinsic
- _InterlockedExchangeAdd64_HLERelease intrinsic
- _InterlockedExchangeAdd64_nf intrinsic
- InterlockedExchangeAdd_rel intrinsic
- InterlockedExchangeAdd intrinsic
- _InterlockedExchangeAdd_nf intrinsic
- _InterlockedExchangeAdd16_rel intrinsic
- InterlockedExchangeAdd_acq intrinsic
- _InterlockedExchangeAdd64_HLEAcquire intrinsic
- _InterlockedExchangeAdd16 intrinsic
- _InterlockedExchangeAdd64_acq intrinsic
- InterlockedExchangeAdd64_rel intrinsic
- _InterlockedExchangeAdd16_acq intrinsic
- InterlockedExchangeAdd64 intrinsic
- _InterlockedExchangeAdd_HLERelease intrinsic
- _InterlockedExchangeAdd16_nf intrinsic
- _InterlockedExchangeAdd64_rel intrinsic
ms.assetid: 25809e1f-9c60-4492-9f7c-0fb59c8d13d2
ms.openlocfilehash: 2cffd5a088c4b3c67441e79bc04bd709be6bf8ef
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039173"
---
# <a name="interlockedexchangeadd-intrinsic-functions"></a>Vnitřní funkce _InterlockedExchangeAdd

**Specifické pro Microsoft**

Poskytuje vnitřní podporu kompilátoru pro sadu SDK Windows Win32 [vnitřní funkce _InterlockedExchangeAdd](../intrinsics/interlockedexchangeadd-intrinsic-functions.md) funkce.

## <a name="syntax"></a>Syntaxe

```
long _InterlockedExchangeAdd(
   long volatile * Addend,
   long Value
);
long _InterlockedExchangeAdd_acq(
   long volatile * Addend,
   long Value
);
long _InterlockedExchangeAdd_rel(
   long volatile * Addend,
   long Value
);
long _InterlockedExchangeAdd_nf(
   long volatile * Addend,
   long Value
);
long _InterlockedExchangeAdd_HLEAcquire(
   long volatile * Addend,
   long Value
);
long _InterlockedExchangeAdd_HLERelease(
   long volatile * Addend,
   long Value
);
char _InterlockedExchangeAdd8(
   char volatile * Addend,
   char Value
);
char _InterlockedExchangeAdd8_acq(
   char volatile * Addend,
   char Value
);
char _InterlockedExchangeAdd8_rel(
   char volatile * Addend,
   char Value
);
char _InterlockedExchangeAdd8_nf(
   char volatile * Addend,
   char Value
);
short _InterlockedExchangeAdd16(
   short volatile * Addend,
   short Value
);
short _InterlockedExchangeAdd16_acq(
   short volatile * Addend,
   short Value
);
short _InterlockedExchangeAdd16_rel(
   short volatile * Addend,
   short Value
);
short _InterlockedExchangeAdd16_nf(
   short volatile * Addend,
   short Value
);
__int64 _InterlockedExchangeAdd64(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedExchangeAdd64_acq(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedExchangeAdd64_rel(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedExchangeAdd64_nf(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedExchangeAdd64_HLEAcquire(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedExchangeAdd64_HLERelease(
   __int64 volatile * Addend,
   __int64 Value
);
```

#### <a name="parameters"></a>Parametry

*Sčítanec*<br/>
[out v] Hodnota, která má být přidán do; výsledek součtu nahrazena.

*Hodnota*<br/>
[in] Hodnota k přidání.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota je počáteční hodnota proměnné, na které odkazují `Addend` parametru.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_InterlockedExchangeAdd`, `_InterlockedExchangeAdd8`, `_InterlockedExchangeAdd16`, `_InterlockedExchangeAdd64`|x86, ARM, x64|\<intrin.h>|
|`_InterlockedExchangeAdd_acq`, `_InterlockedExchangeAdd_rel`, `_InterlockedExchangeAdd_nf`, `_InterlockedExchangeAdd8_acq`, `_InterlockedExchangeAdd8_rel`, `_InterlockedExchangeAdd8_nf`,`_InterlockedExchangeAdd16_acq`, `_InterlockedExchangeAdd16_rel`, `_InterlockedExchangeAdd16_nf`, `_InterlockedExchangeAdd64_acq`, `_InterlockedExchangeAdd64_rel`, `_InterlockedExchangeAdd64_nf`|ARM|\<intrin.h>|
|`_InterlockedExchangeAdd_HLEAcquire`, `_InterlockedExchangeAdd_HLERelease`, `_InterlockedExchangeAdd64_HLEAcquire`, `_InterlockedExchangeAdd64_HLErelease`|x86, x64|\<immintrin.h>|

## <a name="remarks"></a>Poznámky

Existuje několik variant na `_InterlockedExchangeAdd` , která se liší v závislosti na datové typy, které zahrnují a zda specifické pro procesor získat nebo se používá sémantiku vydání.

Při `_InterlockedExchangeAdd` funkce se používá na 32bitové celé číslo hodnoty `_InterlockedExchangeAdd8` pracuje hodnoty 8bitové celé číslo, `_InterlockedExchangeAdd16` pracuje hodnoty 16bitové celé číslo a `_InterlockedExchangeAdd64` pracuje na 64bitové celočíselné hodnoty.

Na platformách ARM, pomocí vnitřní objekty s `_acq` a `_rel` přípony, pokud potřebujete získat a release sémantiky, jako například na začátku a konci kritický oddíl. Vnitřní objekty s `_nf` příponu ("žádná ohrazení") nefungují jako překážku paměti.

Na platformách Intel, které podporují pokyny Elize zámek hardwaru (HLE), vnitřní objekty s `_HLEAcquire` a `_HLERelease` přípony zahrnují nápovědu pro procesor, který může zrychlit výkonu odstraněním kroku zámek zápisu v hardwaru. Pokud tyto vnitřní objekty jsou volány na platformách, které nepodporují HLE, doporučení se ignoruje.

Tyto rutiny jsou dostupné jenom jako vnitřní funkce. Proto jsou vnitřní Určuje, zda nebo Ne [/Oi](../build/reference/oi-generate-intrinsic-functions.md) nebo [#pragma intrinsic](../preprocessor/intrinsic.md) se používá. Není možné použít [#pragma funkce](../preprocessor/function-c-cpp.md) na těchto vnitřních objektů.

## <a name="example"></a>Příklad

Pro ukázku toho, jak používat `_InterlockedExchangeAdd`, naleznete v tématu [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).

**END Specifické pro Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[klíčová slova](../cpp/keywords-cpp.md)<br/>
[Konflikty s kompilátorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)