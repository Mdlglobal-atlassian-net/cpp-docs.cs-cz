---
title: _rotl8, _rotl16
ms.date: 09/02/2019
f1_keywords:
- _rotl8
- _rotl16
helpviewer_keywords:
- _rotl8 intrinsic
- _rotl16 intrinsic
ms.assetid: 8c519ab6-aef9-4f07-a387-daee8408368f
ms.openlocfilehash: 5dffde2d3f830b6ec4ad43865648c27b1defb593
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218024"
---
# <a name="_rotl8-_rotl16"></a>_rotl8, _rotl16

**Specifické pro společnost Microsoft**

Otočí vstupní hodnoty vlevo na nejvýznamnější bit (MSB) podle zadaného počtu bitových pozic.

## <a name="syntax"></a>Syntaxe

```C
unsigned char _rotl8(
   unsigned char value,
   unsigned char shift
);
unsigned short _rotl16(
   unsigned short value,
   unsigned char shift
);
```

### <a name="parameters"></a>Parametry

*osa*\
pro Hodnota, která se má otočit

*posouvá*\
pro Počet bitů, které se mají otočit

## <a name="return-value"></a>Návratová hodnota

Otočená hodnota.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_rotl8`|x86, ARM, x64, ARM64|
|`_rotl16`|x86, ARM, x64, ARM64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Na rozdíl od operace Left Shift se při spuštění levého otočení přesunou horních bitů, které spadají do horního konce, do nejméně významných bitových pozic.

## <a name="example"></a>Příklad

```cpp
// rotl.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_rotl8, _rotl16)

int main()
{
    unsigned char c = 'A', c1, c2;

    for (int i = 0; i < 8; i++)
    {
       printf_s("Rotating 0x%x left by %d bits gives 0x%x\n", c,
               i, _rotl8(c, i));
    }

    unsigned short s = 0x12;
    int nBit = 10;

    printf_s("Rotating unsigned short 0x%x left by %d bits gives 0x%x\n",
            s, nBit, _rotl16(s, nBit));
}
```

```Output
Rotating 0x41 left by 0 bits gives 0x41
Rotating 0x41 left by 1 bits gives 0x82
Rotating 0x41 left by 2 bits gives 0x5
Rotating 0x41 left by 3 bits gives 0xa
Rotating 0x41 left by 4 bits gives 0x14
Rotating 0x41 left by 5 bits gives 0x28
Rotating 0x41 left by 6 bits gives 0x50
Rotating 0x41 left by 7 bits gives 0xa0
Rotating unsigned short 0x12 left by 10 bits gives 0x4800
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[_rotr8, _rotr16](../intrinsics/rotr8-rotr16.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
