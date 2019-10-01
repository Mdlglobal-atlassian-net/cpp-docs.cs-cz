---
title: Vytvoření prostředku dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- dialog resources
- MFC dialog boxes [MFC], creating
- dialog templates [MFC], creating dialog resource
- templates [MFC], creating
- resources [MFC], creating dialog boxes
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 0b83bd33-14d3-4611-8129-fccdae18053e
ms.openlocfilehash: 7b1e6c81a0f4bd6983c2a76baf6148941a4fa21d
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685631"
---
# <a name="creating-the-dialog-resource"></a>Vytvoření prostředku dialogového okna

Chcete-li navrhnout [dialogové okno](../mfc/dialog-boxes.md) a vytvořit prostředek dialogu, použijte [Editor dialogových oken](../windows/dialog-editor.md). V editoru dialogového okna můžete:

- Upravte velikost a umístění, ve kterém bude dialogové okno vypadat.

- Přetáhněte různé druhy ovládacích prvků z palety ovládacích prvků a přetáhněte je tam, kde je chcete mít v dialogovém okně.

- Umístěte ovládací prvky s tlačítky zarovnání na panelu nástrojů.

- Otestujte dialogové okno simulací vzhledu a chování, které bude mít v programu. V testovacím režimu můžete manipulovat s ovládacími prvky dialogového okna zadáním textu do textových polí, kliknutím na pushbuttons a tak dále.

Po dokončení se prostředek šablony dialogu uloží do souboru skriptu prostředků vaší aplikace. V případě potřeby ho můžete upravit později. Úplný popis vytváření a úprav prostředků dialogového okna najdete v tématech v [editoru dialogových oken](../windows/dialog-editor.md) . Tato technika se používá také k vytvoření prostředků šablony dialogového okna pro třídy [CFormView](../mfc/reference/cformview-class.md) a [CRecordView](../mfc/reference/crecordview-class.md) .

Když vzhled dialogového okna vyhovuje vám, vytvořte třídu dialogového okna a namapujte její zprávy, jak je popsáno v tématu [Vytvoření třídy dialogového okna pomocí průvodců kódem](../mfc/creating-a-dialog-class-with-code-wizards.md).

## <a name="see-also"></a>Další informace najdete v tématech

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)
