---
title: __lzcnt16, __lzcnt, __lzcnt64
ms.date: 11/04/2016
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
ms.openlocfilehash: 333d9f2b23fb90388af8395945256956c9222ab9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041335"
---
# <a name="lzcnt16-lzcnt-lzcnt64"></a>__lzcnt16, __lzcnt, __lzcnt64

**Microsoft Specific**

Spočítá počet úvodní nuly v 16, 32 nebo 64-bit integer.

## <a name="syntax"></a>Syntaxe

```
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

#### <a name="parameters"></a>Parametry

*value*<br/>
[in] 16 - 32 a 64-bit znaménka kontrolovala počátečními nulami.

## <a name="return-value"></a>Návratová hodnota

Počet úvodní nula bity `value` parametru. Pokud `value` je nula, vrácená hodnota je velikost vstupní operand (16, 32 nebo 64). Pokud bitu `value` je 1, vrácená hodnota je nula.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__lzcnt16`|AMD: Manipulace s pokročilé Bit (ABM)<br /><br /> Intel: Haswell|
|`__lzcnt`|AMD: Manipulace s pokročilé Bit (ABM)<br /><br /> Intel: Haswell|
|`__lzcnt64`|AMD: Pokročilé Bit manipulaci (ABM) v 64bitovém režimu.<br /><br /> Intel: Haswell|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Každá z těchto vnitřních objektů vygeneruje `lzcnt` instrukce.  Velikost hodnoty, který `lzcnt` instrukce vrátí je stejná jako velikost svého argumentu.  V 32bitovém režimu nejsou žádné 64-bit pro obecné účely registry, tedy ne 64-bit `lzcnt`.

K určení hardwarovou podporu `lzcnt` volání instrukce `__cpuid` vnitřní s `InfoType=0x80000001` a zkontrolujte bit 5 `CPUInfo[2] (ECX)`. Tato verze bude 1, pokud podporované instrukce a 0 jinak. Pokud jste spustili kód, který používá tuto vnitřní hardware, který není podporován `lzcnt` instrukce, výsledky nepředvídatelné.

Na procesorech Intel, které nepodporují `lzcnt` instrukce, kódování instrukce bajt je proveden, protože `bsr` (bit zpětného kontroly). Pokud je přenositelnost kódu, zvažte použití `_BitScanReverse` vnitřní místo. Další informace najdete v tématu [_BitScanReverse _BitScanReverse64](../intrinsics/bitscanreverse-bitscanreverse64.md).

## <a name="example"></a>Příklad

```
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

**Specifické pro END Microsoft**

Některé části tohoto článku je Copyright 2007 rozšířené Micro zařízení, Inc. Všechna práva vyhrazena. Reprodukovat se svolením rozšířené Micro zařízení, Inc.

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)
