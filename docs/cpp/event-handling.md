---
title: "Zpracování událostí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- attributes [C++], event handling
- intrinsic functions [C++], event handling
- event handling [C++], Visual C++
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1ae45cf1ea8b2540038bab12f28c244ed7b5de7a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="event-handling"></a>Zpracování událostí
Zpracování událostí je primárně podporována pro třídy COM (C++ třídy, které implementují objekty modelu COM, obvykle pomocí třídy ATL nebo [třída typu coclass](../windows/coclass.md) atributu).  Další informace najdete v tématu [zpracování událostí v modelu COM](../cpp/event-handling-in-com.md).  
  
 Zpracování událostí je také podporována pro nativních tříd jazyka C++ (C++ třídy, které neimplementují objekty modelu COM), ale, že podpora se již nepoužívá a bude v budoucí verzi odebrána.  Další informace najdete v tématu [zpracování událostí v nativním kódu C++](../cpp/event-handling-in-native-cpp.md).  
  
 Zpracování událostí podporuje jeden a vícevláknové použití a chrání data z současně s více vlákny přístup. Můžete taky odvození podtřídy ze zdroje událostí nebo třídy příjemce a podporu rozšířených událostí sourcing a přijímáním v odvozené třídě.  
  
 Visual C++ zahrnuje atributy a klíčová slova pro deklarace události a obslužné rutiny událostí. Klíčová slova a atributy události lze použít v CLR programy a nativní C++ – programy.  
  
|Téma|Popis|  
|-----------|-----------------|  
|[event_source –](../windows/event-source.md)|Vytvoří zdroje událostí.|  
|[event_receiver –](../windows/event-receiver.md)|Vytvoří přijímače událostí (jímky).|  
|[__Event](../cpp/event.md)|Deklaruje událost.|  
|[__raise](../cpp/raise.md)|Zvýrazní stranu volání události.|  
|[__hook](../cpp/hook.md)|Přidruží metoda obslužná rutina události.|  
|[__unhook](../cpp/unhook.md)|Dissociates z událost metodu obslužné rutiny.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Ukázky zpracování událostí](http://msdn.microsoft.com/en-us/cc0287d4-f92b-4da5-85fc-a0f186e16424)