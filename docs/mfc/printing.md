---
title: Tisk
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: e0cd2d6d85cb9820b23495a003068994b13f9c85
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278077"
---
# <a name="printing"></a>Tisk

Microsoft Windows implementuje zobrazení nezávislých na zařízení. V knihovně MFC, to znamená, že stejné volání vykreslování, v `OnDraw` členské funkce třídy zobrazení jsou zodpovědné za vykreslování na displeji a na jiných zařízeních, jako jsou tiskárny. Pro náhled tisku cílové zařízení je simulované tiskový výstup na obrazovce.

##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> Vaše Role v tisku a v rámci Role

Zobrazit třídu má následující zodpovědnosti:

- Informování rozhraní framework jsou počet stránek v dokumentu.

- Když se zobrazí výzva k vytištění zadanou stránku, nakreslete část dokumentu.

- Přidělit a uvolnit písem, nebo jiné grafické prostředky rozhraní GDI systému zařízení potřebné pro tisk.

- V případě potřeby odesílat žádný řídicí kódy potřeba změnit režim tiskárny před tiskem danou stránku, například, chcete-li změnit orientaci tisk na základě na stránku.

Odpovědnosti rozhraní framework jsou následující:

- Zobrazení **tisk** dialogové okno.

- Vytvoření [CDC](../mfc/reference/cdc-class.md) objektu tiskárny.

- Volání [zobrazující](../mfc/reference/cdc-class.md#startdoc) a [EndDoc](../mfc/reference/cdc-class.md#enddoc) členských funkcí třídy `CDC` objektu.

- Opakovaně volat [StartPage](../mfc/reference/cdc-class.md#startpage) členskou funkci `CDC` objektu, informujte třídu zobrazení na stránce, které by měl vytisknout a volat [EndPage](../mfc/reference/cdc-class.md#endpage) členskou funkci `CDC` objektu.

- Volání přepisovatelné funkce v zobrazení ve vhodných chvílích.

Následující články popisují, jak rozhraní framework podporuje tisku a tiskového náhledu:

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Jak probíhá výchozí tisk](../mfc/how-default-printing-is-done.md)

- [Vícestránkové dokumenty](../mfc/multipage-documents.md)

- [Záhlaví a zápatí](../mfc/headers-and-footers.md)

- [Přidělování prostředků GDI pro tisk](../mfc/allocating-gdi-resources.md)

- [Náhled tisku](../mfc/print-preview-architecture.md)

## <a name="see-also"></a>Viz také:

[Tisk a náhled tisku](../mfc/printing-and-print-preview.md)
