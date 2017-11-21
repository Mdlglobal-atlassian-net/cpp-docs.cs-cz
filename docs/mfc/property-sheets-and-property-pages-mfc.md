---
title: "Seznam vlastností a stránky vlastností (MFC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 409bb0fadf994e793323c5585098f12c7f5f6c32
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="property-sheets-and-property-pages-mfc"></a>Seznamy vlastností a stránky vlastností (MFC)
Knihovny MFC [dialogové okno](../mfc/dialog-boxes.md) na podívejte "kartě dialogové okno" může trvat začleněním vlastností a stránky vlastností. V prostředí MFC názvem "seznam vlastností", tento druh dialogové okno, podobně jako mnoho dialogová okna v aplikaci Microsoft Word, Excel a Visual C++, pravděpodobně obsahuje zásobník záložkách listy, podobně jako zásobníku složek souborů z přední zálohovat nebo skupiny systému windows, kaskádě pohledu. Ovládací prvky na kartě front jsou viditelné; pouze s popiskem karta je zobrazena na zadní karty. Seznam vlastností jsou obzvláště užitečná pro správu velkého počtu vlastnosti nebo nastavení, které spadají poměrně přehledně do několika skupin. Obvykle jeden seznam vlastností, můžete zjednodušit uživatelské rozhraní nahrazením několik samostatných dialogových oken.  
  
 Od verze knihovny MFC verze 4.0 seznam vlastností a stránky vlastností se implementují použití běžných ovládacích prvků, které jsou součástí verze systému Windows 95 a Windows NT 3.51 a novější.  
  
 Seznam vlastností, které jsou implementované s třídami [cpropertysheet –](../mfc/reference/cpropertysheet-class.md) a [CPropertyPage](../mfc/reference/cpropertypage-class.md) (popsané v *odkaz knihovny MFC*). `CPropertySheet`definuje celkové dialogových oken, která může obsahovat více "stránky" na základě `CPropertyPage`.  
  
 Informace o vytváření a práci s vlastností, naleznete v tématu [vlastností](../mfc/property-sheets-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [Dialogová okna](../mfc/dialog-boxes.md)   
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)   
 [Seznam vlastností a stránky vlastností v MFC](../mfc/property-sheets-and-property-pages-in-mfc.md)   
 [Výměna dat](../mfc/exchanging-data.md)   
 [Vytvoření nemodálního seznamu vlastností](../mfc/creating-a-modeless-property-sheet.md)   
 [Ošetření tlačítka použít](../mfc/handling-the-apply-button.md)

