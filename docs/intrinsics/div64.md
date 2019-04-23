---
title: _div64
ms.date: 04/17/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: a221cc7cf0655a41873c6777aecd8a9b27131b74
ms.sourcegitcommit: 2ce88de75e7681220ae09a0ab13056f22f357a46
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983104"
---
# <a name="div64"></a>_div64

`_div64` Vnitřní rozděluje 64bitové celé číslo pomocí 32bitové celé číslo. Návratová hodnota obsahuje podíl a vnitřní Vrátí zbytek prostřednictvím parametru ukazatele. `_div64` je **specifické pro Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>Parametry

*podíl* \
[in] 64bitové celé číslo se má dělit.

*dělitel* \
[in] 32bitové celé číslo k rozdělení.

*Zbývající* \
[out] 32bitové celé číslo bity zbytek.

## <a name="return-value"></a>Návratová hodnota

32 bitů podíl.

## <a name="remarks"></a>Poznámky

`_div64` Vnitřní rozdělí *dělenec* podle *dělitel*. Zbývající ukládá 32bitové celé číslo, na které odkazuje *zbývající*a vrátí 32 bitů podíl.

`_div64` Vnitřní je k dispozici od verze Visual Studio. 2019 RTM.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_div64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Viz také:

[_udiv64](udiv64.md) \
[Vnitřní funkce kompilátoru](compiler-intrinsics.md)
