---
title: __shiftright128
ms.date: 11/04/2016
f1_keywords:
- __shiftright128
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
ms.openlocfilehash: b721abc9be22709fdc221951e2012300d6b96762
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390331"
---
# <a name="shiftright128"></a>__shiftright128

**Microsoft Specific**

Množství 128-bit, vyjádřené dvě veličiny 64-bit posune `LowPart` a `HighPart`, vpravo o počet bitů určený `Shift` a vrátí nízké 64 bitů výsledku.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __shiftright128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

#### <a name="parameters"></a>Parametry

*LowPart*<br/>
[in] Nízká 64 bitů množství 128 bitů a posunutí.

*HighPart*<br/>
[in] Vysoká 64 bitů množství 128 bitů a posunutí.

*SHIFT*<br/>
[in] Počet bitů na posunu.

## <a name="return-value"></a>Návratová hodnota

Nízká 64 bitů výsledku.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__shiftright128`|x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

`Shift` Hodnota je vždy modulo 64 tak, že, například při volání `__shiftright128(0, 1, 64)`, funkce změní horní část `0` bits klikněte pravým tlačítkem myši a vrátí dolní část z `0` a ne `1` jako jinak lze očekávat.

## <a name="example"></a>Příklad

Příklad najdete v tématu [__shiftleft128](../intrinsics/shiftleft128.md).

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[__shiftleft128](../intrinsics/shiftleft128.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)