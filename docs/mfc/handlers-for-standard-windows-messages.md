---
title: "Obslužné rutiny pro standardní zprávy Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- afx_msg
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 91df3462297c2a45a8938d815cc3b6a3b8ca6edb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="handlers-for-standard-windows-messages"></a>Obslužné rutiny pro standardní zprávy Windows
Výchozí obslužné rutiny pro standardní zprávy Windows (**WM_**) jsou předdefinované v třídě `CWnd`. Knihovny tříd základny názvy pro tyto obslužné rutiny na název zprávy. Třeba obslužná rutina pro `WM_PAINT` zprávy je deklarován v `CWnd` jako:  
  
 `afx_msg void OnPaint();`  
  
 **Afx_msg** – klíčové slovo navrhuje účinku C++ **virtuální** – klíčové slovo rozlišuje obslužných rutin se z jiných `CWnd` členské funkce. Upozorňujeme však, že tyto funkce nejsou ve skutečnosti virtuální; implementují se místo toho prostřednictvím mapy zpráv. Mapy zpráv závisí výhradně na standardní makra preprocesoru, nikoli na rozšíření jazyka C++. **Afx_msg** – klíčové slovo přeloží na mezer po předběžného zpracování.  
  
 K přepsání definovaná v základní třídě obslužná rutina, jednoduše zadejte funkce s stejné prototypu v odvozené třídě a a vytvořit položku mapy zpráv pro obslužnou rutinu. Vaší obslužné rutiny "přepíše" žádné obslužná rutina se stejným názvem v některém z vaší třídy základní třídy.  
  
 V některých případech vaší obslužné rutiny by měly volat obslužná rutina přepsaného v základní třídě tak může fungovat základní třídy a systému Windows na zprávu. Kde volání obslužná rutina základní třídy v přepsání závisí na v případech. Někdy musíte nejprve volání obslužná rutina základní třídy a někdy poslední. Někdy lze volat obslužná rutina základní třídy podmíněně, pokud se rozhodnete zpracovat zprávu sami. Někdy měli volání obslužná rutina základní třídy a pak podmíněnému spuštění vlastní kód obslužné rutiny, v závislosti na hodnotu nebo stav vrácený obslužná rutina základní třídy.  
  
> [!CAUTION]
>  Není bezpečné upravit argumenty předané do obslužnou rutinu, pokud máte v úmyslu předat obslužnou rutinu základní třídy. Například může být rozhodnout změnit `nChar` argument `OnChar` obslužné rutiny (převést na velká písmena, například). Toto chování je docela skrytého, ale pokud budete muset provést tento platit, použijte `CWnd` – členská funkce **SendMessage** místo.  
  
 Jak se určíte správný způsob, jak můžete přepsat danou zprávou, když okno Vlastnosti zapíše kostru funkce obslužné rutiny pro danou zprávu – `OnCreate` obslužné rutiny pro `WM_CREATE`, například – výkresy ji ve formě doporučené Přepsat – členská funkce. Následující příklad doporučuje obslužná rutina nejprve volání obslužná rutina základní třídy a pokračovat pouze tehdy, nevrátí hodnotu -1.  
  
 [!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]  
  
 Podle konvence názvy těchto obslužných rutinách začít s předponou "Na". Některé z těchto obslužných rutinách nepřebírají žádné argumenty, zatímco jiné přijímají několik. Některé také mít typ vrácené hodnoty jiné než `void`. Výchozí obslužné rutiny pro všechny **WM_** zprávy jsou dokumentovány v článku *odkaz knihovny MFC* jako funkce člena třídy `CWnd` jejichž názvy začínají řetězcem "Na". Členské funkce deklarace v `CWnd` mají předponu **afx_msg**.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)
