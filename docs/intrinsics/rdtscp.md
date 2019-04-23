---
title: __rdtscp
ms.date: 11/04/2016
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: b28052fbe0a1ab0e1a6f037ce61f43abea5cf771
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028477"
---
# <a name="rdtscp"></a>__rdtscp

**Microsoft Specific**

Generuje `rdtscp` instrukce, zapíše `TSC_AUX[31:0`] do paměti a vrátí čítač razítko času 64-bit (`TSC)` výsledek.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __rdtscp(
   unsigned int * Aux
);
```

#### <a name="parameters"></a>Parametry

*Aux*<br/>
[out] Ukazatel na umístění, která bude obsahovat obsah registru specifické pro počítač `TSC_AUX[31:0]`.

## <a name="return-value"></a>Návratová hodnota

Počet cyklů 64bitové celé číslo bez znaménka.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__rdtscp`|0Fh řady NPT AMD nebo novější verze|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tomto vnitřní vygeneruje `rdtscp` instrukce. Chcete-li určit hardwarovou podporu pro tento pokyn, zavolejte `__cpuid` vnitřní s `InfoType=0x80000001` a zkontrolujte bit 27 `CPUInfo[3] (EDX)`. Tato verze je 1, pokud podporované instrukce a 0 jinak.  Pokud jste spustili kód, který používá tuto vnitřní hardware, který není podporován `rdtscp` instrukce, výsledky nepředvídatelné.

> [!CAUTION]
>  Na rozdíl od `rdtsc`, `rdtscp` je serializaci instrukce; nicméně, kompilátor může přesunout kód tomuto vnitřní.

Výklad TSC hodnotu této generace hardwaru se liší od v dřívějších verzích x64.  Najdete v článku hardware příruček pro další informace.

Hodnoty ve smyslu `TSC_AUX[31:0]` závisí na operačním systému.

## <a name="example"></a>Příklad

```
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

**Specifické pro END Microsoft**

Copyright 2007 by Advanced Micro Devices, Inc. Všechna práva vyhrazena. Reprodukovat se svolením rozšířené Micro zařízení, Inc.

## <a name="see-also"></a>Viz také:

[__rdtsc](../intrinsics/rdtsc.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)