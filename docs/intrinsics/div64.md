---
title: _div64
ms.date: 09/02/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: 1d05c5d6e25540a5de1b2f8231697c9a738759ce
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216772"
---
# <a name="_div64"></a>_div64

`_div64` Vnitřní dělí 64 celé číslo na 32 celé číslo. Vrácená hodnota drží podíl a vnitřní Vrátí zbytek prostřednictvím parametru ukazatele. `_div64`je **specifická pro společnost Microsoft**.

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
pro 64 celé číslo, které se má rozdělit.

*dělitel* \
pro 32 celé číslo, které se má rozdělit.

*Hledáte* \
mimo 32 celé číslo bitů zbytku.

## <a name="return-value"></a>Návratová hodnota

32 bitů podílu.

## <a name="remarks"></a>Poznámky

Vnitřní dělí dělenec dělitelem. `_div64` Ukládá zbytek v 32 celé číslo, na které ukazuje *zbytek*, a vrátí 32 bitů podílu.

`_div64` Vnitřní verze je k dispozici počínaje verzí Visual Studio 2019 RTM.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|Záhlaví|
|---------------|------------------|------------|
|`_div64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Viz také:

[_udiv64](udiv64.md) \
[Vnitřní objekty kompilátoru](compiler-intrinsics.md)
