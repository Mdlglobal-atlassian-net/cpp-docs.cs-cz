---
title: __rdtscp
ms.date: 07/11/2019
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: b8a31c6d19cd171cbe909c75a27c2389866bd578
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861115"
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
|`__rdtscp`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tomto vnitřní vygeneruje `rdtscp` instrukce. Chcete-li určit hardwarovou podporu pro tento pokyn, zavolejte `__cpuid` vnitřní s `InfoType=0x80000001` a zkontrolujte bit 27 `CPUInfo[3] (EDX)`. Tato verze je 1, pokud podporované instrukce a 0 jinak.  Pokud jste spustili kód, který používá tuto vnitřní hardware, který není podporován `rdtscp` instrukce, výsledky nepředvídatelné.

Tento pokyn počká, až uzavřeli dohodu o všech předchozích kroků a všech předchozích načtení jsou viditelné globálně. Však není serializaci instrukce. Zobrazit Intelu a AMD příruček pro další informace.

Hodnoty ve smyslu `TSC_AUX[31:0]` závisí na operačním systému.

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

**Specifické pro END Microsoft**


## <a name="see-also"></a>Viz také:

[__rdtsc](../intrinsics/rdtsc.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)