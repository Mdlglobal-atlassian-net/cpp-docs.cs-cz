---
title: Výjimky hardwaru
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [C++], hardware
- errors [C++], low-level
- errors [C++], hardware
- hardware exceptions [C++]
- low level errors
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
ms.openlocfilehash: 17775f3b2ee6dfa235c93d0bf0e3335b464aaa69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553527"
---
# <a name="hardware-exceptions"></a>Výjimky hardwaru

Většina standardních výjimek rozpoznávaných operačním systémem jsou výjimky definované hardwarem. Systém Windows rozpoznává několik softwarových výjimek nízké úrovně, ty však bývají operačním systémem zpracovány nejvhodněji.

Systém Windows mapuje chyby hardwaru různých procesorů na kódy výjimek v tomto oddílu. V některých případech může procesor vygenerovat pouze podmnožinu těchto výjimek. Systém Windows upravuje informace o výjimce a udává příslušný kód výjimky.

Hardwarové výjimky rozpoznávané systémem Windows jsou shrnuty v následující tabulce:

|Kód výjimky|Příčina výjimky|
|--------------------|------------------------|
|STATUS_ACCESS_VIOLATION|Čtení nebo zápis nepřístupného umístění v paměti.|
|STATUS_BREAKPOINT|Přechod na hardwarem definovanou zarážku. Používáno pouze ladicími programy.|
|STATUS_DATATYPE_MISALIGNMENT|Čtení nebo zápis dat na nesprávně zarovnané adrese. Například 16bitové entity musí být zarovnány na 2bajtové hranice. (Nevztahuje se na Intel 80*x*86 procesory.)|
|STATUS_FLOAT_DIVIDE_BY_ZERO|Dělení typu s plovoucí desetinnou čárkou hodnotou 0,0.|
|STATUS_FLOAT_OVERFLOW|Překročení maximálního kladného exponentu typu s plovoucí desetinnou čárkou.|
|STATUS_FLOAT_UNDERFLOW|Překročení velikosti nejmenšího záporného exponentu typu s plovoucí desetinnou čárkou.|
|STATUS_FLOATING_RESEVERED_OPERAND|Použití rezervovaného formátu s plovoucí desetinnou čárkou (nesprávné použití formátu).|
|STATUS_ILLEGAL_INSTRUCTION|Pokus o spuštění kódu instrukce, který procesor nedefinuje.|
|STATUS_PRIVILEGED_INSTRUCTION|Spuštění instrukce, která není v aktuálním režimu počítače povolena.|
|STATUS_INTEGER_DIVIDE_BY_ZERO|Dělení celočíselného typu hodnotou 0.|
|STATUS_INTEGER_OVERFLOW|Pokus o operaci, která překračuje rozsah celého čísla.|
|STATUS_SINGLE_STEP|Spuštění jedné instrukce v režimu krokování. Používáno pouze ladicími programy.|

Mnoho výjimek uvedených v předchozí tabulce by mělo být zpracováno ladicími programy, operačním systémem a jiným kódem nízké úrovně. S výjimkou chyb celých čísel a čísel s plovoucí desetinnou čárkou by váš kód neměl tyto chyby zpracovávat. Proto by měl být obvykle použit filtr pro zpracování výjimek, který výjimky ignoruje (vyhodnotí na hodnotu 0). V opačném případě může být mechanismům nižší úrovně zabráněno reagovat odpovídajícím způsobem. Však lze přijmout vhodná opatření proti potenciálním účinkům těchto chyb nízké úrovně [napsáním obslužných rutin ukončení](../cpp/writing-a-termination-handler.md).

## <a name="see-also"></a>Viz také:

[Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)