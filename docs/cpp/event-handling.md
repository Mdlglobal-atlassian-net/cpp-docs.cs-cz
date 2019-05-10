---
title: Zpracování událostí
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
ms.openlocfilehash: bd74ba0b20e2058f0b04d0d0d3c22c9d526157a0
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222120"
---
# <a name="event-handling"></a>Zpracování událostí

Zpracování událostí se primárně podporuje pro třídy COM (třídy jazyka C++, které implementují objekty modelu COM, obvykle pomocí tříd knihovny ATL nebo [coclass](../windows/coclass.md) atributu). Další informace najdete v tématu [zpracování událostí v modulu COM](../cpp/event-handling-in-com.md).

Zpracování událostí je také podporována pro nativních tříd jazyka C++ (třídy jazyka C++, které neimplementují objekty modelu COM), ale, že podpora je zastaralá a bude v budoucí verzi odebrána.  Další informace najdete v tématu [zpracování událostí v nativním kódu C++](../cpp/event-handling-in-native-cpp.md).

Zpracování událostí podporuje jeden a vícevláknové použití a chrání data před mělo současně přístup s více vlákny. Také umožňuje lze odvodit podtřídy ze zdroje události nebo třídy příjemce a podporu extended event sourcing a přijímáním v odvozené třídě.

Microsoft C++ kompilátor obsahuje atributy a klíčová slova pro deklarování událostí a obslužných rutin událostí. Atributy událostí a klíčová slova lze použít v aplikacích CLR a v nativních aplikacích C++.

|Téma|Popis|
|-----------|-----------------|
|[event_source](../windows/attributes/event-source.md)|Vytvoří zdroj událostí.|
|[event_receiver](../windows/attributes/event-receiver.md)|Vytvoří přijímače událostí (jímky).|
|[__event](../cpp/event.md)|Deklaruje událost.|
|[__raise](../cpp/raise.md)|Zvýrazní stranu volání události.|
|[__hook](../cpp/hook.md)|Přidruží metodu obslužné rutiny události.|
|[__unhook](../cpp/unhook.md)|Dissociates metodu obslužné rutiny z události.|

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)