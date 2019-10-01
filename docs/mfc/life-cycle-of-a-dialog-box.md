---
title: Práce s dialogovými okny v MFC
ms.date: 09/27/2019
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
ms.openlocfilehash: ad15250cf9a8dd663072cf9423263260bbb40a0e
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685724"
---
# <a name="working-with-dialog-boxes-in-mfc"></a>Práce s dialogovými okny v MFC

Během životního cyklu dialogového okna uživatel vyvolá dialogové okno, obvykle v rámci obslužné rutiny příkazu, která vytvoří a inicializuje objekt dialogového okna, uživatel pracuje s dialogovým oknem a pak se dialogové okno zavře.

U modálních dialogových oken vaše obslužná rutina shromáždí všechna data, která uživatel zadal po zavření dialogového okna. Vzhledem k tomu, že objekt dialogového okna existuje po zavření jeho dialogového okna, můžete jednoduše použít členské proměnné vaší třídy dialogu k extrakci dat.

Pro nemodální dialogová okna můžete často extrahovat data z objektu dialogového okna, když je dialogové okno stále vidět. V určitém okamžiku je objekt dialogového okna zničen; v takovém případě závisí na vašem kódu.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Vytváření a zobrazování dialogových oken](../mfc/creating-and-displaying-dialog-boxes.md)

- [Vytváření modálních dialogových oken](../mfc/creating-modal-dialog-boxes.md)

- [Vytváření nemodálních dialogových oken](../mfc/creating-modeless-dialog-boxes.md)

- [Použití šablony dialogového okna v paměti](../mfc/using-a-dialog-template-in-memory.md)

- [Nastavení barvy pozadí dialogového okna](../mfc/setting-the-dialog-boxs-background-color.md)

- [Inicializace dialogového okna](../mfc/initializing-the-dialog-box.md)

- [Zpracování zpráv systému Windows ve vašem dialogovém okně](../mfc/handling-windows-messages-in-your-dialog-box.md)

- [Načítání dat z objektu dialogového okna](../mfc/retrieving-data-from-the-dialog-object.md)

- [Zavření dialogového okna](../mfc/closing-the-dialog-box.md)

- [Zničení dialogového okna](../mfc/destroying-the-dialog-box.md)

- [Výměna dat dialogových oken (DDX) a ověřování (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Dialogová okna seznamu vlastností](../mfc/property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>Další informace najdete v tématech

[Dialogová okna](../mfc/dialog-boxes.md)
