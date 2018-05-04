---
title: Zpracování událostí | Microsoft Docs
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
ms.openlocfilehash: 09029f3afef0a9a28fdc572b9b7d8685cf76e811
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="event-handling"></a>Zpracování událostí
Zpracování událostí je primárně podporována pro třídy COM (C++ třídy, které implementují objekty modelu COM, obvykle pomocí třídy ATL nebo [třída typu coclass](../windows/coclass.md) atributu).  Další informace najdete v tématu [zpracování událostí v modelu COM](../cpp/event-handling-in-com.md).  
  
 Zpracování událostí je také podporována pro nativních tříd jazyka C++ (C++ třídy, které neimplementují objekty modelu COM), ale, že podpora se již nepoužívá a bude v budoucí verzi odebrána.  Další informace najdete v tématu [zpracování událostí v nativním kódu C++](../cpp/event-handling-in-native-cpp.md).  
  
 Zpracování událostí podporuje jeden a vícevláknové použití a chrání data z současně s více vlákny přístup. Můžete taky odvození podtřídy ze zdroje událostí nebo třídy příjemce a podporu rozšířených událostí sourcing a přijímáním v odvozené třídě.  
  
 Visual C++ zahrnuje atributy a klíčová slova pro deklarace události a obslužné rutiny událostí. Klíčová slova a atributy události lze použít v CLR programy a nativní C++ – programy.  
  
|Téma|Popis|  
|-----------|-----------------|  
|[event_source](../windows/event-source.md)|Vytvoří zdroje událostí.|  
|[event_receiver](../windows/event-receiver.md)|Vytvoří přijímače událostí (jímky).|  
|[__event](../cpp/event.md)|Deklaruje událost.|  
|[__raise](../cpp/raise.md)|Zvýrazní stranu volání události.|  
|[__hook](../cpp/hook.md)|Přidruží metoda obslužná rutina události.|  
|[__unhook](../cpp/unhook.md)|Dissociates z událost metodu obslužné rutiny.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Ukázky zpracování událostí](http://msdn.microsoft.com/en-us/cc0287d4-f92b-4da5-85fc-a0f186e16424)