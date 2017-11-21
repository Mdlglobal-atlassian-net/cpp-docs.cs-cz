---
title: "Definování obslužné rutiny zpráv pro zrcadlené zprávy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.defining.msg.msghandler
dev_langs: C++
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a576ffdc7fcd637873045ee44e3a13a0a9647942
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Definování obslužné rutiny zpráv pro zrcadlené zprávy
Po vytvoření nové třídě ovládacího prvku MFC, můžete definovat obslužné rutiny zpráv pro ni. Zrcadlených zpráv umožňují vaší třídě zpracování vlastní zprávy před nadřízený objekt doručení zprávy. Můžete použít MFC [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) funkce k odesílání zpráv z ovládacího prvku do nadřazeného okna.  
  
 Pomocí této funkce lze například vytvořit seznam, který bude překreslit, namísto spoléhání na nadřazeného okna udělat (vlastní vykreslování). Další informace o reflektované zprávy naleznete v tématu [zpracování Reflektovaných zpráv](../../mfc/handling-reflected-messages.md).  
  
 Chcete-li vytvořit [ovládací prvek ActiveX](../../mfc/activex-controls-on-the-internet.md) s touto funkcí, musíte vytvořit projekt pro ovládací prvek ActiveX.  
  
> [!NOTE]
>  Nelze přidat zrcadlené zprávy (OCM_*zpráva*) pro prvku ActiveX řídit pomocí okna vlastností, jak je popsáno níže. Tyto zprávy je musí přidat ručně.  
  
### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-properties-window"></a>Chcete-li definovat obslužné rutiny zpráv pro zrcadlené zprávy v okně Vlastnosti  
  
1.  Přidání ovládacího prvku, jako je například seznam, ovládacím prvkem matrice, panel nástrojů nebo ovládacím prvkem strom, do projektu MFC.  
  
2.  V zobrazení tříd klikněte na název třídy ovládacího prvku.  
  
3.  V [vlastnosti – okno](/visualstudio/ide/reference/properties-window), se zobrazí v názvu třídy ovládacího prvku **název třídy** seznamu.  
  
4.  Klikněte **zprávy** tlačítko zobrazení zpráv systému Windows, které chcete přidat do ovládacího prvku.  
  
5.  Projděte dolů seznam zpráv v okně vlastností, dokud neuvidíte záhlaví **Reflected**. Klepnout **kategorie** tlačítko a sbalit zobrazení najdete v článku **Reflected** záhlaví.  
  
6.  Vyberte zrcadlené zprávy, pro které chcete definovat obslužnou rutinu. Reflektované zprávy jsou označené symbolem rovná se (=).  
  
7.  Klikněte na buňky v pravém sloupci v okně vlastností zobrazíte navrhovaný název obslužné rutiny jako \<Přidat >*HandlerName*. (Například **= WM_CTLCOLOR –** navrhuje obslužné rutiny zpráv \<Přidat >**CtlColor**).  
  
8.  Klikněte na název navržené tak, aby přijímal. Obslužná rutina se přidá do projektu.  
  
     V pravém sloupci okna reflektované zprávy se zobrazují názvy obslužné rutiny zpráv, které jste přidali.  
  
9. Chcete-li upravit nebo odstranit obslužné rutiny zpráv, opakujte kroky 4 až 7. Klikněte na buňku obsahující název obslužné rutiny upravit nebo odstranit, a klikněte na příslušnou úlohu.  
  
## <a name="see-also"></a>Viz také  
 [Mapování zpráv do funkcí](../../mfc/reference/mapping-messages-to-functions.md)   
 [Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Přidání třídy](../../ide/adding-a-class-visual-cpp.md)   
 [Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)   
 [Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Přepisování virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Popisovač zpráv knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navigace strukturou třídy](../../ide/navigating-the-class-structure-visual-cpp.md)
