---
title: __lzcnt16, __lzcnt, __lzcnt64
ms.date: 09/02/2019
f1_keywords:
- __lzcnt64
- __lzcnt16
- __lzcnt
helpviewer_keywords:
- __lzcnt intrinsic
- lzcnt instruction
- lzcnt16 intrinsic
- lzcnt intrinsic
- __lzcnt16 intrinsic
- lzcnt64 intrinsic
- __lzcnt64 intrinsic
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
ms.openlocfilehash: fcd801717974a230fbd19cc7802d8f6a011774f7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221801"
---
# <a name="__lzcnt16-__lzcnt-__lzcnt64"></a>__lzcnt16, __lzcnt, __lzcnt64

**Specifické pro společnost Microsoft**

Spočítá počet počátečních nul v čísle 16, 32 nebo 64.

## <a name="syntax"></a>Syntaxe

```C
unsigned short __lzcnt16(
   unsigned short value
);
unsigned int __lzcnt(
   unsigned int value
);
unsigned __int64 __lzcnt64(
   unsigned __int64 value
);
```

### <a name="parameters"></a>Parametry

*osa*\
pro 16, 32 nebo 64 bitová unsigned integer pro kontrolu počátečních nul.

## <a name="return-value"></a>Návratová hodnota

Počet počátečních nul bitů v `value` parametru. Pokud `value` je nula, návratová hodnota je velikost vstupního operandu (16, 32 nebo 64). Je-li nejvýznamnějším bitem `value` jeden, vrácená hodnota je nula.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__lzcnt16`|AMD Pokročilá bitová manipulace (ABM)<br /><br /> RSS Haswell|
|`__lzcnt`|AMD Pokročilá bitová manipulace (ABM)<br /><br /> RSS Haswell|
|`__lzcnt64`|AMD Rozšířená manipulace s bitovou manipulací (ABM) v režimu 64.<br /><br /> RSS Haswell|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Každý z vnitřních objektů generuje `lzcnt` instrukci.  Velikost hodnoty, kterou vrátí `lzcnt` instrukce, je stejná jako velikost argumentu.  V 32ovém režimu nejsou k dispozici žádné 64 bitové registry pro obecné účely, takže bit `lzcnt` 64 není podporován.

Chcete-li zjistit hardwarovou `lzcnt` podporu instrukce, `__cpuid` zavolejte vnitřní s `InfoType=0x80000001` a zkontrolujte bit 5 z `CPUInfo[2] (ECX)`. Tento bit bude 1, pokud je instrukce podporovaná a 0 jinak. Pokud spustíte kód, který používá vnitřní na hardwaru, který nepodporuje `lzcnt` instrukci, výsledky se nepředvídatelné.

U procesorů Intel, které nepodporují `lzcnt` instrukci, se kódování instrukcí instrukce spouští jako `bsr` (zpětné prohledávání bitů). Pokud je k přenositelnosti kódu obavy, zvažte místo toho `_BitScanReverse` použití vnitřní funkce. Další informace najdete v tématu [_BitScanReverse, _BitScanReverse64](../intrinsics/bitscanreverse-bitscanreverse64.md).

## <a name="example"></a>Příklad

```cpp
// Compile this test with: /EHsc
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
    usr = __lzcnt16(us[i]);
    cout << "__lzcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __lzcnt(ui[i]);
    cout << "__lzcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__lzcnt16(0x0) = 16
__lzcnt16(0xff) = 8
__lzcnt16(0xffff) = 0
__lzcnt(0x0) = 32
__lzcnt(0xff) = 24
__lzcnt(0xffff) = 16
__lzcnt(0xffffffff) = 0
```

**Specifické pro konec Microsoftu**

Části tohoto obsahu jsou Copyright 2007 od společnosti Advanced Micro Devices, Inc. Všechna práva vyhrazena. Reprodukováno s oprávněním z Advanced Micro Devices, Inc.

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
