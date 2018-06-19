---
title: Kontejnery ovládacích prvků ActiveX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73496f892cc55ef59b2d84228ae9ae0416d3e8a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338972"
---
# <a name="activex-control-containers"></a>ActiveX – kontejnery ovládacích prvků
Kontejneru ovládacího prvku ActiveX je kontejner, který plně podporuje ovládací prvky ActiveX a můžete začlenit do svých vlastních windows dialogová okna. Ovládacího prvku ActiveX je element opakovaně použitelné software, který můžete použít v mnoha projekty vývoje. Ovládací prvky umožňují uživatelům vaší aplikace přístup k databázím, monitorovat data a různé možnosti v rámci vaší aplikace. Další informace o ovládací prvky ActiveX, najdete v článku [ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md).  
  
 Kontejnery ovládacích prvků obvykle mít dvě formy v projektu:  
  
-   Dialogová okna a jako dialogové okno windows například zobrazení formulářů, kde se ovládací prvek ActiveX používá někde v dialogovém okně.  
  
-   Windows v aplikaci, kde se používá ovládacího prvku ActiveX v panelu nástrojů nebo jiného umístění v okně uživatele.  
  
 ActiveX kontejneru ovládacího prvku komunikuje s ovládacím prvkem prostřednictvím zveřejněné [metody](../mfc/mfc-activex-controls-methods.md) a [vlastnosti](../mfc/mfc-activex-controls-properties.md). Tyto metody a vlastnosti, které lze získat přístup a měnit kontejneru ovládacích prvků, ke kterým se přistupuje prostřednictvím obálkovou třídu do projektu kontejneru ovládacího prvku ActiveX. Vloženému ovládacímu prvku ActiveX lze také interagovat s kontejnerem ohlásí (odesílajícím) [události](../mfc/mfc-activex-controls-events.md) oznámit kontejner, který akce došlo k chybě. Kontejneru ovládacích prvků můžete k provedení akce tato oznámení, nebo ne.  
  
 Další články popisují několik témat ve vytváření projektu kontejneru ovládacího prvku ActiveX na základní implementace problémy související s kontejnery ovládacích prvků ActiveX vytvořené s nástroji Visual C++:  
  
-   [Vytvoření kontejneru ovládacího prvku ActiveX prostředí MFC](../mfc/reference/creating-an-mfc-activex-control-container.md)  
  
-   [Kontejnery pro ovládací prvky ActiveX](../mfc/containers-for-activex-controls.md)  
  
-   [ActiveX – kontejnery ovládacích prvků: Ruční povolení uzavření ovládacího prvku ActiveX](../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)  
  
-   [ActiveX – kontejnery ovládacích prvků: Vložení ovládacího prvku do kontejnerové aplikace ovládacího prvku](../mfc/inserting-a-control-into-a-control-container-application.md)  
  
-   [Kontejnery ovládacích prvků ActiveX: Připojení ovládacího prvku ActiveX k členské proměnné](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)  
  
-   [– Kontejnery ovládacích prvků ActiveX: Řídí zpracování událostí z prvku ActiveX](../mfc/activex-control-containers-handling-events-from-an-activex-control.md)  
  
-   [ActiveX – kontejnery ovládacích prvků: Zobrazení a úpravy vlastností ovládacích prvků](../mfc/activex-control-containers-viewing-and-modifying-control-properties.md)  
  
-   [ActiveX – kontejnery ovládacích prvků: Programování ovládacích prvků ActiveX v kontejneru ovládacího prvku ActiveX](../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
-   [ActiveX – kontejnery ovládacích prvků: Použití ovládacích prvků v jiném kontejneru než dialogovém okně](../mfc/activex-control-containers-using-controls-in-a-non-dialog-container.md)  
  
 Další informace o použití ovládacích prvků ActiveX v dialogovém okně najdete v tématu [editoru dialogového okna](../windows/dialog-editor.md) témata.  
  
 Seznam článků, které vysvětlují, podrobnosti o vývoji ovládacích prvků ActiveX pomocí Visual C++ a třídy ovládacích prvků MFC ActiveX najdete v tématu [ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md). Články jsou seskupené podle funkčních kategorií.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

