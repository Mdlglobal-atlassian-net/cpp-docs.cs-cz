---
title: Komponenty dialogového okna v rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fb72e2961eec53b2dea8e37cfc39ccbcc0c5f27
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397166"
---
# <a name="dialog-box-components-in-the-framework"></a>Komponenty dialogového okna v rozhraní .NET Framework

V rámci MFC dialogového okna má dvě součásti:

- Prostředek šablony dialogového okna, která určuje ovládací prvky dialogových oken a jejich umístění.

     Dialogové okno prostředků ukládá šablony dialogového okna, ve kterém Windows vytvoří dialogové okno a zobrazí ji. Šablona specifikuje v dialogovém okně Vlastnosti, včetně jeho velikost, umístění, styl a typy a umístění ovládacích prvků v dialogovém okně. Obvykle použijete šablony dialogového okna uložené jako prostředek, ale můžete také vytvořit vlastní šablonu v paměti.

- Dialogové okno třída odvozená z [CDialog](../mfc/reference/cdialog-class.md), a poskytuje tak programové rozhraní pro správu dialogových oken.

     Dialogové okno je okno a připojí do okna Windows, když je viditelné. Při vytvoření dialogového okna, prostředku šablony dialogového okna slouží jako šablony pro vytváření podřízených ovládacích prvků okno pro dialogové okno.

## <a name="see-also"></a>Viz také

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

