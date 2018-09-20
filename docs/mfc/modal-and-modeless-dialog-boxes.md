---
title: Modální a nemodální dialogová okna | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e355c3bcef9edb68e49903dafbf4719fe0aa925
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417524"
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

