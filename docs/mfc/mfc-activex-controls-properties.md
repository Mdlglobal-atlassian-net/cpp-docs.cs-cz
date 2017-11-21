---
title: "Ovládací prvky MFC ActiveX: Vlastnosti | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 26947b0c2c779f65fb01dd78d56ffe19afaf27ce
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-activex-controls-properties"></a>MFC – ovládací prvky ActiveX: Vlastnosti
Ovládací prvek ActiveX aktivuje události ke komunikaci s jeho kontejneru ovládacího prvku. Kontejner, používá ke komunikaci s ovládacím prvkem, metod a vlastností. Metody a vlastnosti jsou podobné se používají a účel, v uvedeném pořadí, členské funkce a proměnné členů třídy C++. Datové členy ovládacího prvku ActiveX, které jsou umístěny do kontejneru, jsou vlastnosti. Vlastnosti poskytují rozhraní pro aplikace, které obsahují ovládací prvky ActiveX, například klienti automatizace a ActiveX – kontejnery ovládacích prvků.  
  
 Vlastnosti se také označují jako atributy.  
  
 Další informace o metodách ovládací prvek ActiveX, najdete v článku [MFC – ovládací prvky ActiveX: metody](../mfc/mfc-activex-controls-methods.md).  
  
 ActiveX – ovládací prvky můžete implementovat stock a vlastních metod a vlastností. Třída `COleControl` poskytuje implementaci pro uložených vlastností. (Úplný seznam uložených vlastností, najdete v článku [MFC – ovládací prvky ActiveX: Přidání vlastnosti Stock](../mfc/mfc-activex-controls-adding-stock-properties.md).) Vlastní vlastnosti, definované vývojář, přidejte specializované funkce do ovládacího prvku ActiveX. Další informace najdete v tématu [MFC – ovládací prvky ActiveX: Přidání vlastních vlastností](../mfc/mfc-activex-controls-adding-custom-properties.md).  
  
 Mechanismus, který se skládá z odesílání mapu, která zpracovává vlastnosti a metody existující členské funkce podporuje uložených a vlastní vlastnosti, jako jsou metody, `COleControl` třídy. Kromě toho tyto vlastnosti můžete mít parametry, které vývojář používá k předání doplňující informace do ovládacího prvku.  
  
 Následující články popisují vlastnosti ovládacích prvků ActiveX podrobněji:  
  
-   [Ovládací prvky MFC ActiveX: Přidání uložených vlastností](../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [Ovládací prvky MFC ActiveX: Přidání přizpůsobených vlastností](../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [Ovládací prvky MFC ActiveX: Implementace rozšířených vlastností](../mfc/mfc-activex-controls-advanced-property-implementation.md)  
  
-   [Ovládací prvky MFC ActiveX: Přístup k vedlejším vlastnostem](../mfc/mfc-activex-controls-accessing-ambient-properties.md)  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)

