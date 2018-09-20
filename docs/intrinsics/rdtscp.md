---
title: __rdtscp | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __rdtscp
dev_langs:
- C++
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65c4638112d87b0544e9a6c61d839c7ad4664d33
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415152"
---
# <a name="rdtscp"></a>__rdtscp

**Specifické pro Microsoft**

Generuje `rdtscp` instrukce, zapíše `TSC_AUX[31:0`] do paměti a vrátí čítač razítko času 64-bit (`TSC)` výsledek.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __rdtscp(
   unsigned int * Aux
);
```

#### <a name="parameters"></a>Parametry

*AUX*<br/>
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

Copyright 2007 pokročilé zařízení Micro, Inc. Všechna práva vyhrazena. Reprodukovat se svolením rozšířené Micro zařízení, Inc.

## <a name="see-also"></a>Viz také

[__rdtsc](../intrinsics/rdtsc.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)