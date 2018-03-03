---
title: "Jakým způsobem volá rámec váš kód | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- control flow [MFC], MFC framework and your code
- events [MFC], command routing in MFC
- command routing [MFC], framework
- command handling [MFC], calling handlers and code in MFC
- events [MFC], event-driven programming
- MFC, calling code from
- MFC, calling code
- application-specific events [MFC]
- command routing [MFC], MFC
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 83eeb1c7fd3032ae33c213f17522b171bdb46e55
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-the-framework-calls-your-code"></a>Jakým způsobem volá rámec váš kód
Je třeba pochopit o vztah mezi vašeho zdrojového kódu a kódu v rozhraní MFC framework. Při spuštění aplikace většinu toku řízení se nachází v rozhraní framework kódu. Rozhraní framework spravuje smyčce zpráv, který získá zprávy ze systému Windows se uživatel rozhodne příkazy a upravuje dat zobrazení. Události, které rozhraní může zpracovat samostatně nespoléhejte na váš kód vůbec. Například rozhraní znát postup zavřete okna a ukončete aplikaci v reakci na příkazy uživatele. Jako s tyto úlohy, používá rozhraní obslužné rutiny zpráv a virtuálních funkcí jazyka C++ tak, abyste získali příležitosti reagovat na tyto události také. Váš kód nejsou v ovládacím prvku, ale; rozhraní je.  
  
 Pro události specifické pro aplikace volá rámec váš kód. Například když uživatel vybere příkaz nabídky, rozhraní směruje příkaz podél posloupnost objekty C++: aktuální okno zobrazení a rámečku, dokument přidružený k zobrazení, Šablona dokumentu dokumentu a objekt aplikace. Pokud některý z těchto objektů můžete zpracovat příkaz, nemá tedy volání funkce odpovídající popisovač zpráv. Pro všechny daný příkaz kódu volaného může být váš nebo může být rozhraní framework.  
  
 Toto uspořádání je poněkud dobře známé pro programátory v jazyce se zkušenostmi s tradiční programování pro systém Windows nebo událostmi řízené programování.  
  
 Příbuzná témata budou číst co rozhraní jak inicializuje a spustí aplikaci a potom vyčistí jako ukončí aplikaci. Bude také chápou, kde se vejde kód, který můžete psát.  
  
 Další informace najdete v tématu [CWinApp – třída: třídy aplikace](../mfc/cwinapp-the-application-class.md) a [šablony dokumentů a proces tvorby Document/View](../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="see-also"></a>Viz také  
 [Sestavení na základě rozhraní .NET Framework](../mfc/building-on-the-framework.md)

