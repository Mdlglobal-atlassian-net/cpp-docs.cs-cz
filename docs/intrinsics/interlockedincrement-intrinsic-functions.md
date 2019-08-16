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
ms.openlocfilehash: 58c71c577e3d87ca72836134a4f895f32170fe7f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509353"
---
# <a name="_interlockedincrement-intrinsic-functions"></a>Vnitřní funkce _InterlockedIncrement

**Specifické pro společnost Microsoft**

Poskytněte vnitřní podporu kompilátoru pro funkci Win32 Windows SDK [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement) .

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
[in, out] Ukazatel na proměnnou, která se má zvýšit.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota je výsledná přírůstková hodnota.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_InterlockedIncrement`, `_InterlockedIncrement16`, `_InterlockedIncrement64`|x86, ARM, x64|\<intrin.h>|
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM|\<intrin.h>|

## <a name="remarks"></a>Poznámky

Existuje několik variant `_InterlockedIncrement` , které se liší v závislosti na datových typech, které zahrnují a na kterých se používají sémantiky získání nebo vydání specifické pro procesor.

`_InterlockedIncrement16` `_InterlockedIncrement64` I když `_InterlockedIncrement` funkce funguje s 32 celočíselnými hodnotami, pracuje na 16bitových celočíselných hodnotách a pracuje na 64 celočíselných hodnotách.

Pokud potřebujete sémantiku získání a vydání, jako `_acq` na `_rel` začátku a na konci kritického oddílu, používejte na platformách ARM vnitřní funkce a přípony. Vnitřní přípona s `_nf` příponou "bez plotu" nefunguje jako bariéra paměti.

Proměnná, na `lpAddend` kterou se odkazuje parametr, musí být zarovnaná na hranici 32. v opačném případě tato funkce selže u víceprocesorových systémů s více procesory a systémy, které nejsou x86. Další informace najdete v tématu [Zarovnání](../cpp/align-cpp.md).

Funkce Win32 je deklarována v `Wdm.h` nebo `Ntddk.h`.

Tyto rutiny jsou k dispozici pouze jako vnitřní objekty.

## <a name="example"></a>Příklad

Ukázku použití `_InterlockedIncrement`naleznete v tématu [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Konflikty s kompilátorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)