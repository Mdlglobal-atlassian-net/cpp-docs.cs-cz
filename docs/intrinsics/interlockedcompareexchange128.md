---
title: _InterlockedCompareExchange128 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2850be4b93738c61e22c5ca841e07f1901ec01e2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="interlockedcompareexchange128"></a>_InterlockedCompareExchange128
**Microsoft Specific**  
  
 Provede porovnání interlocked 128-bit a serveru exchange.  
  
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
 [ve out] `Destination`  
 Ukazatel na cíl, který je pole dvě celá čísla 64-bit považuje za pole 128-bit. Cílový data musí být 16 bajtů v souladu předejdete obecnou chybu ochrany.  
  
 [in] `ExchangeHigh`  
 64bitové celé číslo, které je možné poskytovat s horní část cílové.  
  
 [in] `ExchangeLow`  
 64bitové celé číslo, které je možné poskytovat s nízkou část cílového.  
  
 [ve out] `ComparandResult`  
 Ukazatele na pole dvě celá čísla 64-bit (považuje za pole 128-bit) k porovnání s cílovým.  Na výstupu se přepíšou s původní hodnotou k cílové složce.  
  
## <a name="return-value"></a>Návratová hodnota  
 1, pokud operand porovnávání 128-bit rovná původní hodnotu k cílové složce. `ExchangeHigh` a `ExchangeLow` přepsat cílový 128-bit.  
  
 0, pokud operand porovnávání se nerovná původní hodnotu k cílové složce. Hodnota cíl je beze změny a hodnota operand porovnávání se přepíše s hodnotou cílového.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`_InterlockedCompareExchange128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tento vnitřní vygeneruje `cmpxchg16b` instrukce (s `lock` předponu) k provádění porovnání uzamčeném 128-bit a exchange. Dřívější verze AMD 64bitový hardware nepodporují tento pokyn. Chcete-li zkontrolovat pro podporu hardwaru pro `cmpxchg16b` instrukce, volání `__cpuid` vnitřní s `InfoType=0x00000001 (standard function 1)`. Bit 13 `CPUInfo[2]` (ECX) je 1, pokud je podporováno pokyn.  
  
> [!NOTE]
>  Hodnota `ComparandResult` vždy přepsán. Po `lock` instrukce, Tento vnitřní okamžitě zkopíruje počáteční hodnota `Destination` k `ComparandResult`. Z tohoto důvodu `ComparandResult` a `Destination` by měla odkazovat na umístění samostatnou paměť pro vyhnout neočekávanému chování.  
  
 Přestože je možné použít `_InterlockedCompareExchange128` pro synchronizaci nízké úrovně vlákno, není nutné k synchronizaci víc než 128 bitů, pokud používáte menší funkce synchronizace (například dalších `_InterlockedCompareExchange` vnitřní funkce) místo. Použití `_InterlockedCompareExchange128` atomic pro přístup na hodnotu 128-bit v paměti.  
  
 Pokud jste spustili kód, který používá tento vnitřní hardware, který nepodporuje `cmpxchg16b` instrukce, nepředvídatelné výsledky.  
  
 Tato rutina je k dispozici pouze jako vnitřní.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `_InterlockedCompareExchange128` nahradit vysoké slovo pole dvě celá čísla 64-bit součet jeho vysoké a nízké slova a se zvýší nízkou aplikace word. Přístup k poli BigInt.Int je atomic, ale tento příklad používá jedním vláknem a ignoruje uzamčení pro jednoduchost.  
  
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
  
**Konkrétní Microsoft END**  
 Copyright 2007 pokročilé Micro zařízení, Inc. Všechna práva vyhrazena. Opakuje se svolením Advanced Micro zařízení, Inc.  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [_InterlockedCompareExchange vnitřní funkce](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)   
 [Konflikty s kompilátorem x86](../build/conflicts-with-the-x86-compiler.md)