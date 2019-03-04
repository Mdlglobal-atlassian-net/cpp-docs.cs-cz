---
title: Pružné čáry a snímače
ms.date: 11/04/2016
helpviewer_keywords:
- trackers [MFC]
- CRectTracker class [MFC], implementing trackers
- OLE objects [MFC], selecting
- rubber banding [MFC]
- WM_LBUTTONDOWN [MFC]
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
ms.openlocfilehash: a6a9c9848e21129d4e6a8ce300e8750b4a0c6126
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281041"
---
# <a name="rubber-banding-and-trackers"></a>Pružné čáry a snímače

Další funkcí, které jsou součástí snímače je výběr "pružných", který umožňuje uživateli vybrat více položek OLE přetažením velikosti obdélník kolem položky, které chcete vybrat. Když uživatel uvolní levé tlačítko myši, jsou vybrané položky v rámci oblasti vybraných uživatelem. a lze ovládat uživatel. Uživatel například může přetáhnout výběr do jiného kontejneru aplikace.

Implementace tato funkce vyžaduje další kód ve funkci obslužné rutiny WM_LBUTTONDOWN vaší aplikace.

Následující vzorový kód implementuje výběr metodou pružných – a další funkce.

[!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]

Pokud chcete povolit reverzibilního orientace sledovacímu modulu za během pružné čáry, měli byste zavolat [CRectTracker::TrackRubberBand](../mfc/reference/crecttracker-class.md#trackrubberband) se třetím zadaným parametrem nastavena na **TRUE**. Mějte na paměti, že umožňuje reverzibilního orientace občas způsobí [CRectTracker::m_rect](../mfc/reference/crecttracker-class.md#m_rect) pro stát obrácený. Tento problém lze vyřešit voláním [CRect::NormalizeRect](../atl-mfc-shared/reference/crect-class.md#normalizerect).

Další informace najdete v tématu [klientské položky kontejneru](../mfc/containers-client-items.md) a [přizpůsobení přetažení](../mfc/drag-and-drop-customizing.md).

## <a name="see-also"></a>Viz také:

[Snímače: Implementace snímačů ve vašich aplikacích OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)<br/>
[CRectTracker – třída](../mfc/reference/crecttracker-class.md)
