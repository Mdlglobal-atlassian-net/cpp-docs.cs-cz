---
title: Kontexty zařízení
ms.date: 11/04/2016
helpviewer_keywords:
- OnPrepareDC method [MFC]
- windows [MFC], and device context
- drawing [MFC], device context
- CClientDC class [MFC], and GetDC method [MFC]
- drawing [MFC], in mouse and device contexts
- CDC class [MFC], objects
- device contexts [MFC]
- client areas
- CMetaFileDC class [MFC], and OnPrepareDC method [MFC]
- GDI objects [MFC], device contexts
- graphic objects [MFC], device contexts
- frame windows [MFC], device contexts
- metafiles and device contexts
- EndPaint method [MFC]
- printers [MFC], device contexts
- mouse [MFC], drawing and device contexts
- BeginPaint method, CPaintDC
- CPaintDC class [MFC], device context for painting
- windows [MFC], drawing directly into
- client areas, and device context
- device contexts [MFC], CDC class [MFC]
- user interface [MFC], device contexts
- device-independent drawing
- GetDC method and CClientDC class [MFC]
- CClientDC class [MFC], and ReleaseDC method [MFC]
- ReleaseDC method [MFC]
- device contexts [MFC], about device contexts
- drawing [MFC], directly into windows
- painting and device context
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
ms.openlocfilehash: 7893b446c224dd84514ab63dc97cae467792750c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405973"
---
# <a name="device-contexts"></a>Kontexty zařízení

Kontext zařízení je datová struktura Windows obsahující informace o vykreslování atributy zařízení, jako je například tiskárnu nebo zobrazení. Všechna volání kreslení probíhají prostřednictvím objektů kontextu zařízení, který zapouzdřuje rozhraní Windows API pro kreslení čáry, tvary a text. Kontexty zařízení povolit kreslení nezávislé na zařízení ve Windows. Kontexty zařízení slouží k vykreslení na obrazovku, na tiskárně nebo do metasouboru.

[Cpaintdc –](../mfc/reference/cpaintdc-class.md) objekty zapouzdřují běžné idiom Windows, volání `BeginPaint` funkce, a kreslení v kontextu zařízení a potom volání `EndPaint` funkce. `CPaintDC` Volá konstruktor `BeginPaint` pro vás a volání destruktoru `EndPaint`. Zjednodušený proces je vytvořit [CDC](../mfc/reference/cdc-class.md) objektu, kreslení a pak zničilo `CDC` objektu. V rámci velkou část i tento proces automatizovat. Konkrétně se vaše `OnDraw` funkce je předána `CPaintDC` už připravené (prostřednictvím `OnPrepareDC`), a které upoutat do něj. Je zničen rozhraním, a po návratu z volání vydání Windows základního kontextu zařízení vaší `OnDraw` funkce.

[Cclientdc –](../mfc/reference/cclientdc-class.md) objekty zapouzdřují práci s kontextu zařízení, která představuje jenom klientské oblasti okna. `CClientDC` Volá konstruktor `GetDC` funkce a volání destruktoru `ReleaseDC` funkce. [Cwindowdc –](../mfc/reference/cwindowdc-class.md) objekty zapouzdřují kontextu zařízení, která představuje celé okno, včetně jeho rámce.

[Cmetafiledc –](../mfc/reference/cmetafiledc-class.md) objekty zapouzdřují kreslení do Windows metafile. Rozdíl od `CPaintDC` předán `OnDraw`, v tomto případě je nutné volat [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) sami.

## <a name="mouse-drawing"></a>Kreslení myši

Většina kreslení v rámci programu – a tedy většinu práce kontextu zařízení – provádí se v zobrazení `OnDraw` členskou funkci. Objekty kontextu zařízení však lze použít pro jiné účely. Například k poskytnutí zpětné vazby sledování pohybu myši v zobrazení, budete muset kreslení přímo do zobrazení bez čekání na `OnDraw` volat.

V takovém případě můžete použít [cclientdc –](../mfc/reference/cclientdc-class.md) objekt kontext zařízení pro kreslení přímo do zobrazení.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Kontexty zařízení (definice)](/windows/desktop/gdi/device-contexts)

- [Kreslení v zobrazení](../mfc/drawing-in-a-view.md)

- [Interpretace vstupu uživatele prostřednictvím zobrazení](../mfc/interpreting-user-input-through-a-view.md)

- [Čar a křivek](/windows/desktop/gdi/lines-and-curves)

- [Vyplněné tvary](/windows/desktop/gdi/filled-shapes)

- [Písma a text](/windows/desktop/gdi/fonts-and-text)

- [Barvy](/windows/desktop/gdi/colors)

- [Mezery souřadnic a transformace](/windows/desktop/gdi/coordinate-spaces-and-transformations)

## <a name="see-also"></a>Viz také:

[Objekty oken](../mfc/window-objects.md)
