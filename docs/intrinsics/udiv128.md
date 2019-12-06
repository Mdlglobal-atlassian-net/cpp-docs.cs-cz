---
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: 5e8cc9ca3dbf19a04d07edb1d73df84f2e29a5c3
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857980"
---
# <a name="_udiv128"></a>_udiv128

Vnitřní `_udiv128` rozděluje 128 unsigned integer bitovou unsigned integerou 64. Vrácená hodnota drží podíl a vnitřní Vrátí zbytek prostřednictvím parametru ukazatele. `_udiv128` je **specifické pro společnost Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 _udiv128(
   unsigned __int64 highDividend,
   unsigned __int64 lowDividend,
   unsigned __int64 divisor,
   unsigned __int64 *remainder
);
```

### <a name="parameters"></a>Parametry

*highDividend* \
pro Horní 64é bity z dividendy.

*lowDividend* \
pro Dolní 64é bity z dividendy.

*dělitel* \
pro 64 celé číslo, které se má rozdělit.

*zbývající* \
mimo 64 celé číslo bitů zbytku.

## <a name="return-value"></a>Návratová hodnota

64 bitů podílu.

## <a name="remarks"></a>Poznámky

Předejte horní 64 bitů 128 děleného dividendu v *highDividend*a nižší 64 bitů v *lowDividend*. Vnitřní dělí tuto hodnotu *dělitelem*. Ukládá zbytek do 64 unsigned integer ukazují na *zbytek*a vrátí 64 bitů podílu.

Vnitřní `_udiv128` je k dispozici počínaje verzí Visual Studio 2019 RTM.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_udiv128`|x64|\<immintrin.h>|

## <a name="see-also"></a>Viz také:

[_div128](div128.md) \
[Vnitřní objekty kompilátoru](compiler-intrinsics.md)
