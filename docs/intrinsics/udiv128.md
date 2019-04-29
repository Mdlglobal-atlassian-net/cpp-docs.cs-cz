---
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: 0e66bbe978199f47134aa288bdd2bac4eb3e332a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390162"
---
# <a name="udiv128"></a>_udiv128

`_udiv128` Vnitřní rozděluje 128-bit znaménka podle 64-bit znaménka. Návratová hodnota obsahuje podíl a vnitřní Vrátí zbytek prostřednictvím parametru ukazatele. `_udiv128` je **specifické pro Microsoft**.

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
[in] 64 bitů dělence.

*lowDividend* \
[in] Nízká 64 bitů podíl.

*dělitel* \
[in] 64bitové celé číslo k rozdělení.

*Zbývající* \
[out] 64bitové celé číslo bity zbytek.

## <a name="return-value"></a>Návratová hodnota

64 bitů podíl.

## <a name="remarks"></a>Poznámky

Předejte horní 64 bitů podíl 128 bitů v *highDividend*a nižší 64 bitů v *lowDividend*. Vnitřní objekt vydělí toto hodnoty *dělitel*. Ukládá zbývající 64bitové celé číslo bez znaménka na které odkazuje *zbývající*a vrátí podíl 64 bitů.

`_udiv128` Vnitřní je k dispozici od verze Visual Studio. 2019 RTM.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_udiv128`|x64|\<immintrin.h>|

## <a name="see-also"></a>Viz také:

[_div128](div128.md) \
[Vnitřní funkce kompilátoru](compiler-intrinsics.md)
