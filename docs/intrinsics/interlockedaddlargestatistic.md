---
title: _InterlockedAddLargeStatistic
ms.date: 11/04/2016
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: befcd74c432eb62ab3a718223ada6d0f441e72c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432822"
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Specifické pro Microsoft**

Provádí doplněk interlocked, ve které je první operand hodnotu 64-bit.

## <a name="syntax"></a>Syntaxe

```
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

#### <a name="parameters"></a>Parametry

*Sčítanec*<br/>
[out v] Ukazatel na první operand operace přidání. Hodnota, na které je nahrazena výsledek součtu.

*Hodnota*<br/>
[in] Druhý operand. Hodnota k přidání prvního operandu.

## <a name="return-value"></a>Návratová hodnota

Hodnota druhého operandu.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tomto vnitřní není atomic vzhledem k tomu, že je implementován jako dva samostatné uzamčené pokyny. Atomic čtení 64-bit, nacházející se na jiné vlákno během provádění této vnitřní může vést čtených hodnot.

Tato funkce se chová jako překážku pro čtení i zápis. Další informace najdete v tématu [_ReadWriteBarrier](../intrinsics/readwritebarrier.md).

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Konflikty s kompilátorem x86](../build/conflicts-with-the-x86-compiler.md)