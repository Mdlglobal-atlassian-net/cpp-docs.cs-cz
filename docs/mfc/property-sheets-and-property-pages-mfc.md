---
title: Seznamy vlastností a stránky vlastností (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
ms.openlocfilehash: 971b8cde1560e54f87269e8b85a41cdec55c091d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445393"
---
# <a name="property-sheets-and-property-pages-mfc"></a>Seznamy vlastností a stránky vlastností (MFC)

Knihovny MFC [dialogové okno](../mfc/dialog-boxes.md) můžete provést na pohled "kartě dialog" začleněním seznamy vlastností a stránky vlastností. Nazývá "seznam vlastností" v knihovně MFC, tento druh dialogové okno, podobně jako mnoho dialogových oken v aplikaci Microsoft Word, Excel a Visual C++ se zobrazí tak, aby obsahovala zásobníku seznamů s kartami, podobně jako zásobník složky souborů z zepředu dozadu nebo skupině kaskádových akcí systému windows. Ovládací prvky na kartě front-jsou viditelné. pouze kartě s popiskem je viditelný na zadní karty. Seznamy vlastností jsou zvláště užitečná pro správu velkého množství vlastností nebo nastavení, která poměrně elegantně lze rozdělit do několika skupin. Obvykle jeden seznam vlastností může zjednodušit uživatelského rozhraní tak, že nahradíte několik samostatných dialogových oknech.

Od verze knihovny MFC verze 4.0 seznamy vlastností a stránky vlastností jsou implementovány pomocí běžných ovládacích prvků, které jsou součástí Windows 95 a Windows NT verze 3.51 a vyšší.

Seznamy vlastností jsou implementovány s třídami [cpropertysheet –](../mfc/reference/cpropertysheet-class.md) a [CPropertyPage](../mfc/reference/cpropertypage-class.md) (podle *odkaz knihovny MFC*). `CPropertySheet` Definuje celkový dialogu, který může obsahovat více výraz "stránky" na základě `CPropertyPage`.

Informace o vytváření a práci se seznamy vlastností, naleznete v tématu [vlastností](../mfc/property-sheets-mfc.md).

## <a name="see-also"></a>Viz také

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Seznamy vlastností a stránky vlastností v prostředí MFC](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[Výměna dat](../mfc/exchanging-data.md)<br/>
[Vytvoření nemodálního seznamu vlastností](../mfc/creating-a-modeless-property-sheet.md)<br/>
[Ošetření tlačítka Použít](../mfc/handling-the-apply-button.md)

