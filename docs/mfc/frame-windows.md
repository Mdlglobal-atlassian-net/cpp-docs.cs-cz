---
title: Okna s rámečkem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document frame windows [MFC]
- windows [MFC], MDI
- window classes [MFC], frame
- single document interface (SDI) [MFC]
- single document interface (SDI) [MFC], frame windows
- views [MFC], and frame windows
- CFrameWnd class [MFC], frame windows
- frame windows [MFC]
- frame windows [MFC], about frame widows
- MFC, frame windows
- MDI [MFC], frame windows
- splitter windows [MFC], and frame windows
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 515df19bcc11f7a6706985014fc44bc4ff315f36
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="frame-windows"></a>Okna s rámečkem
Pokud je aplikace spuštěna v systému Windows, uživatel pracuje s dokumenty zobrazí v oknech s rámečkem. Okně s rámečkem dokumentu tvoří dvě hlavní součásti: rámečku a obsah, který se snímky. Může být okně s rámečkem dokumentu [rozhraní s jedním dokumentem](../mfc/sdi-and-mdi.md) oken s rámečkem (SDI) nebo [rozhraní více dokumentů](../mfc/sdi-and-mdi.md) podřízeného okna (MDI). Systém Windows spravuje většinu interakce uživatele se okně s rámečkem: přesunutí a změna velikosti okna, zavřít a současně minimalizujete její a jeho maximalizaci. Můžete spravovat obsah uvnitř rámečku.  
  
## <a name="frame-windows-and-views"></a>Zobrazení a oken s rámečkem  
 Rozhraní MFC framework používá okna s rámečkem tak, aby obsahovala zobrazení. Dvě komponenty – včetně obsahu – jsou reprezentována a spravuje dvou různých tříd v prostředí MFC. Třídy oken s rámečkem spravuje rámečku, a třídu zobrazení obsahu. Okno zobrazení je podřízená rámce okna. Kreslení a další interakce uživatele s dokumentu provádět v zobrazení klientské oblasti není klientské oblasti rámce okna. Okně s rámečkem poskytuje viditelné rámečku kolem zobrazení s záhlaví a standardní okno Ovládací prvky, jako je například ovládací prvek nabídky, tlačítek a minimalizovat maximalizujte okno a ovládací prvky pro změnu velikosti okna. "Obsah" skládat z okna klienta oblast, která je plně obsazena podřízeného okna – zobrazení. Následující obrázek znázorňuje vztahy mezi okně s rámečkem a zobrazení.  
  
 ![Zobrazení v okně s rámečkem](../mfc/media/vc37fx1.gif "vc37fx1")  
Oken s rámečkem a zobrazení  
  
## <a name="frame-windows-and-splitter-windows"></a>Okna s rámečkem a rozdělovače oken  
 Další běžné uspořádání je rámce okna s rámečkem více zobrazení, obvykle pomocí [rozděleném okně](../mfc/multiple-document-types-views-and-frame-windows.md). V okně rozdělovače rámce okna klientské oblasti obsazena rozděleném okně, která naopak má více podřízených oken, názvem podokna, které jsou zobrazení.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
 **Témata týkající se oken s rámečkem obecné**  
  
-   [Objekty oken](../mfc/window-objects.md)  
  
-   [Třídy oken s rámečkem](../mfc/frame-window-classes.md)  
  
-   [Třídy oken s rámečkem vytvořené průvodcem aplikací](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [Styly oken s rámečkem](../mfc/frame-window-styles-cpp.md)  
  
-   [Co dělat okna s rámečkem](../mfc/what-frame-windows-do.md)  
  
 **Témata týkající se použití oken s rámečkem**  
  
-   [Použití oken s rámečkem](../mfc/using-frame-windows.md)  
  
-   [Vytváření dokumentů, oken s rámečkem](../mfc/creating-document-frame-windows.md)  
  
-   [Zničení oken s rámečkem](../mfc/destroying-frame-windows.md)  
  
-   [Správa podřízených oken MDI](../mfc/managing-mdi-child-windows.md)  
  
-   [Správa aktuálního zobrazení](../mfc/managing-the-current-view.md) v okně s rámečkem, který obsahuje více než jedno zobrazení  
  
-   [Správa nabídek, ovládacích pruhů a akcelerátorů (jiné objekty, které sdílejí prostor rámce okna)](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
 **Témata týkající se možnosti speciální rámce okna**  
  
-   [Přetahování souborů](../mfc/dragging-and-dropping-files-in-a-frame-window.md) z Průzkumníka souborů nebo Správce souborů v okně s rámečkem  
  
-   [Odpověď na dynamickou výměnu dat (DDE)](../mfc/responding-to-dynamic-data-exchange-dde.md)  
  
-   [Semimodální stavy: Context-sensitive nápovědy pro Windows (Orchestrace dalších akcí okna)](../mfc/orchestrating-other-window-actions.md)  
  
-   [Semimodální stavy: tisku a tiskového náhledu (Orchestrace dalších akcí okna)](../mfc/orchestrating-other-window-actions.md)  
  
 **Témata na jiné druhy oken**  
  
-   [Použití zobrazení](../mfc/using-views.md)  
  
-   [Dialogová okna](../mfc/dialog-boxes.md)  
  
-   [Ovládací prvky](../mfc/controls-mfc.md)  
  
## <a name="see-also"></a>Viz také  
 [Windows](../mfc/windows.md)

