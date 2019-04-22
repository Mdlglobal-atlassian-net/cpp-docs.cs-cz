---
title: _InterlockedExchangePointer Intrinsic Functions
ms.date: 12/17/2018
f1_keywords:
- _InterlockedExchangePointer_cpp
- _InterlockedExchangePointer_rel
- _InterlockedExchangePointer_nf
- _InterlockedExchangePointer_HLERelease
- _InterlockedExchangePointer_acq
- _InterlockedExchangePointer
- _InterlockedExchangePointer_acq_cpp
- _InterlockedExchangePointer_HLEAcquire
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
ms.openlocfilehash: 1f6e66ae4d5524518c3388f5af843cc15f65da50
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024527"
---
# <a name="interlockedexchangepointer-intrinsic-functions"></a>_InterlockedExchangePointer Intrinsic Functions

**Microsoft Specific**

Proveďte operaci atomické exchange, který zkopíruje adresu předanou jako druhý argument první a vrátí původní adresu první.

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

*Cíl*<br/>
[out v] Ukazatel na ukazatel na hodnotu k exchangi. Funkce nastaví hodnotu `Value` a vrátí původní hodnotu.

*Hodnota*<br/>
[in] Hodnota mají vyměnit s hodnotou odkazované `Target`.

## <a name="return-value"></a>Návratová hodnota

Funkce vrátí počáteční hodnotu, na které odkazuje `Target`.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_InterlockedExchangePointer`|x86, ARM, x64|\<intrin.h>|
|`_InterlockedExchangePointer_acq`, `_InterlockedExchangePointer_rel`, `_InterlockedExchangePointer_nf`|ARM|\<intrin.h>|
|`_InterlockedExchangePointer_HLEAcquire`, `_InterlockedExchangePointer_HLERelease`|x64 s podporou HLE|\<immintrin.h>|

Na x86 architektury, `_InterlockedExchangePointer` je makro, které volá `_InterlockedExchange`.

## <a name="remarks"></a>Poznámky

64bitová verze systému parametry jsou 64 bitů a musí být zarovnány na hranice 64-bit; v opačném případě funkce selže. Parametry v 32bitové verzi systému, 32 bitů a musí být zarovnány na hranice 32-bit. Další informace najdete v tématu [zarovnat](../cpp/align-cpp.md).

Na platformách ARM, pomocí vnitřní objekty s `_acq` a `_rel` přípony, pokud potřebujete získat a release sémantiky, jako například na začátku a konci kritický oddíl. Vnitřní s `_nf` jako překážku paměti nepostupuje příponu ("žádná ohrazení").

Na platformách Intel, které podporují pokyny Elize zámek hardwaru (HLE), vnitřní objekty s `_HLEAcquire` a `_HLERelease` přípony zahrnují nápovědu pro procesor, který může zrychlit výkonu odstraněním kroku zámek zápisu v hardwaru. Pokud tyto vnitřní objekty jsou volány na platformách, které nepodporují HLE, doporučení se ignoruje.

Tyto rutiny jsou dostupné jenom jako vnitřní funkce.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Konflikty s kompilátorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)