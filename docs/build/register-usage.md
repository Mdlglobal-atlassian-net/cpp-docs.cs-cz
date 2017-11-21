---
title: "Využití registrů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: ce58e2cf-afd3-4068-980e-28a209298265
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7394088f4bd3cec21dde9ea82c0573c56d87366a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="register-usage"></a>Využití registrů
[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] Architektura poskytuje pro 16 pro obecné účely registrů (dále jen jako celočíselné registry) a také 16 XMM/YMM registrů, k dispozici pro použití s plovoucí desetinnou čárkou. Volatile registry jsou odolné registry předpokládá, že volající zničení prostřednictvím volání. Nezávislé registry zachovat jejich hodnoty prostřednictvím volání funkce a musí být uložena volaného, pokud se používá.  
  
 Následující tabulka popisuje, jak každý registr se používá napříč volání funkce:  
  
||||  
|-|-|-|  
|Registr|Stav|Použití|  
|RAX|Volatile|Návratová hodnota registru|  
|RCX|Volatile|První argument celé číslo|  
|RDX –|Volatile|Druhý argument celé číslo|  
|R8|Volatile|Třetí argument celé číslo|  
|R9|Volatile|Poslední argument celé číslo|  
|R10:R11|Volatile|Musí být zachováno podle potřeby volající; používá se v pokynech syscall/sysret|  
|R12:R15|Stálé|Musí být zachováno podle volaný|  
|RDI|Stálé|Musí být zachováno podle volaný|  
|RSI|Stálé|Musí být zachováno podle volaný|  
|RBX|Stálé|Musí být zachováno podle volaný|  
|RBP|Stálé|Slouží jako ukazatel na rámec; musí být zachováno podle volaný|  
|KONFIGURACE|Stálé|Ukazatel zásobníku|  
|XMM0 YMM0|Volatile|První argument FP; první argument typu vektoru při `__vectorcall` slouží|  
|XMM1 YMM1|Volatile|Druhý argument FP; druhý argument typu vektoru při `__vectorcall` slouží|  
|XMM2 YMM2|Volatile|Třetí argument FP; třetí argument typu vektoru při `__vectorcall` slouží|  
|XMM3 YMM3|Volatile|Poslední argument FP; poslední argument vektoru type při `__vectorcall` slouží|  
|XMM4 YMM4|Volatile|Musí být zachováno podle potřeby volající; pátý argument typu vektoru při `__vectorcall` slouží|  
|XMM5 ZÁVISLÉ, YMM5|Volatile|Musí být zachováno podle potřeby volající; šesté argumentu vektoru typu při `__vectorcall` slouží|  
|XMM6:XMM15 YMM6:YMM15|Stálé (XMM) Volatile (horní polovině YMM)|Musí být volaný uchovávat. Podle potřeby volající musí být zachováno YMM Registry.|  
  
## <a name="see-also"></a>Viz také  
 [x64 softwarové konvence](../build/x64-software-conventions.md)   
 [__vectorcall](../cpp/vectorcall.md)
