---
title: Modální a nemodální dialogová okna
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: 7e1dc9c40f60dc46117ee0673a038d5a63df7680
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528359"
---
# <a name="modal-and-modeless-dialog-boxes"></a>Modální a nemodální dialogová okna

Můžete použít třídu [CDialog](../mfc/reference/cdialog-class.md) spravovat dva typy dialogová okna:

- *Modální dialogová okna*, což vyžaduje, aby uživatel reagovat před pokračováním program

- *Nemodální dialogová okna*, která zůstanou na obrazovce a jsou k dispozici pro použití v každém okamžiku ale povolit další aktivity uživatelů

Úpravy prostředků a postupech pro vytvoření šablony dialogového okna je stejný pro modální a nemodální dialogová okna.

Vytvoření dialogového okna pro váš program vyžaduje následující kroky:

1. Použití [editoru dialogového okna](../windows/dialog-editor.md) navrhovat dialogových oken a vytvoření jeho prostředku šablony dialogového okna.

1. Vytvoření třídy dialogového okna.

1. Připojení [prostředku dialogového okna ovládacích prvků pro obslužné rutiny zpráv](../windows/adding-event-handlers-for-dialog-box-controls.md) ve třídě dialog.

1. Přidejte datové členy související s ovládacími prvky v dialogovém okně a k určení [výměna dat dialogových oken](../mfc/dialog-data-exchange.md) a [ověřování dat dialogového okna](../mfc/dialog-data-validation.md) pro ovládací prvky.

## <a name="see-also"></a>Viz také

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

