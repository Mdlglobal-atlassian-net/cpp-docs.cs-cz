---
title: Dekorování názvů
ms.date: 09/05/2018
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: b916a73e0b8f86755384914fa85ef8a901e4a64c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041520"
---
# <a name="name-decoration"></a>Dekorování názvů

Dekorování názvů obvykle odkazuje na zásady vytváření názvů C++, ale můžete použít na několik případů jazyka C i. Ve výchozím nastavení C++ používá název funkce, parametry a návratový typ pro vytvoření názvu linkeru pro funkci. Vezměte v úvahu následující funkce:

```
void CALLTYPE test(void)
```

V následující tabulce jsou uvedeny název linkeru pro různých konvencí volání.

|Konvence volání|extern "C" nebo .c souboru|.cpp nebo .cxx /TP|
|------------------------|---------------------------|------------------------|
|Zásady vytváření názvů jazyka C (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|Zásady vytváření názvů fastcall (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|Standardní konvence volání (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|Zásady vytváření názvů Vectorcall (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

Extern "C" použijte k volání funkce C z jazyka C++. Extern "C" vynutí použití zásady vytváření názvů jazyka C pro funkce jazyka C++ jiné třídy. Mějte přepínače kompilátoru **/Tc** nebo **/Tp**, zjistit, které kompilátor ignorovat příponu názvu souboru a zkompilujte soubor jako C nebo C++, v uvedeném pořadí. Tyto možnosti může způsobit, že názvy, které nepočítáte.

Tato chyba může také způsobit s prototypy funkcí, které mají parametry neodpovídající. Dekorování názvů parametrů funkce zahrnuje do názvu poslední upravené funkce. Volání funkce s typy parametrů, které neodpovídají těm v deklaraci funkce může také způsobit LNK2001.

Aktuálně neexistuje žádný standardní pojmenování mezi dodavateli kompilátoru nebo dokonce i mezi různými verzemi kompilátoru jazyka c++. Proto propojování souborů objektů kompilován jinými kompilátory nemusí poskytovat stejné schéma pojmenování a proto způsobí, že nerozpoznané externí typy.

## <a name="see-also"></a>Viz také:

[Chyba linkerů LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)