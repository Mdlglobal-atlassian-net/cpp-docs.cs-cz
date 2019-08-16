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
ms.openlocfilehash: d5337e8d8b83a641458a15612803feeec3b6361c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508654"
---
# <a name="device-contexts"></a>Kontexty zařízení

Kontext zařízení je datová struktura systému Windows, která obsahuje informace o atributech kreslení zařízení, jako je například displej nebo tiskárna. Všechna volání vykreslování jsou vytvořena pomocí objektu kontextu zařízení, který zapouzdřuje rozhraní API systému Windows pro kreslení čar, tvarů a textu. Kontexty zařízení umožňují kreslení nezávislé na zařízení v systému Windows. Kontexty zařízení lze použít k vykreslení na obrazovku, do tiskárny nebo do metasouboru.

Objekty [CPaintDC –](../mfc/reference/cpaintdc-class.md) zapouzdřují běžné idiom Windows, zavolají `BeginPaint` funkci, vykreslí do kontextu zařízení `EndPaint` a pak zavolají funkci. Konstruktor volá `BeginPaint` za vás a volá `EndPaint`destruktor. `CPaintDC` Zjednodušeným procesem je vytvoření objektu [CDC](../mfc/reference/cdc-class.md) , vykreslení a zničení `CDC` objektu. V rozhraní je většina i tento proces automatizovaná. Konkrétně je vaše `OnDraw` funkce `CPaintDC` předána už připravená (přes `OnPrepareDC`) a jednoduše se do ní nakreslíte. Je zničena rozhraním a základní kontext zařízení je uvolněn do systému Windows při návratu z volání `OnDraw` funkce.

Objekty [CClientDC –](../mfc/reference/cclientdc-class.md) zapouzdřují práci s kontextem zařízení, který představuje pouze klientskou oblast okna. Konstruktor volá funkci a destruktor volá funkci. `ReleaseDC` `CClientDC` `GetDC` Objekty [CWindowDC](../mfc/reference/cwindowdc-class.md) zapouzdřují kontext zařízení, který představuje celé okno, včetně jeho rámce.

Objekty [CMetaFileDC –](../mfc/reference/cmetafiledc-class.md) zapouzdřují kreslení do metasouboru Windows. Na rozdíl `CPaintDC` od předaného `OnDraw`do musíte v tomto případě volat [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) sami.

## <a name="mouse-drawing"></a>Kreslení myší

Většina kreslení v rámci programu – a tedy většina práce v kontextu zařízení – je prováděna v `OnDraw` členské funkci zobrazení. Pro jiné účely však můžete přesto použít objekty kontextu zařízení. Například chcete-li poskytnout zpětnou vazbu ke sledování pohybu myši v zobrazení, je nutné kreslit přímo do zobrazení bez čekání `OnDraw` na volání.

V takovém případě můžete použít objekt kontextu zařízení [CClientDC –](../mfc/reference/cclientdc-class.md) k nakreslení přímo do zobrazení.

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Kontexty zařízení (definice)](/windows/win32/gdi/device-contexts)

- [Kreslení v zobrazení](../mfc/drawing-in-a-view.md)

- [Interpretace vstupu uživatele prostřednictvím zobrazení](../mfc/interpreting-user-input-through-a-view.md)

- [Čáry a křivky](/windows/win32/gdi/lines-and-curves)

- [Vyplněné obrazce](/windows/win32/gdi/filled-shapes)

- [Písma a text](/windows/win32/gdi/fonts-and-text)

- [Barvy](/windows/win32/gdi/colors)

- [Souřadnice mezer a transformací](/windows/win32/gdi/coordinate-spaces-and-transformations)

## <a name="see-also"></a>Viz také:

[Objekty oken](../mfc/window-objects.md)
