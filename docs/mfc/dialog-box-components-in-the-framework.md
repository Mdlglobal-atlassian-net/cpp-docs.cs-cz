---
title: Komponenty dialogového okna v rozhraní .NET Framework
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
ms.openlocfilehash: 15d01924be811a9c9ec8ea333870f444bf9aa61a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685836"
---
# <a name="dialog-box-components-in-the-framework"></a>Komponenty dialogového okna v rozhraní .NET Framework

V rozhraní knihovny MFC má dialogové okno dvě komponenty:

- Prostředek šablony dialogového okna, který určuje ovládací prvky dialogového okna a jejich umístění.

   Dialogové okno obsahuje šablonu dialogového okna, ze které systém Windows vytvoří dialogové okno a zobrazí jej. Šablona určuje charakteristiky dialogového okna, včetně jeho velikosti, umístění, stylu a typů a umístění ovládacích prvků dialogového okna. Obvykle budete používat šablonu dialogu uloženou jako prostředek, ale můžete také vytvořit vlastní šablonu v paměti.

- Třída dialogového okna odvozená od [CDialog](../mfc/reference/cdialog-class.md), která poskytuje programové rozhraní pro správu dialogového okna.

   Dialogové okno je okno, které se připojí k oknu Windows, pokud je viditelné. Když je dialogové okno vytvořeno, použije se jako šablona pro vytváření podřízených ovládacích prvků okna pro dialogové okno prostředek šablony dialogového okna.

## <a name="see-also"></a>Další informace najdete v tématech

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)
