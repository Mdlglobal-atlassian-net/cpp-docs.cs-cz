---
title: "Pružné čáry a snímače | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- trackers [MFC]
- CRectTracker class [MFC], implementing trackers
- OLE objects [MFC], selecting
- rubber banding [MFC]
- WM_LBUTTONDOWN [MFC]
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3bd9da00d2d6ea0110562f523a0adc53c1a476c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="rubber-banding-and-trackers"></a>Pružné čáry a snímače
Další funkcí, které jsou součástí snímačů je výběr "pružné vzdálené správy", který umožňuje uživateli vybrat více položek OLE přetažením obdélníku velikosti kolem položky, které chcete vybrat. Když uživatel uvolní levé tlačítko myši, jsou vybrané položky v rámci oblasti vybraný uživatelem a práce s uživatelem. Uživatel může například přetáhněte výběr do jiné aplikace kontejneru.  
  
 Implementace tato funkce vyžaduje některé další kód ve vaší aplikaci `WM_LBUTTONDOWN` funkce obslužné rutiny.  
  
 Následující ukázka kódu implementuje pružné vzdálené výběr a další funkce.  
  
 [!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]  
  
 Pokud chcete povolit reverzibilního orientaci ke sledovacímu modulu během pružné čáry, by měly volat [CRectTracker::TrackRubberBand](../mfc/reference/crecttracker-class.md#trackrubberband) se třetím zadaným parametrem nastavena na **TRUE**. Mějte na paměti, že povolení reverzibilního orientaci někdy způsobí [CRectTracker::m_rect](../mfc/reference/crecttracker-class.md#m_rect) k stát obrácený. Tento problém lze vyřešit voláním [CRect::NormalizeRect](../atl-mfc-shared/reference/crect-class.md#normalizerect).  
  
 Další informace najdete v tématu [klientské položky kontejneru](../mfc/containers-client-items.md) a [přizpůsobení přetažení](../mfc/drag-and-drop-customizing.md).  
  
## <a name="see-also"></a>Viz také  
 [Snímače: Implementace snímačů ve vašich aplikacích OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)   
 [CRectTracker – třída](../mfc/reference/crecttracker-class.md)
