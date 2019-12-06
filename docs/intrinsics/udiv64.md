---
title: _udiv64
ms.date: 09/02/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: ddb46f33b0fccc1cedc2a704265b096ba715b506
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857993"
---
# <a name="_udiv64"></a>_udiv64

Vnitřní `_udiv64` rozděluje 64 unsigned integer bitovou unsigned integerou 32. Vrácená hodnota drží podíl a vnitřní Vrátí zbytek prostřednictvím parametru ukazatele. `_udiv64` je **specifické pro společnost Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>Parametry

\ *dividend*
pro 64 bitová unsigned integer k dělení.

*dělitel*\
pro 32 bitová unsigned integer k dělení.

*zbývající*\
mimo 32 unsigned integer zbytek.

## <a name="return-value"></a>Návratová hodnota

32 bitů podílu.

## <a name="remarks"></a>Poznámky

Vnitřní `_udiv64` rozdělí *dividendy* pomocí *dělitele*. Ukládá zbytek do 32 unsigned integer ukazují na *zbytek*a vrátí 32 bitů podílu.

Vnitřní `_udiv64` je k dispozici počínaje verzí Visual Studio 2019 RTM.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_udiv64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Viz také:

[_div64](div64.md) \
[Vnitřní objekty kompilátoru](compiler-intrinsics.md)
