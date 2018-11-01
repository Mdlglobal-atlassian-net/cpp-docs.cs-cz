---
title: 'Postupy: Vytvoření mapy zpráv pro třídu šablony'
ms.date: 11/04/2016
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
ms.openlocfilehash: 437fdf59ae9c9d3428654fc412fd78bf1348a701
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586235"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>Postupy: Vytvoření mapy zpráv pro třídu šablony

Mapování zpráv v prostředí MFC poskytuje efektivní způsob, jak směrování zpráv Windows k příslušné instanci objektu C++. Příklady cílů mapy zpráv knihovny MFC: třídy aplikace, dokument a zobrazení tříd, třídy ovládacích prvků a tak dále.

Tradiční mapy zpráv knihovny MFC jsou deklarovány pomocí [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) – makro, chcete-li deklarovat počáteční mapu zpráv – makro položky pro každou metodu třídy obslužná rutina zprávy a nakonec [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)– makro pro deklaraci na konec mapování zprávy.

Jediným omezením s [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) – makro nastane, pokud se používá ve spojení s třídou obsahující argumenty šablony. Při použití s třída šablony, toto makro způsobí chybu kompilace z důvodu chybějící parametry šablony při rozšíření makra. [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map) – makro byla navržena k umožnění mapuje třídy obsahující o jeden argument deklarovat své vlastní zprávu.

## <a name="example"></a>Příklad

Vezměte v úvahu příklad kde MFC [clistbox –](../mfc/reference/clistbox-class.md) třídy je rozšířené kvůli synchronizaci s externí zdroj dat. Fiktivní `CSyncListBox` třída je deklarována následovně:

[!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]

`CSyncListBox` Třída je jeden typ, který popisuje zdroje dat se synchronizují se bez vizuálního vzhledu. Také deklaruje tři metody, které se bude účastnit v mapování zprávy třídy: `OnPaint`, `OnDestroy`, a `OnSynchronize`. `OnSynchronize` Metoda je implementován takto:

[!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]

Umožňuje provádění výše `CSyncListBox` třídy specificky určené na libovolný typ třídy, která implementuje `GetCount` metody, například `CArray`, `CList`, a `CMap`. `StringizeElement` Je funkce prototypem pomocí následující šablony funkce:

[!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]

Mapy zpráv pro tuto třídu za normálních okolností je definován jako:

```cpp
BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)
  ON_WM_PAINT()
  ON_WM_DESTROY()
  ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)
END_MESSAGE_MAP()
```

kde **LBN_SYNCHRONIZE** vlastní uživatelská zpráva definované aplikací, jako například:

[!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]

Výše uvedené mapování – makro nebude kompilovat, vzhledem k tomu, že specifikace šablony pro `CSyncListBox` třídy budou chybět během rozšíření makra. **BEGIN_TEMPLATE_MESSAGE_MAP** – makro tento problém řeší začleňte do mapy rozšířené – makro parametr určené šablony. Mapy zpráv pro tuto třídu bude:

[!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]

Následující znázorňuje ukázkové využití `CSyncListBox` pomocí `CStringList` objektu:

[!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]

K dokončení testu `StringizeElement` funkce musí být specializovaná pro práci s `CStringList` třídy:

[!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]

## <a name="see-also"></a>Viz také

[BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)<br/>
[Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)

