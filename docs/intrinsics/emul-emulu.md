---
title: __emul __emulu
ms.date: 11/04/2016
f1_keywords:
- __emulu_cpp
- __emul
- __emul_cpp
- __emulu
helpviewer_keywords:
- __emul intrinsic
- __emulu intrinsic
ms.assetid: 79545236-cca2-40b8-a4e1-8abce9b26311
ms.openlocfilehash: 8657c0fb034ac6bbcfbebb946e059ad08d9e7046
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030047"
---
# <a name="emul-emulu"></a>__emul __emulu

**Specifické pro Microsoft**

Provádí součinů, které přetečení, co může obsahovat 32bitové celé číslo.

## <a name="syntax"></a>Syntaxe

```
__int64 __emul(
   int a,
   int b
);
unsigned __int64 __emulu(
   unsigned int a,
   unsigned int b
);
```

#### <a name="parameters"></a>Parametry

*a*<br/>
[in] První celočíselný operand násobení.

*b*<br/>
[in] Druhý operand celé číslo násobení.

## <a name="return-value"></a>Návratová hodnota

Výsledek násobení.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__emul`|x86, x64|
|`__emulu`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

`__emul` přebírá dva 32-bit hodnoty se znaménkem a vrátí výsledek násobení jako 64-bit celočíselnou hodnotu se znaménkem.

`__emulu` má dvě hodnoty 32bitové celé číslo bez znaménka a vrátí výsledek násobení jako hodnotu 64bitové celé číslo bez znaménka.

## <a name="example"></a>Příklad

```
// emul.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__emul)
#pragma intrinsic(__emulu)

int main()
{
   int a = -268435456;
   int b = 2;

   __int64 result = __emul(a, b);

   cout << a << " * " << b << " = " << result << endl;

   unsigned int ua = 0xFFFFFFFF; // Dec value: 4294967295
   unsigned int ub = 0xF000000;  // Dec value: 251658240

   unsigned __int64 uresult = __emulu(ua, ub);

   cout << ua << " * " << ub << " = " << uresult << endl;

}
```

## <a name="output"></a>Výstup

```
-268435456 * 2 = -536870912
4294967295 * 251658240 = 1080863910317260800
```

**END Specifické pro Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)