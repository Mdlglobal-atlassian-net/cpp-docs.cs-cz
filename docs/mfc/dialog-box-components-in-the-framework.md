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
ms.openlocfilehash: 6936a48d1a3e1845d56c73524c84800d9d605155
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065503"
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

