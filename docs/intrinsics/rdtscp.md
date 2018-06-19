---
title: __rdtscp | Microsoft Docs
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
ms.openlocfilehash: 0d890afe9e19782f19442e8d95709b91a8680278
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329800"
---
# <a name="rdtscp"></a>__rdtscp
**Konkrétní Microsoft**  
  
 Generuje `rdtscp` instrukce, zapíše `TSC_AUX[31:0`] paměti a vrátí čítač 64-bit časové razítko (`TSC)` výsledek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned __int64 __rdtscp(  
   unsigned int * Aux  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `Aux`  
 Ukazatel na umístění, která bude obsahovat obsah registru specifické pro počítač `TSC_AUX[31:0]`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet značek 64bitové celé číslo bez znaménka.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__rdtscp`|0Fh rodiny NPT AMD nebo novější verze|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tento vnitřní vygeneruje `rdtscp` instrukcí. Chcete-li určit podporu hardwaru pro tento pokyn, zavolejte `__cpuid` vnitřní s `InfoType=0x80000001` a zkontrolujte bit 27 `CPUInfo[3] (EDX)`. Tato verze je 1, pokud je podporovaná pokyn a 0 jinak.  Pokud jste spustili kód, který používá tento vnitřní hardware, který nepodporuje `rdtscp` instrukce, nepředvídatelné výsledky.  
  
> [!CAUTION]
>  Na rozdíl od `rdtsc`, `rdtscp` serializaci instrukce; je nicméně kompilátor můžete přesunout kódu kolem to vnitřní.  
  
 Výklad TSC hodnota v generování hardwaru se liší od ve starších verzích [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  V tématu příručky hardwaru pro další informace.  
  
 Význam hodnoty v `TSC_AUX[31:0]` závisí na operačním systému.  
  
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
  
**Konkrétní Microsoft END**  
 Copyright 2007 pokročilé Micro zařízení, Inc. Všechna práva vyhrazena. Opakuje se svolením Advanced Micro zařízení, Inc.  
  
## <a name="see-also"></a>Viz také  
 [__rdtsc](../intrinsics/rdtsc.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)