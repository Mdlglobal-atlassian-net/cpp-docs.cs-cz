---
title: _InterlockedCompareExchange128 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
dev_langs:
- C++
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7dfcdb0c7c2f6315ea7560c236c36d1a1ba449b9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389275"
---
# <a name="interlockedcompareexchange128"></a>_InterlockedCompareExchange128

**Specifické pro Microsoft**

Provádí 128-bit propojené porovnání a záměna.

## <a name="syntax"></a>Syntaxe

```
unsigned char _InterlockedCompareExchange128(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
```

#### <a name="parameters"></a>Parametry

*cíl*<br/>
[out v] Ukazatel na cílový, což je pole dvou celých čísel 64-bit považují za 128bitového pole. Cíl dat musí být 16 bajtů v souladu, aby obecnou chybu ochrany.

*ExchangeHigh*<br/>
[in] 64bitové celé číslo, který možná bude vyměněn za horní část cílové.

*ExchangeLow*<br/>
[in] 64bitové celé číslo, který možná bude vyměněn za dolní část cílové.

*ComparandResult*<br/>
[out v] Ukazatel na pole dvou celých čísel 64-bit (považují za pole 128-bit) má být porovnán s cílem.  Na výstupu je přepsán s původní hodnotou cíl.

## <a name="return-value"></a>Návratová hodnota

1, pokud operand porovnávání 128bitové shodná s původní hodnota cíle. `ExchangeHigh` a `ExchangeLow` přepsat cílový 128 bitů.

0, pokud operand porovnávání se nerovná původní hodnota cíle. Hodnota cíle je beze změny a hodnota operand porovnávání je přepsán s hodnotou cílového.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`_InterlockedCompareExchange128`|x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tomto vnitřní vygeneruje `cmpxchg16b` instrukcí (s `lock` předpony) provádět 128-bit uzamčené porovnání a záměna. Starší verze AMD 64bitový hardware nepodporuje tuto instrukci. Zkontrolujte hardwarovou podporu `cmpxchg16b` instrukce, volání `__cpuid` vnitřní s `InfoType=0x00000001 (standard function 1)`. Bit 13 `CPUInfo[2]` (ECX) je 1, pokud je podporován podle pokynů.

> [!NOTE]
>  Hodnota `ComparandResult` vždy přepsán. Po `lock` instrukce, tomto vnitřní okamžitě zkopíruje počáteční hodnota `Destination` k `ComparandResult`. Z tohoto důvodu `ComparandResult` a `Destination` by měly odkazovat na samostatná paměťová místa, aby se zabránilo neočekávané chování.

I když používáte `_InterlockedCompareExchange128` pro synchronizaci vláken nízké úrovně, nepotřebujete k synchronizaci více než 128 bitů, pokud používáte menší funkce synchronizace (jako je například druhé `_InterlockedCompareExchange` vnitřní funkce) místo toho. Použití `_InterlockedCompareExchange128` atomic pro přístup na hodnotu 128 bitů v paměti.

Pokud jste spustili kód, který používá tuto vnitřní hardware, který není podporován `cmpxchg16b` instrukce, výsledky nepředvídatelné.

Tato rutina je k dispozici pouze jako vnitřní.

## <a name="example"></a>Příklad

Tento příklad používá `_InterlockedCompareExchange128` vysoký Wordu pole dvou celých čísel 64-bit nahraďte součet jeho vysoké a nízké slova a postupně dolní slovo. Přístup k poli BigInt.Int je atomické, ale tento příklad používá jedno vlákno a ignoruje uzamčení pro jednoduchost.

```
// cmpxchg16b.c
// processor: x64
// compile with: /EHsc /O2
#include <stdio.h>
#include <intrin.h>

typedef struct _LARGE_INTEGER_128 {
    __int64 Int[2];
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;

volatile LARGE_INTEGER_128 BigInt;

// This AtomicOp() function atomically performs:
//   BigInt.Int[1] += BigInt.Int[0]
//   BigInt.Int[0] += 1
void AtomicOp ()
{
    LARGE_INTEGER_128 Comparand;
    Comparand.Int[0] = BigInt.Int[0];
    Comparand.Int[1] = BigInt.Int[1];
    do {
        ; // nothing
    } while (_InterlockedCompareExchange128(BigInt.Int,
                                            Comparand.Int[0] + Comparand.Int[1],
                                            Comparand.Int[0] + 1,
                                            Comparand.Int) == 0);
}

// In a real application, several threads contend for the value
// of BigInt.
// Here we focus on the compare and exchange for simplicity.
int main(void)
{
   BigInt.Int[1] = 23;
   BigInt.Int[0] = 11;
   AtomicOp();
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",
      BigInt.Int[1],BigInt.Int[0]);
}
```

```Output
BigInt.Int[1] = 34, BigInt.Int[0] = 12
```

**Specifické pro END Microsoft**

Copyright 2007 pokročilé zařízení Micro, Inc. Všechna práva vyhrazena. Reprodukovat se svolením rozšířené Micro zařízení, Inc.

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Vnitřní funkce _InterlockedCompareExchange](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)<br/>
[Konflikty s kompilátorem x86](../build/conflicts-with-the-x86-compiler.md)