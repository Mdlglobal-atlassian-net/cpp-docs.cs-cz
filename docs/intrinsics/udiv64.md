---
title: _udiv64
ms.date: 09/02/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: 6dabbc94260ef578eb1a58a1b289b4a4654decdd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219676"
---
# <a name="_udiv64"></a>_udiv64

`_udiv64` Vnitřní rozděluje 64 unsigned integer 32-bit unsigned integer. Vrácená hodnota drží podíl a vnitřní Vrátí zbytek prostřednictvím parametru ukazatele. `_udiv64`je **specifická pro společnost Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>Parametry

*podíl*\
pro 64 bitová unsigned integer k dělení.

*dělitel*\
pro 32 bitová unsigned integer k dělení.

*Hledáte*\
mimo 32 unsigned integer zbytek.

## <a name="return-value"></a>Návratová hodnota

32 bitů podílu.

## <a name="remarks"></a>Poznámky

Vnitřní dělí dělenec dělitelem. `_udiv64` Ukládá zbytek do 32 unsigned integer ukazují na *zbytek*a vrátí 32 bitů podílu.

`_udiv64` Vnitřní verze je k dispozici počínaje verzí Visual Studio 2019 RTM.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_udiv64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Viz také:

[_div64](div64.md) \
[Vnitřní objekty kompilátoru](compiler-intrinsics.md)
