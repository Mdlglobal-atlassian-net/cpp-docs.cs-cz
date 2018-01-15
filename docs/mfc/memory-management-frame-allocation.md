---
title: "Správa paměti: Přidělení s rámečkem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory leaks [MFC], frame allocation
- memory [MFC], detecting leaks
- memory [MFC], reclaiming
- memory allocation [MFC], frames
- frame variables [MFC], automatic deletion of
- scope [MFC], frame variables
- heap allocation [MFC], vs. frame allocation
- variables [MFC], frame variables
- memory leaks [MFC], detecting
- memory, releasing [MFC]
- stack frames [MFC]
- memory leaks [MFC], allocating objects on the frame
- detecting memory leaks [MFC]
- frame allocation [MFC]
- frame variables [MFC]
ms.assetid: 945a211a-6f4f-4679-bb6a-b0f2a0d4a6c1
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 03a8e5f81e55398ffba30479ecfafc42726e9519
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="memory-management-frame-allocation"></a>Správa paměti: Přidělení rámců
Přidělení rámec trvá jeho název z "rámce zásobníku", který je nastaven vždy, když je volána funkce. Rámec zásobníku je oblast paměti, která dočasně obsahuje argumenty funkce a také všechny proměnné, které jsou definovány místní funkce. Proměnné rámce se často nazývají "automatické" proměnné, protože kompilátor automaticky přiděluje místo pro ně.  
  
 Existují dva klíče charakteristika přidělení rámce. Nejprve když definujete proměnnou místní, dostatek místa na přiděluje rámce zásobníku pro uložení celé proměnnou, i když je velké pole nebo datová struktura. Proměnné rámce druhý, automaticky se odstraní při jejich se dostala mimo rozsah:  
  
 [!code-cpp[NVC_MFC_Utilities#10](../mfc/codesnippet/cpp/memory-management-frame-allocation_1.cpp)]  
  
 Pro místní funkce proměnné tento přechod oboru se stane, když funkce ukončí, ale rozsahu proměnné rámce může být menší než funkci, pokud se používají vnořené složené závorky. Toto automatické odstranění proměnné rámce je velmi důležité. V případě jednoduchého primitivní typy (například `int` nebo **bajtů**), pole nebo datové struktury, automatické odstranění jednoduše získá množství paměti používané proměnnou. Vzhledem k tomu, že proměnná byla mimo rozsah, nelze přesto přistupovat. V případě objekty C++ ale proces automatické odstranění je trochu složitější.  
  
 Pokud objekt je definován jako proměnnou a rámečku, jeho konstruktor se automaticky vyvolá v okamžiku, kdy došlo k definici. Když se objekt dostane mimo rozsah, jeho destruktor se automaticky vyvolá předtím, než je uvolnit paměť pro objekt. Toto automatické vytváření a odstraňování může být velmi užitečný, ale musíte být vědomi automatické volání, především při destruktoru.  
  
 Hlavní výhodou přidělování objektů na rámci je, že se automaticky odstraní. Při přidělování vašich objektů v rámečku, nemusíte starat o zapomenuté objekty způsobuje nevracení paměti. (Podrobnosti o nevracení paměti najdete v článku [zjišťování nevracení paměti v prostředí MFC](http://msdn.microsoft.com/en-us/29ee8909-96e9-4246-9332-d3a8aa8d4658).) Přidělení rámce tu nevýhodu, že proměnné rámce se nedají použít mimo jejich oboru. Jiné faktorem při volbě přidělení rámce oproti přidělení haldy je, že pro velké struktury a objekty, je často lepší použít halda místo v zásobníku úložiště, protože je často omezená místa v zásobníku.  
  
## <a name="see-also"></a>Viz také  
 [Správa paměti](../mfc/memory-management.md)

