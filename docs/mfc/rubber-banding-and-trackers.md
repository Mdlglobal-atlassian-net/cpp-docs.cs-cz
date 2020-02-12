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
ms.openlocfilehash: 095f3c15546466c6a495f6aa348990ed69b04a9e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127363"
---
# <a name="rubber-banding-and-trackers"></a>Pružné čáry a snímače

Další funkcí poskytovanou pro stopy je výběr "pryž-Band", který umožňuje uživateli vybrat více položek OLE přetažením rámečku velikosti kolem položek, které mají být vybrány. Když uživatel uvolní levé tlačítko myši, vybere položky v oblasti vybrané uživatelem a může je měnit uživatel. Uživatel například může přetáhnout výběr do jiné aplikace kontejneru.

Implementace této funkce vyžaduje další kód ve funkci obslužné rutiny WM_LBUTTONDOWN vaší aplikace.

Následující ukázka kódu implementuje výběr z pružných pásem a další funkce.

[!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]

Pokud chcete, aby byl během pružných čar povolen vratný směr sledování, měli byste zavolat [CRectTracker –:: TrackRubberBand](../mfc/reference/crecttracker-class.md#trackrubberband) s třetím parametrem nastaveným na **hodnotu true**. Pamatujte, že povolení vratné orientace někdy způsobí, že [CRectTracker –:: m_rect](../mfc/reference/crecttracker-class.md#m_rect) přestanou být obrácené. To může být opraveno voláním [CRect:: NormalizeRect](../atl-mfc-shared/reference/crect-class.md#normalizerect).

Další informace najdete v tématu [položky klienta kontejneru](../mfc/containers-client-items.md) a [přetahování OLE: přizpůsobení přetahování myší](../mfc/drag-and-drop-ole.md#customize-drag-and-drop).

## <a name="see-also"></a>Viz také

[Snímače: Implementace snímačů ve vašich aplikacích OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)<br/>
[CRectTracker – třída](../mfc/reference/crecttracker-class.md)
