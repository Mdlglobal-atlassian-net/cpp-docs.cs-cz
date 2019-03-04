---
title: Výměna dat
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
ms.openlocfilehash: de82a337f19b7b2ac6039fd3f3c16ab67aa1dc99
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265922"
---
# <a name="exchanging-data"></a>Výměna dat

Stejně jako u většiny dialogová okna, výměna dat mezi vlastností a aplikací je jednou z vašich nejdůležitějších funkcí vlastností. Tento článek popisuje, jak tento úkol provést.

Výměna dat s vlastností je ve skutečnosti otázkou výměna dat se na stránkách vlastností jednotlivých vlastností. Postup pro výměnu dat pomocí stránky vlastností je stejná jako výměna dat se dialogové okno, protože [CPropertyPage](../mfc/reference/cpropertypage-class.md) objekt je jenom specializované [CDialog](../mfc/reference/cdialog-class.md) objektu. Postup využívá v rámci dialogového okna data exchange (DDX) zařízení, který vyměňuje data mezi ovládacími prvky v objektu pole dialogové okno dialogové okno pole a členské proměnné.

Důležitý rozdíl mezi výměna dat s vlastností a s normální dialogového okna je, že seznam vlastností obsahuje více stránek, proto musí vyměňovat data s všechny stránky v seznamu vlastností. Další informace o DDX najdete v tématu [výměna dat dialogových oken a ověření](../mfc/dialog-data-exchange-and-validation.md).

Následující příklad ukazuje výměnou dat mezi zobrazením a dvě stránky vlastností:

[!code-cpp[NVC_MFCDocView#4](../mfc/codesnippet/cpp/exchanging-data_1.cpp)]

## <a name="see-also"></a>Viz také:

[Seznamy vlastností](../mfc/property-sheets-mfc.md)
