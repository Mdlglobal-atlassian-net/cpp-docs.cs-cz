---
title: Tisk
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: a46096592c9983d04d2122bfabb56ece9346c4bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371196"
---
# <a name="printing"></a>Tisk

Systém Microsoft Windows implementuje zobrazení nezávislé na zařízení. V knihovně MFC to znamená, že `OnDraw` stejná volání výkresu v členské funkci třídy zobrazení jsou zodpovědná za kreslení na displeji a na jiných zařízeních, jako jsou tiskárny. Pro náhled tisku je cílové zařízení simulovaným výstupem tiskárny na displej.

## <a name="your-role-in-printing-vs-the-frameworks-role"></a><a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>Vaše role v tisku vs role rozhraní

Vaše třída zobrazení má následující povinnosti:

- Informujte rozhraní, kolik stránek je v dokumentu.

- Po zobrazení vyzvání k vytištění zadané stránky nakreslete tuto část dokumentu.

- Přidělte a nakondat všechna písma nebo jiné prostředky rozhraní grafického zařízení (GDI) potřebné pro tisk.

- V případě potřeby odešlete všechny únikové kódy potřebné ke změně režimu tiskárny před tiskem dané stránky, například pro změnu orientace tisku na základě stránky.

Odpovědnost rámce je následující:

- Zobrazení **tiskového** dialogového okna.

- Vytvořte objekt [CDC](../mfc/reference/cdc-class.md) pro tiskárnu.

- Volání [StartDoc](../mfc/reference/cdc-class.md#startdoc) a [EndDoc](../mfc/reference/cdc-class.md#enddoc) členské `CDC` funkce objektu.

- Opakovaně volat [StartPage](../mfc/reference/cdc-class.md#startpage) členské funkce `CDC` objektu, informovat třídu zobrazení, která stránka by měla být `CDC` vytištěna a volání [EndPage](../mfc/reference/cdc-class.md#endpage) členské funkce objektu.

- Volejte overridable funkce v zobrazení ve vhodnou dobu.

Následující články popisují, jak rámec podporuje tisk a náhled:

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Jak se provádí výchozí tisk](../mfc/how-default-printing-is-done.md)

- [Vícestránkové dokumenty](../mfc/multipage-documents.md)

- [Záhlaví a zápatí](../mfc/headers-and-footers.md)

- [Přidělování prostředků GDI pro tisk](../mfc/allocating-gdi-resources.md)

- [Náhledu](../mfc/print-preview-architecture.md)

## <a name="see-also"></a>Viz také

[Tisk a náhled tisku](../mfc/printing-and-print-preview.md)
