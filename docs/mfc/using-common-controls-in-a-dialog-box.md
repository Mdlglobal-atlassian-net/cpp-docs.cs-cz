---
title: Použití běžných ovládacích prvků v dialogovém okně | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- dialog box controls [MFC], common controls
- Windows common controls [MFC], in dialog boxes
ms.assetid: 17713caf-09f8-484a-bf54-5f48bf09cce9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c848cfa74363d871720f9ca269b114687aad9ecf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-common-controls-in-a-dialog-box"></a>Použití běžných ovládacích prvků v dialogovém okně
Běžné ovládací prvky Windows lze použít v [dialogová okna](../mfc/dialog-boxes.md), tvoří zobrazení, zobrazení záznamů a další okno, podle šablony dialogového okna. Následující postup s menšími změnami, budou fungovat v forms také.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-use-a-common-control-in-a-dialog-box"></a>Použití běžného ovládacího prvku v dialogovém okně  
  
1.  Umístěte ovládací prvek v dialogovém okně šablony [pomocí editoru dialogových oken](../mfc/using-the-dialog-editor-to-add-controls.md).  
  
2.  Přidejte do třídy dialogového okna členské proměnné, která představuje ovládací prvek. V **přidání členské proměnné** dialogové okno, zkontrolujte **řídicí proměnná** a ujistěte se, že **řízení** je vybraná **kategorie**.  
  
3.  Pokud tato běžného ovládacího prvku poskytuje vstup k programu, deklarovat další člen variable(s) ve třídě dialog pro zpracování ty vstupní hodnoty.  
  
    > [!NOTE]
    >  Můžete přidat tyto členské proměnné pomocí místní nabídky v zobrazení tříd (viz [přidání člena proměnné](../ide/adding-a-member-variable-visual-cpp.md)).  
  
4.  V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) pro vlastní třídy dialogového okna nastavit počáteční podmínky pro běžné ovládací prvek. Členské funkce pomocí členské proměnné, vytvořené v předchozím kroku, slouží k nastavení výchozí hodnoty a další nastavení. O nastavení naleznete v následujících popisech ovládacích prvků podrobnosti.  
  
     Můžete také použít [výměna dialogových dat](../mfc/dialog-data-exchange-and-validation.md) (DDX) k chybě při inicializaci ovládacích prvků v dialogovém okně.  
  
5.  V obslužné rutiny pro ovládací prvky v dialogovém okně použijte k manipulaci s ovládacího prvku členské proměnné. O metody naleznete v následujících popisech ovládacích prvků podrobnosti.  
  
    > [!NOTE]
    >  Členské proměnné, budou existovat jenom, dokud existuje dialogu sám sebe. Nebudete moci po zavření dialogu dotazu pro vstupní hodnoty ovládacího prvku. Chcete-li pracovat s vstupní hodnoty z běžného ovládacího prvku, přepište `OnOK` ve vlastní třídy dialogového okna. V přepsání dotaz pro vstupní hodnoty ovládacího prvku a uložit tyto hodnoty v členské proměnné třídy dialogového okna.  
  
    > [!NOTE]
    >  Výměna dialogových dat můžete také nastavit nebo načíst hodnoty z ovládacích prvků v dialogovém okně.  
  
## <a name="remarks"></a>Poznámky  
 Přidání některých běžných ovládacích prvků do dialogového okna způsobí, že dialogové okno přestane fungovat. Odkazovat na [přidání ovládacích prvků do dialogového okna způsobí, že dialogové okno již funkce](../windows/adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function.md) Další informace o zpracování této situaci.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat  
  
-   [Přidání ovládacích prvků do dialogového okna ručně místo pomocí editoru dialogových oken](../mfc/adding-controls-by-hand.md)  
  
-   [Odvodit Moje ovládacího prvku z jedné ze standardní běžné ovládací prvky Windows](../mfc/deriving-controls-from-a-standard-control.md)  
  
-   [Použití běžného ovládacího prvku jako podřízeného okna](../mfc/using-a-common-control-as-a-child-window.md)  
  
-   [Příjem oznámení z ovládacího prvku](../mfc/receiving-notification-from-common-controls.md)  
  
-   [Použít výměna dialogových dat (DDX)](../mfc/dialog-data-exchange-and-validation.md)  
  
## <a name="see-also"></a>Viz také  
 [Příprava a použití ovládacích prvků](../mfc/making-and-using-controls.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

