---
title: Vnitřní funkce _InterlockedIncrement
ms.date: 12/17/2018
f1_keywords:
- _InterlockedIncrement_acq
- _InterlockedIncrement16_rel_cpp
- _InterlockedIncrement16_cpp
- _InterlockedIncrement64_rel
- _InterlockedIncrement_rel
- _InterlockedIncrement64_nf
- _InterlockedIncrement16_acq_cpp
- _InterlockedIncrement_rel_cpp
- _InterlockedIncrement64
- _InterlockedIncrement64_rel_cpp
- _InterlockedIncrement16_nf
- _InterlockedIncrement16_rel
- _InterlockedIncrement16_acq
- _InterlockedIncrement_nf
- _InterlockedIncrement_acq_cpp
- _InterlockedIncrement64_cpp
- _InterlockedIncrement64_acq_cpp
- _InterlockedIncrement
- _InterlockedIncrement_cpp
- _InterlockedIncrement64_acq
- _InterlockedIncrement16
helpviewer_keywords:
- _InterlockedIncrement64_rel intrinsic
- _InterlockedIncrement16_rel intrinsic
- InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16 intrinsic
- _InterlockedIncrement16_acq intrinsic
- _InterlockedIncrement_nf intrinsic
- _InterlockedIncrement_rel intrinsic
- _InterlockedIncrement64_nf intrinsic
- InterlockedIncrement_rel intrinsic
- InterlockedIncrement_acq intrinsic
- _InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16_nf intrinsic
- _InterlockedIncrement intrinsic
- _InterlockedIncrement64 intrinsic
- InterlockedIncrement64_rel intrinsic
- InterlockedIncrement64 intrinsic
- InterlockedIncrement16 intrinsic
- _InterlockedIncrement_acq intrinsic
- InterlockedIncrement intrinsic
ms.assetid: 37700615-f372-438b-bcef-d76e11839482
ms.openlocfilehash: 3054a9eab21f6f7ec149f7f1c23c3c40fca3b9e1
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53626929"
---
# <a name="interlockedincrement-intrinsic-functions"></a>Vnitřní funkce _InterlockedIncrement

**Specifické pro Microsoft**

Poskytuje vnitřní podporu kompilátoru pro sadu SDK Windows Win32 [InterlockedIncrement](/windows/desktop/api/winbase/nf-winbase-interlockedincrement) funkce.

## <a name="syntax"></a>Syntaxe

```
long _InterlockedIncrement(
   long * lpAddend
);
long _InterlockedIncrement_acq(
   long * lpAddend
);
long _InterlockedIncrement_rel(
   long * lpAddend
);
long _InterlockedIncrement_nf(
   long * lpAddend
);
short _InterlockedIncrement16(
   short * lpAddend
);
short _InterlockedIncrement16_acq(
   short * lpAddend
);
short _InterlockedIncrement16_rel(
   short * lpAddend
);
short _InterlockedIncrement16_nf (
   short * lpAddend
);
__int64 _InterlockedIncrement64(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_acq(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_rel(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_nf(
   __int64 * lpAddend
);
```

#### <a name="parameters"></a>Parametry

*lpAddend*<br/>
[out v] Ukazatel na proměnnou se zvýší.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota je výsledná hodnota zvýšena.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_InterlockedIncrement`, `_InterlockedIncrement16`, `_InterlockedIncrement64`|x86, ARM, x64|\<intrin.h >|
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM|\<intrin.h >|

## <a name="remarks"></a>Poznámky

Existuje několik variant na `_InterlockedIncrement` , která se liší v závislosti na datové typy, které zahrnují a zda specifické pro procesor získat nebo se používá sémantiku vydání.

Zatímco `_InterlockedIncrement` funkce se používá na 32bitové celé číslo hodnoty `_InterlockedIncrement16` pracuje hodnoty 16bitové celé číslo a `_InterlockedIncrement64` pracuje na 64bitové celočíselné hodnoty.

Na platformách ARM, pomocí vnitřní objekty s `_acq` a `_rel` přípony, pokud potřebujete získat a release sémantiky, jako například na začátku a konci kritický oddíl. Vnitřní s `_nf` jako překážku paměti nepostupuje příponu ("žádná ohrazení").

Proměnná odkazuje `lpAddend` parametr musí být zarovnány na hranici 32-bit; v opačném případě této funkce nezdaří se s více procesory x86 systémy a systémy x x86. Další informace najdete v tématu [zarovnat](../cpp/align-cpp.md).

Funkce Win32 je deklarována v `Wdm.h` nebo `Ntddk.h`.

Tyto rutiny jsou dostupné jenom jako vnitřní funkce.

## <a name="example"></a>Příklad

Pro ukázku toho, jak používat `_InterlockedIncrement`, naleznete v tématu [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Konflikty s kompilátorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)