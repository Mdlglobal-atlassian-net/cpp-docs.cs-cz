---
title: __ull_rshift
ms.date: 09/02/2019
f1_keywords:
- __ull_rshift
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
ms.openlocfilehash: bf9fe7775cee1c774c097a1b6bd371721c9fa34f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80074979"
---
# <a name="__ull_rshift"></a>__ull_rshift

**Specifické pro společnost Microsoft**

na platformě x64 posune 64 hodnotu určenou prvním parametrem vpravo o počet bitů určených druhým parametrem.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __ull_rshift(
   unsigned __int64 mask,
   int nBit
);
```

### <a name="parameters"></a>Parametry

\ *masky*
pro Hodnota 64 celé číslo, která se má posunout vpravo.

*nBit*\
pro Počet bitů, které se mají posunout, modulo 32 na x86 a modulo 64 na platformě x64.

## <a name="return-value"></a>Návratová hodnota

Maska se posune o `nBit` bitů.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__ull_rshift`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Pokud je druhý parametr větší než 31 na platformě x86 (63 na platformě x64), toto číslo se převezme modulo 32 (64 na platformě x64) a určí počet bitů, které se mají posunout. `ull` v názvu označuje `unsigned long long (unsigned __int64)`.

## <a name="example"></a>Příklad

```cpp
// ull_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ull_rshift)

int main()
{
   unsigned __int64 mask = 0x100;
   int nBit = 8;
   mask = __ull_rshift(mask, nBit);
   cout << hex << mask << endl;
}
```

```Output
1
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[__ll_lshift](../intrinsics/ll-lshift.md)\
[__ll_rshift](../intrinsics/ll-rshift.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
