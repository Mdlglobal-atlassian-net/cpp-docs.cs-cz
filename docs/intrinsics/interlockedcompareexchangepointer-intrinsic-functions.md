---
title: Vnitřní funkce _InterlockedCompareExchangePointer
ms.date: 09/02/2019
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
ms.openlocfilehash: c0a0083c19df51d2d2eccb7a7bbf6521303c1f85
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222032"
---
# <a name="_interlockedcompareexchangepointer-intrinsic-functions"></a>Vnitřní funkce _InterlockedCompareExchangePointer

**Specifické pro společnost Microsoft**

Provede atomickou operaci, která uloží `Exchange` adresu `Destination` do `Destination` adresy, pokud `Comparand` je adresa a adresa shodná.

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Parametry

*Tabulka*\
[in, out] Ukazatel na ukazatel na cílovou hodnotu. Znaménko je ignorováno.

*Výměn*\
pro Ukazatel Exchange Znaménko je ignorováno.

*Operand porovnávání*\
pro Ukazatel na porovnání s cílem. Znaménko je ignorováno.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota je počáteční hodnota cíle.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_InterlockedCompareExchangePointer`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedCompareExchangePointer_acq`, `_InterlockedCompareExchangePointer_nf`, `_InterlockedCompareExchangePointer_rel`|ARM, ARM64|\<iiintrin.h>|
|`_InterlockedCompareExchangePointer_HLEAcquire`, `_InterlockedCompareExchangePointer_HLERelease`|x86, x64|\<immintrin.h>|

## <a name="remarks"></a>Poznámky

`_InterlockedCompareExchangePointer`provede atomické porovnání `Destination` adresy `Comparand` s adresou. Pokud se `Comparand` `Exchange` adresa rovná adrese, bude adresa uložená v adrese určené parametrem `Destination`. `Destination` V opačném případě se neprovede žádná operace.

`_InterlockedCompareExchangePointer`poskytuje vnitřní podporu kompilátoru pro funkci Win32 Windows SDK [InterlockedCompareExchangePointer](/windows-hardware/drivers/ddi/content/wdm/nf-wdm-interlockedcompareexchangepointer) .

Příklad použití `_InterlockedCompareExchangePointer`naleznete v tématu [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).

Pokud potřebujete sémantiku získání a vydání, jako `_acq` na `_rel` začátku a na konci kritického oddílu, používejte na platformách ARM vnitřní funkce a přípony. Vnitřní objekty ARM s `_nf` příponou (bez plotu) nefungují jako bariéra paměti.

Vnitřní objekty s `_np` příponou ("bez předběžného navýšení") brání v tom, aby kompilátor vložil možné operace předběžného načtení.

Na platformách Intel, které podporují pokyny Elizi (hardware Lock), vnitřní `_HLEAcquire` funkce a `_HLERelease` přípona obsahují nápovědu pro procesor, který může urychlit odstranění zámku v případě hardwarového zápisu. Pokud jsou tyto vnitřní objekty volány na platformách, které nepodporují HLE, bude pomocný parametr ignorován.

Tyto rutiny jsou k dispozici pouze jako vnitřní objekty.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Klíčová slova](../cpp/keywords-cpp.md)
