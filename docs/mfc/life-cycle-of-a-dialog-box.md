---
title: Životní cyklus dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
ms.openlocfilehash: a3772a180e35a57c997446fcf2268d84bec2daa5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291103"
---
# <a name="life-cycle-of-a-dialog-box"></a>Životní cyklus dialogového okna

Během životního cyklu dialogového okna uživatel vyvolá dialogové okno, obvykle uvnitř obslužná rutina příkazu, který vytvoří a inicializuje objektu dialogového okna, kterou uživatel komunikuje dialogových oken a dialog se zavře.

Vaše obslužná rutina pro modální dialogová okna, shromažďuje všechna data uživatele zadali po zavření dialogového okna. Protože objektu dialogového okna existuje po jeho dialogového okna uzavřel, jednoduše můžete členské proměnné třídy dialogového okna extrahovat data.

Pro nemodální dialogová okna může často extrahovat data z objektu dialogového okna, dialogové okno je stále zobrazená. V určitém okamžiku jeho zničení objektu dialogového okna; Pokud k tomu dojde, závisí na kódu.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Vytváření a zobrazování dialogových oken](../mfc/creating-and-displaying-dialog-boxes.md)

- [Vytváření modálních dialogových oken](../mfc/creating-modal-dialog-boxes.md)

- [Vytváření nemodálních dialogových oken](../mfc/creating-modeless-dialog-boxes.md)

- [Použití šablony dialogového okna v paměti](../mfc/using-a-dialog-template-in-memory.md)

- [Nastavení barvy pozadí v dialogovém okně](../mfc/setting-the-dialog-boxs-background-color.md)

- [Inicializace dialogových oken](../mfc/initializing-the-dialog-box.md)

- [Zpracování zpráv Windows ve vašem dialogovém okně](../mfc/handling-windows-messages-in-your-dialog-box.md)

- [Načítání dat z objektu dialogového okna](../mfc/retrieving-data-from-the-dialog-object.md)

- [Zavření dialogového okna](../mfc/closing-the-dialog-box.md)

- [Zničení dialogových oken](../mfc/destroying-the-dialog-box.md)

- [Výměna dat dialogových oken (DDX) a ověřování (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Dialogová okna Vlastnosti list](../mfc/property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>Viz také:

[Dialogová okna](../mfc/dialog-boxes.md)
