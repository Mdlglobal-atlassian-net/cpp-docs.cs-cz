---
title: Využití registrů
ms.date: 11/04/2016
ms.assetid: ce58e2cf-afd3-4068-980e-28a209298265
ms.openlocfilehash: fa04318ad4af298f300fbbbad8c01d0df9500ec7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629980"
---
# <a name="register-usage"></a>Využití registrů

X64, které poskytuje architekturu pro 16 pro obecné účely registrů (dále jako celočíselné registry), stejně jako 16 XMM nebo YMM zaregistruje k dispozici pro použití s plovoucí desetinnou čárkou. Volatile registrů se předpokládá, že volající, který se má zničit prostřednictvím volání pomocné registrů. Stálé registry je potřeba zachovat jejich hodnoty prostřednictvím volání funkce a musí být uložen volaný, pokud se používá.

## <a name="register-volatility-and-preservation"></a>Zaregistrujte volatility a zachovávání s rozlišením

Následující tabulka popisuje, jak každý registr se používá ve volání funkce:

||||
|-|-|-|
|Registr|Stav|Použití|
|RAX|Volatile|Návratová hodnota registru|
|RCX|Volatile|První argument typu celé číslo|
|RDX|Volatile|Druhý argument typu celé číslo|
|R8|Volatile|Třetí argument typu celé číslo|
|R9|Volatile|Čtvrtý argument typu celé číslo|
|R10:R11|Volatile|Musí být zachovány podle potřeby volajícím; používá se v pokynech syscall/sysret|
|R12:R15|Stálé|Musí být zachovány volaným|
|RDI|Stálé|Musí být zachovány volaným|
|RSI|Stálé|Musí být zachovány volaným|
|RBX|Stálé|Musí být zachovány volaným|
|RBP|Stálé|Může sloužit jako ukazatel na rámec; musí být zachovány volaným|
|RSP|Stálé|Ukazatel zásobníku|
|XMM0, YMM0|Volatile|První argument FP první argument typu vector při `__vectorcall` slouží|
|XMM1, YMM1|Volatile|Druhý argument FP; druhý argument typ vektoru při `__vectorcall` slouží|
|XMM2, YMM2|Volatile|Třetí argument FP třetí argument typ vektoru při `__vectorcall` slouží|
|XMM3 YMM3|Volatile|Čtvrtý argument FP čtvrtý argument typ vektoru při `__vectorcall` slouží|
|XMM4 YMM4|Volatile|Musí být zachovány podle potřeby volajícím; pátý argument typ vektoru při `__vectorcall` slouží|
|XMM5 YMM5|Volatile|Musí být zachovány podle potřeby volajícím; šestý argument typ vektoru při `__vectorcall` slouží|
|XMM6:XMM15 YMM6:YMM15|Stálé (XMM) Volatile (horní polovinu YMM)|Musí být zachovány volaným. Podle potřeby volající musí být zachovány registrech YMM.|

Při ukončení funkce a na položku funkce a volání knihovny Runtime jazyka C a systému Windows, příznak směru v procesoru příznaky registrace má zůstat nezaškrtnutá.

## <a name="see-also"></a>Viz také:

- [x64 – softwarové konvence](../build/x64-software-conventions.md)
- [__vectorcall](../cpp/vectorcall.md)
- [Příznak směru](../c-runtime-library/direction-flag.md)
