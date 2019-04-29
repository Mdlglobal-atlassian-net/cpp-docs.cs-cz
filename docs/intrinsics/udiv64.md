---
title: _udiv64
ms.date: 04/17/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: 73a29b180eeda49a9a25e9e568d25c7563234fad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390149"
---
# <a name="udiv64"></a>_udiv64

`_udiv64` Vnitřní rozdělí 64bitové celé číslo bez znaménka podle 32-bit znaménka. Návratová hodnota obsahuje podíl a vnitřní Vrátí zbytek prostřednictvím parametru ukazatele. `_udiv64` je **specifické pro Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>Parametry

*podíl*<br/>
[in] 64bitové celé číslo bez znaménka se má dělit.

*dělitel*<br/>
[in] 32bitové celé číslo bez znaménka dělit.

*Zbývající*<br/>
[out] Zbývající 32bitové celé číslo bez znaménka.

## <a name="return-value"></a>Návratová hodnota

32 bitů podíl.

## <a name="remarks"></a>Poznámky

`_udiv64` Vnitřní rozdělí *dělenec* podle *dělitel*. Ukládá zbývající 32bitové celé číslo bez znaménka na které odkazuje *zbývající*a vrátí 32 bitů podíl.

`_udiv64` Vnitřní je k dispozici od verze Visual Studio. 2019 RTM.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_udiv64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Viz také:

[_div64](div64.md) \
[Vnitřní funkce kompilátoru](compiler-intrinsics.md)
