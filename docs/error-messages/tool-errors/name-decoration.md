---
title: Dekorování názvů
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: d1557f53a07a544ff4f9e5a63f905e6854fb74ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393152"
---
# <a name="name-decoration"></a>Dekorování názvů

Dekorování názvů obvykle odkazuje na zásady vytváření názvů C++, ale můžete použít na několik případů jazyka C i. Ve výchozím nastavení C++ používá název funkce, parametry a návratový typ pro vytvoření názvu linkeru pro funkci. Vezměte v úvahu následující deklarace funkce:

`void CALLTYPE test(void);`

V následující tabulce jsou uvedeny název linkeru pro různých konvencí volání.

|Konvence volání|`extern "C"` nebo `.c` souboru|`.cpp`, `.cxx` nebo `/TP`|
|------------------------|---------------------------|------------------------|
|Zásady vytváření názvů jazyka C (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|Zásady vytváření názvů rychlé volání (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|Standardní volání zásady vytváření názvů (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|Vector – konvence volání (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

Použití `extern "C"` volat funkci C z C++. `extern "C"` Vynutí použití zásady vytváření názvů jazyka C pro jiné třídy C++ funkce. Mějte přepínače kompilátoru **/Tc** nebo **/Tp**, zjistit, které kompilátor ignorovat příponu názvu souboru a zkompilujte soubor jako C nebo C++, v uvedeném pořadí. Tyto možnosti může způsobit názvy linkeru, který nemusíte očekávat.

Tato chyba může také způsobit s prototypy funkcí, které mají parametry neodpovídající. Dekorování názvů parametrů funkce zahrnuje do názvu poslední upravené funkce. Volání funkce s typy parametrů, které neodpovídají hodnotám v deklaraci funkce může také způsobit LNK2001.

Aktuálně neexistují žádné standardy pro C++ pojmenování mezi dodavateli kompilátoru nebo dokonce i mezi různými verzemi kompilátoru. Propojování souborů objektů kompilován jinými kompilátory nemusí poskytovat stejné schéma pojmenování a může způsobit nerozpoznané externí typy.

## <a name="see-also"></a>Viz také:

[Chyba linkerů LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)