---
title: 'Ovládací prvky MFC ActiveX: Vlastnosti | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac9d9e4f5e7d777bd147ce36e970e7a30fd875b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-properties"></a>MFC – ovládací prvky ActiveX: Vlastnosti
Ovládací prvek ActiveX aktivuje události ke komunikaci s jeho kontejneru ovládacího prvku. Kontejner, používá ke komunikaci s ovládacím prvkem, metod a vlastností. Metody a vlastnosti jsou podobné se používají a účel, v uvedeném pořadí, členské funkce a proměnné členů třídy C++. Datové členy ovládacího prvku ActiveX, které jsou umístěny do kontejneru, jsou vlastnosti. Vlastnosti poskytují rozhraní pro aplikace, které obsahují ovládací prvky ActiveX, například klienti automatizace a ActiveX – kontejnery ovládacích prvků.  
  
 Vlastnosti se také označují jako atributy.  
  
 Další informace o metodách ovládací prvek ActiveX, najdete v článku [MFC – ovládací prvky ActiveX: metody](../mfc/mfc-activex-controls-methods.md).  
  
 ActiveX – ovládací prvky můžete implementovat stock a vlastních metod a vlastností. Třída `COleControl` poskytuje implementaci pro uložených vlastností. (Úplný seznam uložených vlastností, najdete v článku [MFC – ovládací prvky ActiveX: Přidání vlastnosti Stock](../mfc/mfc-activex-controls-adding-stock-properties.md).) Vlastní vlastnosti, definované vývojář, přidejte specializované funkce do ovládacího prvku ActiveX. Další informace najdete v tématu [MFC – ovládací prvky ActiveX: Přidání vlastních vlastností](../mfc/mfc-activex-controls-adding-custom-properties.md).  
  
 Mechanismus, který se skládá z odesílání mapu, která zpracovává vlastnosti a metody existující členské funkce podporuje uložených a vlastní vlastnosti, jako jsou metody, `COleControl` třídy. Kromě toho tyto vlastnosti můžete mít parametry, které vývojář používá k předání doplňující informace do ovládacího prvku.  
  
 Následující články popisují vlastnosti ovládacích prvků ActiveX podrobněji:  
  
-   [MFC – ovládací prvky ActiveX: Přidání uložených vlastností](../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [MFC – ovládací prvky ActiveX: Přidání přizpůsobených vlastností](../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [MFC – ovládací prvky ActiveX: Implementace rozšířených vlastností](../mfc/mfc-activex-controls-advanced-property-implementation.md)  
  
-   [MFC – ovládací prvky ActiveX: Přístup k vedlejším vlastnostem](../mfc/mfc-activex-controls-accessing-ambient-properties.md)  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

