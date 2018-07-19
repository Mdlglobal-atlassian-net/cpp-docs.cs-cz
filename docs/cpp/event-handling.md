---
title: Zpracování událostí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], event handling
- intrinsic functions [C++], event handling
- event handling [C++], Visual C++
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d27ff977bf3e4132f7782c0ffcb85bebefd42d68
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961438"
---
# <a name="event-handling"></a>Zpracování událostí
Zpracování událostí se primárně podporuje pro třídy COM (třídy jazyka C++, které implementují objekty modelu COM, obvykle pomocí tříd knihovny ATL nebo [coclass](../windows/coclass.md) atributu).  Další informace najdete v tématu [zpracování událostí v modulu COM](../cpp/event-handling-in-com.md).  
  
 Zpracování událostí je také podporována pro nativních tříd jazyka C++ (třídy jazyka C++, které neimplementují objekty modelu COM), ale, že podpora je zastaralá a bude v budoucí verzi odebrána.  Další informace najdete v tématu [zpracování událostí v nativním kódu C++](../cpp/event-handling-in-native-cpp.md).  
  
 Zpracování událostí podporuje jeden a vícevláknové použití a chrání data před mělo současně přístup s více vlákny. Také umožňuje lze odvodit podtřídy ze zdroje události nebo třídy příjemce a podporu extended event sourcing a přijímáním v odvozené třídě.  
  
 Visual C++ obsahuje atributy a klíčová slova pro deklarování událostí a obslužných rutin událostí. Atributy událostí a klíčová slova lze použít v aplikacích CLR a v nativních aplikacích C++.  
  
|Téma|Popis|  
|-----------|-----------------|  
|[event_source](../windows/event-source.md)|Vytvoří zdroj událostí.|  
|[event_receiver](../windows/event-receiver.md)|Vytvoří přijímače událostí (jímky).|  
|[__event](../cpp/event.md)|Deklaruje událost.|  
|[__raise](../cpp/raise.md)|Zvýrazní stranu volání události.|  
|[__hook](../cpp/hook.md)|Přidruží metodu obslužné rutiny události.|  
|[__unhook](../cpp/unhook.md)|Dissociates metodu obslužné rutiny z události.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
