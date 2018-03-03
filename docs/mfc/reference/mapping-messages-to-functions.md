---
title: "Mapování zpráv do funkcí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.mapping.msg.function
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], adding message handlers
- message maps [MFC], mapping messages to functions
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad36b249e601e15e25f32ef1ef7e6d5a28874cf1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mapping-messages-to-functions"></a>Mapování zpráv na funkce
Okno vlastností umožňuje vytvořit vazbu obslužné rutiny zpráv (členské funkce tříd MFC uživatelského rozhraní) zprávy generované zdrojů vaší aplikace. Používají [mapy zpráv knihovny MFC](../../mfc/messages-and-commands-in-the-framework.md) pro vytvoření vazby.  
  
 Použijete-li vytvořit nové třídy odvozené od jedné ze tříd framework zobrazení tříd, se automaticky místech kompletní a funkční třídy v hlavičky () a implementace (sada) soubory, které zadáte.  
  
> [!NOTE]
>  Pokud chcete přidat novou třídu, která zpracovává zprávy, vytvořte třídu přímo v textovém editoru.  
  
### <a name="to-define-or-remove-a-message-handler-using-the-properties-window"></a>Definování nebo odebrat pomocí okna Vlastnosti obslužné rutiny zpráv  
  
1.  V zobrazení tříd klikněte na třídu.  
  
2.  V okně vlastností klikněte **zprávy** tlačítko.  
  
    > [!NOTE]
    >  **Zprávy** tlačítko je k dispozici, když vyberete název třídy v zobrazení tříd nebo když kliknete na okno zdrojového kódu.  
  
     Pokud váš projekt má obslužné rutiny pro zprávy, název obslužné rutiny zobrazí v pravém sloupci vedle zprávy.  
  
3.  Pokud zpráva nemá žádná obslužná rutina, klikněte na buňku v pravém sloupci v okně vlastností zobrazíte navrhovaný název obslužné rutiny jako \<Přidat >*HandlerName*. (Například `WM_TIMER` navrhuje obslužné rutiny zpráv \<Přidat >`OnTimer`).  
  
4.  Klikněte na tlačítko Přidat se zakázaným inzerováním kódu pro funkce navrhovaný název.  
  
5.  Úpravy obslužné rutiny zpráv, dvakrát klikněte na zprávu ve třídě zobrazení a úpravy kódu v okně zdroje.  
  
 Pokud chcete odebrat obslužné rutiny zpráv, klikněte dvakrát na obslužnou rutinu v pravém sloupci a vyberte \<odstranit >*HandlerName*. Kód funkce je označeno jako komentář.  
  
## <a name="see-also"></a>Viz také  
 [Popisovač zpráv knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Přidání třídy](../../ide/adding-a-class-visual-cpp.md)   
 [Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)   
 [Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Přepisování virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Přidání obslužných rutin událostí pro ovládací prvky dialogové okno](../../windows/adding-event-handlers-for-dialog-box-controls.md)   
 [Navigace strukturou třídy](../../ide/navigating-the-class-structure-visual-cpp.md)
