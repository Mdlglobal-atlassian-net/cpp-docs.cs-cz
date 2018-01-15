---
title: "Použití ovládacích prvků strom | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CTreeCtrl class [MFC], using
- tree controls [MFC], about tree controls
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea3b7e0348cb21aa4338293f7cc1119e380f92dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-tree-controls"></a>Použití ovládacích prvků strom
Typické použití ovládacího prvku strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) se následující níže:  
  
-   Ovládací prvek je vytvořen. Jestliže se ovládací prvek v poli šablony dialogového okna, nebo pokud používáte `CTreeView`, po vytvoření automatického při vytvoření dialogového nebo zobrazení. Pokud chcete vytvořit ovládací prvek stromu jako podřízeného okna Další okna, použijte [vytvořit](../mfc/reference/ctreectrl-class.md#create) – členská funkce.  
  
-   Pokud chcete, aby vaše ovládací prvek stromu používat bitové kopie, nastavte seznamu obrázků voláním [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist). Můžete také změnit odsazení voláním [SetIndent](../mfc/reference/ctreectrl-class.md#setindent). Vhodná doba na k tomu je v [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) (pro ovládací prvky v dialogových oknech) nebo [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) (pro zobrazení).  
  
-   Ukládat data do ovládacího prvku voláním `CTreeCtrl`na [metody InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) funkce jednou pro každou položku dat. `InsertItem`Vrátí popisovač pro položku, kterou můžete použít k odkazování na ho později, například při přidání podřízené položky. Je vhodná doba k chybě při inicializaci dat v `OnInitDialog` (pro ovládací prvky v dialogových oknech) nebo `OnInitialUpdate` (pro zobrazení).  
  
-   Jako uživatel pracuje s ovládacím prvkem, odešle různých zpráv s oznámením. Můžete zadat funkci pro zpracování jednotlivých zpráv chcete zpracovat tak, že přidáte **on_notify_reflect –** makro v mapy zpráv okno řízení nebo přidáním `ON_NOTIFY` makro do nadřazeného okna mapa zpráv. V tématu [zprávy s oznámením ovládacího prvku strom](../mfc/tree-control-notification-messages.md) dál v tomto tématu pro seznam možných oznámení.  
  
-   Volání různé sady členské funkce pro nastavení hodnot pro ovládací prvek. Změny, které můžete provést zahrnují nastavení odsazení a změna text, image nebo data přidružená položce.  
  
-   Zkontrolujte obsah ovládacího prvku pomocí různých funkcí Get. Také můžete procházet obsah ovládacího prvku strom s funkcemi, které vám umožní načíst popisovače nadřazených položek, děti a zadané položky na stejné úrovni. Můžete řadit i podřízené objekty daného konkrétním uzlu.  
  
-   Když jste hotovi s ovládacím prvkem, zkontrolujte, zda že je správně zničena. Pokud ovládací prvek stromu je v dialogovém okně nebo pokud se jedná o zobrazení ho a `CTreeCtrl` objektu budou automaticky zničena. Pokud ne, musíte zajistit, aby obě ovládacího prvku a `CTreeCtrl` objekt jsou správně zničena.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

