---
title: Vnitřní funkce _InterlockedExchangePointer
ms.date: 09/02/2019
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
ms.openlocfilehash: 1402dcf5279658c1364b59a324d988129bc841d8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217626"
---
# <a name="_interlockedexchangepointer-intrinsic-functions"></a>Vnitřní funkce _InterlockedExchangePointer

**Specifické pro společnost Microsoft**

Provede operaci atoming Exchange, která zkopíruje adresu předanou jako druhý argument do prvního argumentu a vrátí původní adresu prvního.

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Parametry

*Cílové*\
[in, out] Ukazatel na ukazatel na hodnotu pro výměnu. Funkce nastaví hodnotu na *hodnotu* a vrátí její předchozí hodnotu.

*Osa*\
pro Hodnota, která se má vyměňovat s hodnotou, na kterou se odkazuje v *cíli*

## <a name="return-value"></a>Návratová hodnota

Funkce vrátí počáteční hodnotu, na kterou ukazuje *cíl*.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_InterlockedExchangePointer`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedExchangePointer_acq`, `_InterlockedExchangePointer_rel`, `_InterlockedExchangePointer_nf`|ARM, ARM64|\<intrin.h>|
|`_InterlockedExchangePointer_HLEAcquire`, `_InterlockedExchangePointer_HLERelease`|x64|\<immintrin.h>|

V architektuře `_InterlockedExchangePointer` x86 je makro, které volá `_InterlockedExchange`.

## <a name="remarks"></a>Poznámky

V 64ovém systému jsou parametry 64 bitů a musí být zarovnány na hranici 64-bit. V opačném případě se funkce nezdařila. V 32ovém systému jsou parametry 32 bitů a musí být zarovnány na hranici 32-bit. Další informace najdete v tématu [Zarovnání](../cpp/align-cpp.md).

Pokud potřebujete sémantiku získání a vydání, jako `_acq` na `_rel` začátku a na konci kritického oddílu, používejte na platformách ARM vnitřní funkce a přípony. Vnitřní přípona s `_nf` příponou (bez plotu) nefunguje jako bariéra paměti.

Na platformách Intel, které podporují pokyny Elizi (hardware Lock), vnitřní `_HLEAcquire` funkce a `_HLERelease` přípona obsahují nápovědu pro procesor, který může urychlit odstranění zámku v případě hardwarového zápisu. Pokud jsou tyto vnitřní objekty volány na platformách, které nepodporují HLE, bude pomocný parametr ignorován.

Tyto rutiny jsou k dispozici pouze jako vnitřní objekty.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Konflikty s kompilátorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
