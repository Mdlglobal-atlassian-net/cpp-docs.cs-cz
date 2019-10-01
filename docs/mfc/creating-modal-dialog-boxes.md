---
title: Vytváření modálních dialogových oken
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: ed0fe3b7ef8aeddea01f573bfe8e1c01a6b5b443
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685674"
---
# <a name="creating-modal-dialog-boxes"></a>Vytváření modálních dialogových oken

Chcete-li vytvořit modální dialogové okno, zavolejte jeden ze dvou veřejných konstruktorů deklarovaných v [CDialog](../mfc/reference/cdialog-class.md). Dále zavolejte členskou funkci [DoModal](../mfc/reference/cdialog-class.md#domodal) objektu dialogového okna pro zobrazení dialogového okna a ke správě interakce s ním, dokud uživatel nezvolí OK nebo zrušit. Tato správa pomocí `DoModal` způsobuje, že dialogové okno je modální. V případě modálních dialogových oken `DoModal` načte prostředek dialogového okna.

## <a name="see-also"></a>Další informace najdete v tématech

[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)
