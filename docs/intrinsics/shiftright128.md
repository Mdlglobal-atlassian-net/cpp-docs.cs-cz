---
title: __shiftright128
ms.date: 09/02/2019
f1_keywords:
- __shiftright128
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
ms.openlocfilehash: a18a9958a51f291e4997c23e87ee48f739562416
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220015"
---
# <a name="__shiftright128"></a>__shiftright128

**Specifické pro společnost Microsoft**

Posune 128 množství, které je reprezentováno jako 2 64 množství `LowPart` bitů a `HighPart`napravo podle počtu bitů určených parametrem `Shift` , a vrátí nižší 64 bitů výsledku.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __shiftright128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

### <a name="parameters"></a>Parametry

*LowPart*\
pro Dolní 64 bitů 128 množství, které se má posunout

*HighPart*\
pro Horní 64 bitů 128 množství, které se má posunout

*Posouvá*\
pro Počet bitů, které se mají posunout

## <a name="return-value"></a>Návratová hodnota

Dolních 64 bitů výsledku.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__shiftright128`|x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

`0` `__shiftright128(0, 1, 64)` `1` `0` Hodnota je vždy modulo 64, takže pokud například voláte, funkce posune pravou část bitů vpravo a vrátí malou část a ne tak, jak by jinak bylo možné očekávat. `Shift`

## <a name="example"></a>Příklad

Příklad naleznete v tématu [__shiftleft128](../intrinsics/shiftleft128.md).

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[__shiftleft128](../intrinsics/shiftleft128.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
