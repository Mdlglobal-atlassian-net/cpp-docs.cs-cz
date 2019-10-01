---
title: Modální a nemodální dialogová okna
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: 886229a2b66968bf76129ecb1da838bd36e66215
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685180"
---
# <a name="modal-and-modeless-dialog-boxes"></a>Modální a nemodální dialogová okna

Třídu [CDialog](../mfc/reference/cdialog-class.md) můžete použít ke správě dvou druhů dialogových oken:

- *Modální dialogová okna*, která vyžadují, aby uživatel reagoval před pokračováním programu

- *Nemodální dialogová okna*, která zůstávají na obrazovce a jsou dostupná pro použití kdykoli, ale umožňují jiné aktivity uživatelů

Úpravy prostředků a postupy pro vytvoření šablony dialogového okna jsou stejné pro modální a nemodální dialogová okna.

Vytvoření dialogového okna pro váš program vyžaduje následující kroky:

1. Pro návrh dialogového okna a vytvoření prostředku šablony dialogového okna použijte [Editor dialogových oken](../windows/dialog-editor.md) .

1. Vytvoří třídu dialogového okna.

1. Připojte [ovládací prvky prostředku dialogového okna k obslužným rutinám zpráv](../windows/adding-event-handlers-for-dialog-box-controls.md) ve třídě dialogového okna.

1. Přidejte datové členy přidružené k ovládacím prvkům dialogového okna a pro nastavení [výměny dat dialogových](../mfc/dialog-data-exchange.md) oken a [dialogových oken](../mfc/dialog-data-validation.md) pro ovládací prvky.

## <a name="see-also"></a>Další informace najdete v tématech

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)
