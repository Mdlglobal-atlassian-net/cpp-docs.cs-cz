---
title: Zpracování událostí
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
ms.openlocfilehash: cf16ea0e6e14981f1105456a5f17d68c05a9c3fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189205"
---
# <a name="event-handling"></a>Zpracování událostí

Zpracování událostí je primárně podporováno pro třídy COM (C++ třídy, které implementují objekty COM, obvykle pomocí tříd ATL nebo atributu [Coclass](../windows/coclass.md) ). Další informace najdete v tématu [zpracování událostí v modelu COM](../cpp/event-handling-in-com.md).

Zpracování událostí je podporované i pro nativní C++ třídy (C++ třídy, které neimplementují objekty com), ale tato podpora je zastaralá a v budoucí verzi se odebere.  Další informace naleznete v tématu [zpracování událostí v nativním režimu C++ ](../cpp/event-handling-in-native-cpp.md).

Zpracování událostí podporuje jednorázové a vícevláknové využití a chrání data proti souběžnému přístupu s více vlákny. Umožňuje také odvodit podtřídy ze tříd zdroje událostí nebo přijímače a podporovat zdroj a příjem rozšířených událostí v odvozené třídě.

Kompilátor společnosti C++ Microsoft obsahuje atributy a klíčová slova pro deklarování událostí a obslužných rutin událostí. Atributy události a klíčová slova lze použít v programech CLR a v nativních C++ programech.

|Téma|Popis|
|-----------|-----------------|
|[event_source](../windows/attributes/event-source.md)|Vytvoří zdroj události.|
|[event_receiver](../windows/attributes/event-receiver.md)|Vytvoří přijímač událostí (jímka).|
|[__event](../cpp/event.md)|Deklaruje událost.|
|[__raise](../cpp/raise.md)|Zvýrazní stranu volání události.|
|[__hook](../cpp/hook.md)|Přidruží metodu obslužné rutiny k události.|
|[__unhook](../cpp/unhook.md)|Dissociates metodu obslužné rutiny z události.|

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
