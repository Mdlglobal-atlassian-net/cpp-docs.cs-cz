---
title: __popcnt16, __popcnt, __popcnt64
ms.date: 09/02/2019
f1_keywords:
- __popcnt64
- __popcnt
- __popcnt16
helpviewer_keywords:
- popcnt instruction
- __popcnt16
- __popcnt64
- __popcnt
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
ms.openlocfilehash: 3e5ae7f897500775671f8bd2563028874579a627
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221354"
---
# <a name="__popcnt16-__popcnt-__popcnt64"></a>__popcnt16, __popcnt, __popcnt64

**Specifické pro společnost Microsoft**

Spočítá počet `1` bitů (počet obyvatel) ve 16, 32 nebo 64 bitové unsigned integer.

## <a name="syntax"></a>Syntaxe

```C
unsigned short __popcnt16(
   unsigned short value
);
unsigned int __popcnt(
   unsigned int value
);
unsigned __int64 __popcnt64(
   unsigned __int64 value
);
```

### <a name="parameters"></a>Parametry

*osa*\
pro 16, 32 nebo 64-bit unsigned integer, pro které chceme počet naplnění.

## <a name="return-value"></a>Návratová hodnota

Počet `1` bitů v parametru *Value* .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__popcnt16`|Pokročilá manipulace s bit|
|`__popcnt`|Pokročilá manipulace s bit|
|`__popcnt64`|Pokročilá přenosová manipulace v 64ovém režimu.|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Každý z vnitřních objektů generuje `popcnt` instrukci. V 32ovém režimu nejsou k dispozici žádné 64 bitové registry pro obecné účely, takže 64-bit `popcnt` není podporován.

Chcete-li zjistit hardwarovou `popcnt` podporu instrukce, `__cpuid` zavolejte vnitřní s `InfoType=0x00000001` a zkontrolujte bit 23 z `CPUInfo[2] (ECX)`. Tento bit je 1, pokud je instrukce podporována a 0 jinak. Pokud spustíte kód, který používá tyto vnitřní hodnoty na hardwaru, který nepodporuje `popcnt` instrukci, nepředvídatelné výsledky.

## <a name="example"></a>Příklad

```cpp
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
  unsigned short us[3] = {0, 0xFF, 0xFFFF};
  unsigned short usr;
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};
  unsigned int   uir;

  for (int i=0; i<3; i++) {
    usr = __popcnt16(us[i]);
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __popcnt(ui[i]);
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__popcnt16(0x0) = 0
__popcnt16(0xff) = 8
__popcnt16(0xffff) = 16
__popcnt(0x0) = 0
__popcnt(0xff) = 8
__popcnt(0xffff) = 16
__popcnt(0xffffffff) = 32
```

**Specifické pro konec Microsoftu**

Copyright 2007 od Advanced Micro Devices, Inc. Všechna práva vyhrazena. Reprodukováno s oprávněním z Advanced Micro Devices, Inc.

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
