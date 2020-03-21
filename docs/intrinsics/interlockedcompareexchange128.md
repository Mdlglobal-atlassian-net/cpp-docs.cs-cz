---
title: _InterlockedCompareExchange128 vnitřní funkce
ms.date: 09/02/2019
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
- _InterlockedCompareExchange128_acq
- _InterlockedCompareExchange128_nf
- _InterlockedCompareExchange128_np
- _InterlockedCompareExchange128_rel
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
ms.openlocfilehash: 6f6b36b238945f7d46e9817cdc85977d666e1e9b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077629"
---
# <a name="_interlockedcompareexchange128-intrinsic-functions"></a>_InterlockedCompareExchange128 vnitřní funkce

**Specifické pro společnost Microsoft**

Provede 128 propojených porovnání a Exchange.

## <a name="syntax"></a>Syntaxe

```C
unsigned char _InterlockedCompareExchange128(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_acq(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_nf(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_np(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_rel(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
```

### <a name="parameters"></a>Parametry

\ *cíle*
[in, out] Ukazatel na cíl, což je pole 2 64 celých čísel, která jsou považována za 128-bitové pole. Aby se zabránilo obecné chybě ochrany, musí být cílová data zarovnaná se 16 bajty.

*ExchangeHigh*\
pro 64 celé číslo, které může být vyměněno s vysokou částí cíle.

*ExchangeLow*\
pro 64 celé číslo, které může být vyměněno s nízkou částí cíle.

*ComparandResult*\
[in, out] Ukazatel na pole 2 64 celých čísel (považuje se za 128elné pole) pro porovnání s cílem.  Ve výstupu je toto pole přepsáno původní hodnotou cíle.

## <a name="return-value"></a>Návratová hodnota

1, pokud 128-bit operand porovnávání odpovídá původní hodnotě cíle. `ExchangeHigh` a `ExchangeLow` přepíší 128 cíl.

0, pokud se operand porovnávání nerovná původní hodnotě cílového umístění. Hodnota cíle se nezměnila a hodnota operand porovnávání se přepíše hodnotou cíle.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_InterlockedCompareExchange128`|x64, ARM64|
|`_InterlockedCompareExchange128_acq`, `_InterlockedCompareExchange128_nf`, `_InterlockedCompareExchange128_rel`|ARM64|
|`_InterlockedCompareExchange128_np`|x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Vnitřní `_InterlockedCompareExchange128` vygeneruje instrukci `cmpxchg16b` (s předponou `lock`) k provedení 128ho uzamčeného porovnání a výměny. Dřívější verze AMD 64-bit hardware tuto instrukci nepodporuje. Chcete-li vyhledat podporu hardwaru pro `cmpxchg16b` instrukci, zavolejte vnitřní `__cpuid` s `InfoType=0x00000001 (standard function 1)`. Pokud je instrukce podporovaná, je bitová verze 13 `CPUInfo[2]` (ECX) 1.

> [!NOTE]
> Hodnota `ComparandResult` je vždy přepsána. Po `lock` instrukci Tento vnitřní objekt okamžitě zkopíruje počáteční hodnotu `Destination` na `ComparandResult`. Z tohoto důvodu by `ComparandResult` a `Destination` odkazovaly na oddělené paměťové umístění, aby nedocházelo k neočekávanému chování.

I když můžete použít `_InterlockedCompareExchange128` pro synchronizaci vláken nízké úrovně, nemusíte synchronizovat přes 128 bitů, pokud můžete místo toho použít menší synchronizační funkce (například jiné vnitřní objekty `_InterlockedCompareExchange`). Použijte `_InterlockedCompareExchange128`, pokud chcete, aby byl v paměti atomický přístup k 128 hodnotě.

Pokud spustíte kód, který používá vnitřní na hardwaru, který nepodporuje instrukci `cmpxchg16b`, nepředvídatelné výsledky.

Na platformách ARM použijte vnitřní objekty s příponami `_acq` a `_rel` pro sémantiku získání a vydání, jako je například na začátku a konci kritické části. Vnitřní objekty ARM s příponou `_nf` (bez plotu) nefungují jako bariéra paměti.

Vnitřní objekty s příponou `_np` ("bez předběžného navýšení") brání, aby bylo možné operaci předběžného načtení vložit do kompilátoru.

Tato rutina je k dispozici pouze jako vnitřní.

## <a name="example"></a>Příklad

V tomto příkladu se používá `_InterlockedCompareExchange128` k nahrazení vysokého slova pole 2 64 celých čísel se součtem jeho horních a dolních slov a k zvýšení nízkého počtu slov. Přístup k poli `BigInt.Int` je Atomic, ale v tomto příkladu se používá jediné vlákno a ignoruje uzamykání pro jednoduchost.

```cpp
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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[_InterlockedCompareExchange vnitřní funkce](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)\
[Konflikty s kompilátorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
