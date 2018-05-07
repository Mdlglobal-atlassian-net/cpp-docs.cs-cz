---
title: Zpráva mapy (MFC) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d1479ac7cb119ef206f8c20b6fa53bf7017b8ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="message-maps-mfc"></a>Mapy zpráv (MFC)
Tato část obsahuje seznam všech [makra mapování zpráv](../../mfc/reference/message-map-macros-mfc.md) a všechny [CWnd](../../mfc/reference/cwnd-class.md) map zpráv položky spolu s odpovídající členské funkce prototypy:  
  
|Kategorie|Popis|  
|--------------|-----------------|  
|ON\_příkaz obslužné rutiny zpráv|Zpracovává `WM_COMMAND` zprávy vytvářené nabídky Výběr uživatelů nebo nabídky přístupové klíče.|  
|[Obslužné rutiny oznamovacích zpráv v podřízených oknech](../../mfc/reference/child-window-notification-message-handlers.md)|Zpracování zpráv s oznámením z podřízené windows.|  
|[Wm_ – obslužné rutiny zpráv](../../mfc/reference/handlers-for-wm-messages.md)|Zpracování `WM_` zprávy, jako například `WM_PAINT`.|  
|[Obslužné rutiny zpráv uživatelem definované](../../mfc/reference/user-defined-handlers.md)|Zpracování zpráv definovaný uživatelem.|  
  
 (Vysvětlení terminologie a pravidla týkající se používá v této referenci, najdete v článku [použití křížových odkazů mapování zpráv](../../mfc/reference/how-to-use-the-message-map-cross-reference.md).)  
  
 Vzhledem k tomu, že Windows je operační systém orientovaný na zprávy, zahrnuje velkou část programování pro prostředí Windows zpracování zpráv. Dojde k pokaždé, když na událost, jako například klávesu nebo myš, pro aplikaci, které musí pak zpracovat událost je odeslána zpráva.  
  
 Knihovny Microsoft Foundation Class nabízí programovací model optimalizovaná pro programování na základě zpráv. V tomto modelu "zpráva mapy" slouží k určení, které funkce bude zpracovávat různé zpráv pro určitou třídu. Mapy zpráv obsahovat jeden nebo více makra, které určují, které zprávy bude zpracovávat funkcích, které. Například zpráva mapy obsahující `ON_COMMAND` makro může vypadat přibližně takto:  
  
 [!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]  
  
 `ON_COMMAND` Makro slouží ke zpracování příkazu zprávy generované nabídky, tlačítek a klávesy akcelerátoru. [Makra](../../mfc/reference/message-map-macros-mfc.md) jsou k dispozici pro mapování následující:  
  
## <a name="windows-messages"></a>Zprávy Windows  
  
-   Oznámení ovládacího prvku  
  
-   Uživatelsky definované  
  
## <a name="command-messages"></a>Příkaz zprávy  
  
-   Zaregistrovat uživatelem definované zprávy  
  
-   Zprávy o aktualizaci uživatelského rozhraní  
  
## <a name="ranges-of-messages"></a>Oblasti zpráv  
  
-   Příkazy  
  
-   Aktualizujte obslužné rutiny zpráv  
  
-   Oznámení ovládacího prvku  
  
 Makra map zpráv jsou důležité, obvykle nebudete mít používat přímo. To je proto okno vlastností automaticky vytvoří položky map zpráv ve zdrojových souborech, při použití funkce zpracování zpráv přidružit zprávy. Kdykoli, kterou chcete upravit nebo přidat položku mapování zpráv můžete okno vlastností.  
  
> [!NOTE]
>  Okno vlastností nepodporuje oblasti map zpráv. Tyto položky map zpráv musíte napsat sami.  
  
 Mapy zpráv však jsou důležitou součástí knihovny Microsoft Foundation Class. Byste měli porozumět, co dělají a dokumentace se poskytuje pro ně.  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

