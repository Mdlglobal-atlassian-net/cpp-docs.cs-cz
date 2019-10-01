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
ms.openlocfilehash: 5d4fd1c957b7f4d0d6ad10379a448309743aa11a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685084"
---
# <a name="property-sheets-and-property-pages-mfc"></a>Seznamy vlastností a stránky vlastností (MFC)

[Dialogové](../mfc/dialog-boxes.md) okno knihovny MFC může být pokaždé, když se zobrazí dialogové okno s přehledem o zahrnutí seznamů vlastností a stránek vlastností. Označuje se jako "seznam vlastností" v knihovně MFC. Tento druh dialogového okna, podobně jako mnoho dialogových oken v aplikaci Microsoft Word, Excel C++a Visual, vypadá jako zásobník karet s kartami, podobně jako zásobník složek souborů zobrazených vpřed nebo i skupina oken s kaskádami. Ovládací prvky na přední kartě jsou viditelné; na zadních kartách je zobrazená jenom karta s popiskem. Seznamy vlastností jsou zvláště užitečné pro správu velkého počtu vlastností nebo nastavení, která se poměrně rozpadají do několika skupin. Jeden seznam vlastností obvykle může zjednodušit uživatelské rozhraní nahrazením několika samostatných dialogových oken.

Od verze MFC 4,0 jsou seznamy vlastností a stránky vlastností implementovány pomocí běžných ovládacích prvků, které jsou dodávány se systémy Windows 95 a Windows NT verze 3,51 a novější.

Seznamy vlastností jsou implementovány pomocí tříd [CPropertySheet –](../mfc/reference/cpropertysheet-class.md) a [CPropertyPage –](../mfc/reference/cpropertypage-class.md) (popsaných v *referenčních informacích knihovny MFC*). `CPropertySheet` definuje celkové dialogové okno, které může obsahovat více "stránek" na základě `CPropertyPage`.

Informace o vytváření a práci se seznamy vlastností naleznete v tématu seznam [vlastností](../mfc/property-sheets-mfc.md)tématu.

## <a name="see-also"></a>Další informace najdete v tématech

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Seznamy vlastností a stránky vlastností v MFC](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[Výměna dat](../mfc/exchanging-data.md)<br/>
[Vytvoření nemodálního seznamu vlastností](../mfc/creating-a-modeless-property-sheet.md)<br/>
[Zpracování tlačítka použít](../mfc/handling-the-apply-button.md)
