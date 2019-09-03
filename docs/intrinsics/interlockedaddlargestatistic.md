---
title: _InterlockedAddLargeStatistic
ms.date: 09/02/2019
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: de8c5b7dfd2462dddcb98324ebacc44c8148d85e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222086"
---
# <a name="_interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Specifické pro společnost Microsoft**

Provede propojené přizpůsobování, ve kterém první operand je 64 hodnota.

## <a name="syntax"></a>Syntaxe

```C
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

### <a name="parameters"></a>Parametry

*Sčítanec*\
[in, out] Ukazatel na první operand operace přidání. Hodnota, na kterou se odkazuje, je nahrazena výsledkem přidání.

*Osa*\
pro Druhý operand; hodnota, která se má přidat do prvního operandu.

## <a name="return-value"></a>Návratová hodnota

Hodnota druhého operandu.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

`_InterlockedAddLargeStatistic` Vnitřní operace není atomická, protože je implementována jako dvě samostatné uzamčené instrukce. Atomová 64 čtení, ke kterému dochází v jiném vlákně během provádění vnitřního, může způsobit čtení nekonzistentní hodnoty.

`_InterlockedAddLargeStatistic`chová se jako bariéra pro čtení i zápis. Další informace najdete v tématu [_ReadWriteBarrier](../intrinsics/readwritebarrier.md).

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Konflikty s kompilátorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
