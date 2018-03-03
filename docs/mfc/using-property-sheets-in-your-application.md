---
title: "Použití seznamů vlastností v aplikaci | Microsoft Docs"
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
- dialog templates [MFC], property sheets
- dialog resources
- property pages [MFC], property sheets
- DoModal method property sheets
- AddPage method [MFC]
- property sheets, about property sheets
- Create method [MFC], property sheets
- CPropertyPage class [MFC], styles
ms.assetid: 240654d4-152b-4e3f-af7b-44234339206e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4247a40fa364774674c1c79845625df51ecd34ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-property-sheets-in-your-application"></a>Použití seznamů vlastností v aplikaci
V aplikaci použít seznam vlastností, proveďte následující kroky:  
  
1.  Vytvoření prostředku šablony dialogové okno pro každou stránku vlastností. Mějte na paměti, která je může být přepínání uživatelů z jedné stránky na jiný, tak uspořádání na každé stránce jako konzistentně možné.  
  
     Šablony dialogu pro všechny stránky, není nutné mít stejnou velikost. Rozhraní používá velikost největší stránky k zjistit, kolik místa k přidělení v seznamu vlastností pro stránky vlastností.  
  
     Při vytváření prostředku šablony dialogového okna pro danou stránku vlastností, je nutné zadat následující styly v dialogovém okně vlastností vlastnost:  
  
    -   Nastavte **popisek** textového pole na **Obecné** stránky na text, který chcete zobrazit na kartě pro tuto stránku.  
  
    -   Nastavte **styl** pole se seznamem na **styly** stránky k **podřízené**.  
  
    -   Nastavte **ohraničení** pole se seznamem na **styly** stránky k **tenký**.  
  
    -   Ujistěte se, že **Titlebar** políčko **styly** je vybrány.  
  
    -   Ujistěte se, že **zakázané** políčko **další styly** je vybrány.  
  
2.  Vytvoření [CPropertyPage](../mfc/reference/cpropertypage-class.md)-odvozené třídy odpovídající každé šablony dialogového okna Vlastnosti stránky. V tématu [přidání třídy](../ide/adding-a-class-visual-cpp.md). Zvolte `CPropertyPage` jako základní třídy.  
  
3.  Vytvoření proměnné, do kterých hodnoty pro tuto stránku vlastností člena. Proces pro přidání členské proměnné na stránku vlastností je přesně stejný jako přidání členské proměnné do dialogového okna, protože je specializované dialogové okno stránky vlastností. Další informace najdete v tématu [definování členských proměnných pro ovládací prvky dialogového okna](../windows/defining-member-variables-for-dialog-controls.md).  
  
4.  Vytvořit [cpropertysheet –](../mfc/reference/cpropertysheet-class.md) objekt ve zdrojovém kódu. Obvykle vytvoříte `CPropertySheet` objekt v obslužná rutina pro příkaz, který zobrazí stránku vlastností. Tento objekt představuje celou vlastností. Pokud vytvoříte modální vlastností s [DoModal](../mfc/reference/cpropertysheet-class.md#domodal) funkce, rozhraní framework poskytuje tři příkazová tlačítka ve výchozím nastavení: OK, zrušit a použít. Rozhraní framework vytvoří žádné příkazová tlačítka pro nemodální vlastností vytvořené pomocí [vytvořit](../mfc/reference/cpropertysheet-class.md#create) funkce. Není potřeba odvození třídy z `CPropertySheet` Pokud chcete přidat další ovládací prvky (například okno náhledu) nebo zobrazit nemodálního seznamu vlastností. Tento krok je nezbytný pro nemodální vlastností, protože neobsahují žádné výchozí ovládací prvky, které by mohly být použity zavřete okno vlastností.  
  
5.  Pro jednotlivé stránky, které mají být přidány do seznamu vlastností postupujte takto:  
  
    -   Vytvořit jeden objekt pro každou `CPropertyPage`-odvozené třídy, kterou jste vytvořili dříve v tomto procesu.  
  
    -   Volání [CPropertySheet::AddPage](../mfc/reference/cpropertysheet-class.md#addpage) pro jednotlivé stránky.  
  
     Obvykle objekt, který vytvoří `CPropertySheet` také vytvoří `CPropertyPage` objekty v tomto kroku. Ale pokud budete implementovat `CPropertySheet`-odvozené třídy, můžete vložit `CPropertyPage` objekty v `CPropertySheet` objekt a volání `AddPage` pro jednotlivé stránky z `CPropertySheet`-konstruktoru třídy odvozené. `AddPage`Přidá `CPropertyPage` objektu do seznamu vlastností seznam stránek, ale ve skutečnosti nevytvoří okna pro této stránce. Proto není nutné počkejte na vytvoření v okně Vlastnosti list volat `AddPage`; můžete volat `AddPage` ze seznamu vlastností konstruktor.  
  
     Ve výchozím nastavení Pokud má seznam vlastností další karty, než se vejde na jednom řádku seznamu vlastností, bude karty zásobníku v více řádků. Chcete-li zakázat překrývání, volejte [CPropertySheet::EnableStackedTabs](../mfc/reference/cpropertysheet-class.md#enablestackedtabs) s parametrem nastavena na **FALSE**. Je třeba volat `EnableStackedTabs` při vytváření seznamu vlastností.  
  
6.  Volání [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal) nebo [vytvořit](../mfc/reference/cpropertysheet-class.md#create) zobrazíte seznam vlastností. Volání `DoModal` k vytvoření seznamu vlastností jako modální dialogové okno. Volání **vytvořit** k vytvoření seznamu vlastností, jako pole dialogového okna bez režimu.  
  
7.  Výměna dat mezi stránky vlastností a vlastník seznamu vlastností. To je vysvětleno v článku [výměna dat](../mfc/exchanging-data.md).  
  
 Příklad použití vlastností, naleznete v části Obecné MFC ukázka [PROPDLG](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Seznam vlastností](../mfc/property-sheets-mfc.md)

