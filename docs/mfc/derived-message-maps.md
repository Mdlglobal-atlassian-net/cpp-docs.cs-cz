---
title: Odvozené mapy zpráv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e780d411e62d1347d8286f86b45df864b0fcdb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="derived-message-maps"></a>Mapy odvozených zpráv
Během zpracování, kontrola zprávu třídy a vlastní zprávy mapy není konec scénář map zpráv. Co se stane, když třída `CMyView` (odvozený z `CView`) nemá odpovídající záznam zprávy  
  
 Mějte na paměti, `CView`, základní třídu `CMyView`, je zase odvozený od `CWnd`. Proto `CMyView` *je* `CView` a *je* `CWnd`. Každý z těchto tříd má svou vlastní mapy zpráv. Obrázek "A zobrazit hierarchii" níže ukazuje hierarchický vztah třídy, ale mějte na paměti, že `CMyView` objekt je jeden objekt, který má vlastnosti všech tří tříd.  
  
 ![Hierarchie zobrazení](../mfc/media/vc38621.gif "vc38621")  
Zobrazení hierarchie  
  
 Pokud nelze porovnat zprávu ve třídě `CMyView`na mapy zpráv, rozhraní také prohledává mapy zpráv jeho okamžitou základní třídy. `BEGIN_MESSAGE_MAP` Makro na začátku mapy zpráv určuje dva názvy tříd jako její argumenty:  
  
 [!code-cpp[NVC_MFCMessageHandling#2](../mfc/codesnippet/cpp/derived-message-maps_1.cpp)]  
  
 První argument názvy třídy, do které patří mapy zpráv. Druhý argument poskytuje připojení s přímé základní třídy – `CView` zde – tak jeho mapy zpráv může hledat příliš rozhraní.  
  
 Obslužné rutiny zpráv, které jsou součástí základní třídy jsou děděné proto v odvozené třídě. Toto je velmi podobně jako normální virtuální členské funkce bez nutnosti, aby všechny funkce člen obslužná rutina virtuální.  
  
 Pokud žádná obslužná rutina je nalezena v žádném z mapy zpráv základní třídy, se provádí zpracování výchozí zprávy. Pokud zpráva je příkaz, rozhraní se směruje na Další cíl příkazu. Pokud je standardní zprávy Windows, je zpráva předaný procedury okna odpovídající výchozí.  
  
 Na rychlost mapování zpráv odpovídající, rozhraní ukládá do mezipaměti poslední odpovídá na pravděpodobnost, že ho stejnou zprávu přijme znovu. Důsledkem tohoto objektu je procesy framework velmi efektivně neošetřená zprávy. Mapy zpráv jsou také místo efektivnější než implementace, které používají virtuální funkce.  
  
## <a name="see-also"></a>Viz také  
 [Jak framework prohledává mapy zpráv](../mfc/how-the-framework-searches-message-maps.md)

