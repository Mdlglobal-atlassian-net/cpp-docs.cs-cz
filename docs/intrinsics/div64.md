---
title: _div64
ms.date: 09/02/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: 59c5eae66f9e93cb88f9512e405376f2ef5f1ceb
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858019"
---
# <a name="_div64"></a>_div64

Vnitřní `_div64` rozdělí 64 celé číslo na 32 celé číslo. Vrácená hodnota drží podíl a vnitřní Vrátí zbytek prostřednictvím parametru ukazatele. `_div64` je **specifické pro společnost Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>Parametry

 \ *dividend*
pro 64 celé číslo, které se má rozdělit.

*dělitel* \
pro 32 celé číslo, které se má rozdělit.

*zbývající* \
mimo 32 celé číslo bitů zbytku.

## <a name="return-value"></a>Návratová hodnota

32 bitů podílu.

## <a name="remarks"></a>Poznámky

Vnitřní `_div64` rozdělí *dividendy* pomocí *dělitele*. Ukládá zbytek v 32 celé číslo, na které ukazuje *zbytek*, a vrátí 32 bitů podílu.

Vnitřní `_div64` je k dispozici počínaje verzí Visual Studio 2019 RTM.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_div64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Viz také:

[_udiv64](udiv64.md) \
[Vnitřní objekty kompilátoru](compiler-intrinsics.md)
