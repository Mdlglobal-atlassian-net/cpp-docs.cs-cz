---
title: Využití registrů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ce58e2cf-afd3-4068-980e-28a209298265
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c77469a8cef03827101f4bf367c00a3bb440820
ms.sourcegitcommit: 4fc6869067d533b175207befd2dc60346afee285
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="register-usage"></a>Využití registrů

X64, které poskytuje architekturu pro 16 pro obecné účely registrů (dále jen jako celočíselné registry) a také 16 XMM/YMM zaregistruje k dispozici pro použití s plovoucí desetinnou čárkou. Volatile registry jsou odolné registry předpokládá, že volající zničení prostřednictvím volání. Nezávislé registry zachovat jejich hodnoty prostřednictvím volání funkce a musí být uložena volaného, pokud se používá.

## <a name="register-volatility-and-preservation"></a>Registrovat volatility a uchovávání

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

Při ukončení funkce a na položku funkce pro volání běhové knihovny jazyka C a systému Windows, příznak směru v procesoru příznaky registrace se očekává vymazat.

## <a name="see-also"></a>Viz také

- [x64 – softwarové konvence](../build/x64-software-conventions.md)
- [__vectorcall](../cpp/vectorcall.md)
- [Příznak směru](../c-runtime-library/direction-flag.md)
