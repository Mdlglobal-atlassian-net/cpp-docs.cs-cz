---
title: "Směrování příkazů | Microsoft Docs"
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
- MFC, command routing
- command handling [MFC], routing commands
- handlers [MFC]
- handlers, command [MFC]
- command routing
ms.assetid: 9393a956-bdd4-47c5-9013-dbd680433f93
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4299d5bb0f638d33714a5b5daeff60fde3f49be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="command-routing"></a>Směrování příkazů
Vaše odpovědnosti při práci s příkazy je omezený na vytváření map zpráv spojení mezi příkazy a jejich funkce obslužné rutiny, pro kterou použijte okno Vlastnosti úlohy. Také musíte napsat většina obslužné rutiny příkazů.  
  
 Zprávy Windows se obvykle odesílají do okna hlavního rámce, ale příkaz zprávy pak směrují na jiné objekty. Rozhraní framework směrování příkazů prostřednictvím standardní pořadí příkaz cílové objekty, z nichž jeden by měl být obslužná rutina příkazu. Každý příkaz cílový objekt ověří jeho mapy zpráv zobrazíte, pokud ho může zpracovávat příchozí zprávy.  
  
 Různé třídy cíl příkazu zkontrolujte že mapy vlastní zpráv v různých časech. Obvykle třídu směruje příkaz k určitým objektům a umožnit jim první příležitosti v příkazu. Pokud žádná z těchto objektů zpracovává příkaz, původní třída zkontroluje vlastní mapy zpráv. Pak pokud ho nelze zadat obslužnou rutinu sám sebe, se může směrovat příkaz ještě další cíle příkazů. V tabulce [standardních příkazů trasy](#_core_standard_command_route) níže ukazuje, jak každý z třídy struktury toto pořadí. Obecné pořadí, ve kterém směruje příkaz cíl příkazu je:  
  
1.  K jeho aktuálně aktivních podřízených příkaz cílový objekt.  
  
2.  Na sebe sama.  
  
3.  Pro jiné cíle příkazů.  
  
 Jak nákladné je tento mechanismus směrování porovnání vaší obslužné rutiny nemá v reakci na příkaz, náklady směrování je nízký. Berte v úvahu, že rozhraní generuje příkazy jenom v případě, že uživatel pracuje s objektem uživatelského rozhraní.  
  
### <a name="_core_standard_command_route"></a>Standardní příkaz trasy  
  
|Pokud objekt tohoto typu přijme příkaz. . .|Nabízí samostatně a další příkaz cílové objekty příležitosti pro zpracování příkazu v tomto pořadí:|  
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|  
|Rámec okna MDI (`CMDIFrameWnd`)|1.  Aktivní`CMDIChildWnd`<br />2.  Tato oken s rámečkem<br />3.  Aplikace (`CWinApp` objekt)|  
|Rámec okna dokumentu (`CFrameWnd`, `CMDIChildWnd`)|1.  Aktivní zobrazení<br />2.  Tato oken s rámečkem<br />3.  Aplikace (`CWinApp` objekt)|  
|Zobrazit|1.  Toto zobrazení<br />2.  Dokument připojený k zobrazení|  
|Dokument|1.  Tento dokument<br />2.  Šablona dokumentu, které jsou připojené k dokumentu|  
|Dialogové okno|1.  Toto dialogové okno<br />2.  Okno, které vlastní dialogových oken<br />3.  Aplikace (`CWinApp` objekt)|  
  
 Kde číslované položky v druhém sloupci v předchozí tabulce zmínili jiné objekty, jako je například dokument, najdete v položce odpovídající z prvního sloupce. Například při čtení v druhém sloupci, zobrazení předává příkaz k jeho dokumentu, najdete v položce "Dokumentu" prvního sloupce podle další směrování.  
  
## <a name="see-also"></a>Viz také  
 [Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

