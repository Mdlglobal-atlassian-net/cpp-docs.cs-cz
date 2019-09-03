---
title: Vnitřní funkce _InterlockedCompareExchange128
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
ms.openlocfilehash: 525b0fd77323789eed05c47c944794ff389bfac5
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217698"
---
# <a name="_interlockedcompareexchange128-intrinsic-functions"></a>Vnitřní funkce _InterlockedCompareExchange128

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

*Tabulka*\
[in, out] Ukazatel na cíl, což je pole 2 64 celých čísel, která jsou považována za 128-bitové pole. Aby se zabránilo obecné chybě ochrany, musí být cílová data zarovnaná se 16 bajty.

*ExchangeHigh*\
pro 64 celé číslo, které může být vyměněno s vysokou částí cíle.

*ExchangeLow*\
pro 64 celé číslo, které může být vyměněno s nízkou částí cíle.

*ComparandResult*\
[in, out] Ukazatel na pole 2 64 celých čísel (považuje se za 128elné pole) pro porovnání s cílem.  Ve výstupu je toto pole přepsáno původní hodnotou cíle.

## <a name="return-value"></a>Návratová hodnota

1, pokud 128-bit operand porovnávání odpovídá původní hodnotě cíle. `ExchangeHigh`a `ExchangeLow` přepište 128 cíl.

0, pokud se operand porovnávání nerovná původní hodnotě cílového umístění. Hodnota cíle se nezměnila a hodnota operand porovnávání se přepíše hodnotou cíle.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_InterlockedCompareExchange128`|x64, ARM64|
|`_InterlockedCompareExchange128_acq`, `_InterlockedCompareExchange128_nf`, `_InterlockedCompareExchange128_rel`|ARM64|
|`_InterlockedCompareExchange128_np`|x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Vnitřní vygeneruje instrukci (s `lock` předponou) k provedení 128y uzamčeného porovnání a výměny. `cmpxchg16b` `_InterlockedCompareExchange128` Dřívější verze AMD 64-bit hardware tuto instrukci nepodporuje. Chcete-li vyhledat podporu hardwaru pro `cmpxchg16b` instrukci, `__cpuid` zavolejte vnitřní objekt `InfoType=0x00000001 (standard function 1)`with. Bit 13 z `CPUInfo[2]` (ecx) je 1, pokud je instrukce podporována.

> [!NOTE]
> Hodnota `ComparandResult` je vždy přepsána. Po instrukci Tento vnitřní objekt okamžitě zkopíruje počáteční `Destination` hodnotu do `ComparandResult`. `lock` Z tohoto důvodu `Destination` by `ComparandResult` měl odkazovat na oddělené paměťové umístění, aby nedocházelo k neočekávanému chování.

I když můžete použít `_InterlockedCompareExchange128` pro synchronizaci vláken nízké úrovně, nemusíte synchronizovat přes 128 bitů, pokud můžete místo toho použít menší synchronizační funkce (například jiné `_InterlockedCompareExchange` vnitřní objekty). Použijte `_InterlockedCompareExchange128` , pokud chcete, aby byl v paměti atomický přístup k 128 hodnotě.

Pokud spustíte kód, který používá vnitřní na hardwaru, který nepodporuje `cmpxchg16b` instrukci, výsledky se nepředvídatelné.

Na platformách ARM používejte vnitřní `_acq` funkce a `_rel` přípony pro získání a vydání sémantiky, jako například na začátku a konci kritické části. Vnitřní objekty ARM s `_nf` příponou (bez plotu) nefungují jako bariéra paměti.

Vnitřní objekty s `_np` příponou ("bez předběžného navýšení") brání v tom, aby kompilátor vložil možné operace předběžného načtení.

Tato rutina je k dispozici pouze jako vnitřní.

## <a name="example"></a>Příklad

Tento příklad používá `_InterlockedCompareExchange128` k nahrazení vysokého slova pole 2 64 celých čísel se součtem jeho horních a dolních slov a k zvýšení nízkého počtu slov. Přístup k `BigInt.Int` poli je Atomic, ale v tomto příkladu se používá jediné vlákno a ignoruje uzamykání pro jednoduchost.

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


## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Vnitřní funkce _InterlockedCompareExchange](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)\
[Konflikty s kompilátorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
