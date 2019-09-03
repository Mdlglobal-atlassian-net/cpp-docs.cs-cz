---
title: __rdtscp
ms.date: 09/02/2019
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: 4dcabd6ed0f7fb3f422927815cbdc91f2b4b9d43
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221321"
---
# <a name="__rdtscp"></a>__rdtscp

**Specifické pro společnost Microsoft**

Vygeneruje `TSC_AUX[31:0``TSC)` instrukci, zápisy] do paměti a vrátí počítadlo 64 časového razítka (výsledek. `rdtscp`

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __rdtscp(
   unsigned int * AUX
);
```

### <a name="parameters"></a>Parametry

*POMOCNÉ*\
mimo Ukazatel na umístění, které bude obsahovat obsah registru `TSC_AUX[31:0]`pro konkrétní počítač.

## <a name="return-value"></a>Návratová hodnota

64 unsigned integer počet impulsů.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__rdtscp`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

`__rdtscp` Vnitřní`rdtscp` vygeneruje instrukci. Chcete-li zjistit hardwarovou podporu pro tuto instrukci, `InfoType=0x80000001` zavolejte `__cpuid` vnitřní objekt with `CPUInfo[3] (EDX)`a zkontrolujte bit 27. Tento bit je 1, pokud je instrukce podporována a 0 jinak.  Pokud spustíte kód, který používá vnitřní na hardwaru, který nepodporuje `rdtscp` instrukci, výsledky se nepředvídatelné.

Tato instrukce počká, dokud se nespustí všechny předchozí pokyny a že všechna předchozí načtení budou globálně viditelná. Nejedná se však o serializaci instrukcí. Další informace najdete v příručkách Intel a AMD.

Význam hodnoty v `TSC_AUX[31:0]` závislosti na operačním systému.

## <a name="example"></a>Příklad

```cpp
#include <intrin.h>
#include <stdio.h>
int main()
{
    unsigned __int64 i;
    unsigned int ui;
    i = __rdtscp(&ui);
    printf_s("%I64d ticks\n", i);
    printf_s("TSC_AUX was %x\n", ui);
}
```

```Output
3363423610155519 ticks
TSC_AUX was 0
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[__rdtsc](../intrinsics/rdtsc.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
