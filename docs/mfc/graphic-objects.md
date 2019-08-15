---
title: Grafické objekty
ms.date: 11/04/2016
f1_keywords:
- HRGN
- HFONT
- HBITMAP
helpviewer_keywords:
- CRgn class [MFC], HRGN handle type
- HPEN [MFC]
- objects [MFC], graphic
- palettes [MFC], creating in device context
- pens [MFC], creating in device context
- bitmaps [MFC], creating in device contexts
- palette objects [MFC]
- memory [MFC], display contexts
- MFC, graphic objects
- regions [MFC], creating in device context
- CPen class [MFC], HPEN handle type
- GDI objects [MFC]
- HRGN [MFC]
- graphic objects [MFC]
- GDI objects [MFC], graphic-object classes
- CFont class [MFC], HFONT handle type
- HFONT and class CFont [MFC]
- HBITMAP and class CBitmap [MFC]
- fonts [MFC], creating in device context
- images [MFC], graphic objects [MFC]
- CBitmap class [MFC], HBITMAP handle type
- HPALETTE and class CPalette [MFC]
- CBrush class [MFC], HBRUSH handle type
- objects [MFC], graphic objects
- drawing [MFC], in device contexts
- device contexts [MFC], graphic objects [MFC]
- brushes [MFC], creating in device context
- region objects [MFC]
- pen objects [MFC]
- GDI [MFC], graphic-object classes
- graphic objects [MFC], creating in device context
- HBRUSH and class CBrush [MFC]
- painting and device context [MFC]
- CPalette class [MFC], HPALETTE handle type
ms.assetid: 41963b25-34b7-4343-8446-34ba516b83ca
ms.openlocfilehash: 4abc2764abd0f31b83253f37b8cb459be638ae5a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508543"
---
# <a name="graphic-objects"></a>Grafické objekty

Systém Windows poskytuje celou řadu nástrojů pro kreslení, které lze použít v kontextech zařízení. Nabízí pera k vykreslování čar, štětců k vyplnění vnitřních a k nakreslení textu písem. Knihovna MFC poskytuje třídy grafických objektů, které odpovídají nástrojům kreslení v systému Windows. V následující tabulce jsou uvedeny dostupné třídy a ekvivalentní typy popisovačů rozhraní GDI (Windows Graphics Device Interface).

> [!NOTE]
>  Další informace najdete v [dokumentaci k rozhraní GDI+ SDK](/windows/win32/gdiplus/-gdiplus-gdi-start).

Tento článek vysvětluje použití těchto tříd grafických objektů:

### <a name="classes-for-windows-gdi-objects"></a>Třídy pro objekty GDI systému Windows

|Třída|Typ popisovače systému Windows|
|-----------|-------------------------|
|[CPen](../mfc/reference/cpen-class.md)|`HPEN`|
|[CBrush –](../mfc/reference/cbrush-class.md)|`HBRUSH`|
|[CFont –](../mfc/reference/cfont-class.md)|**HFONT**|
|[CBitmap](../mfc/reference/cbitmap-class.md)|`HBITMAP`|
|[CPalette](../mfc/reference/cpalette-class.md)|`HPALETTE`|
|[CRgn](../mfc/reference/crgn-class.md)|**HRGN**|

> [!NOTE]
>  Třída [služby CImage ve](../atl-mfc-shared/reference/cimage-class.md) poskytuje rozšířenou podporu rastrového obrázku.

Každá třída grafického objektu v knihovně tříd má konstruktor, který umožňuje vytvořit grafické objekty této třídy, které musíte následně inicializovat pomocí příslušné funkce Create, `CreatePen`jako je například.

Každá třída grafického objektu v knihovně tříd má operátor přetypování, který přetypování objektu knihovny MFC na přidružený popisovač systému Windows. Výsledný popisovač je platný, dokud jej přidružený objekt odpojí. K odpojení popisovače použijte `Detach` členskou funkci objektu.

Následující kód přetypování `CPen` objektu na popisovač systému Windows:

[!code-cpp[NVC_MFCDocViewSDI#5](../mfc/codesnippet/cpp/graphic-objects_1.cpp)]

#### <a name="to-create-a-graphic-object-in-a-device-context"></a>Vytvoření grafického objektu v kontextu zařízení

1. Definujte grafický objekt v bloku zásobníku. Inicializujte objekt pomocí funkce Create specifické pro typ, například `CreatePen`. Případně Inicializujte objekt v konstruktoru. Podívejte se na diskusi o [jednom kroku a dvoufázové tvorbě](../mfc/one-stage-and-two-stage-construction-of-objects.md), která poskytuje příklad kódu.

1. [Vyberte objekt v kontextu aktuálního zařízení](../mfc/selecting-a-graphic-object-into-a-device-context.md)a uložte starý grafický objekt, který byl vybrán před.

1. Po dokončení s aktuálním grafickým objektem vyberte starý grafický objekt zpátky do kontextu zařízení a obnovte jeho stav.

1. Povolí odstranění objektu, který je přidělený snímkům automaticky při ukončení oboru.

> [!NOTE]
>  Pokud budete grafický objekt opakovaně používat, můžete ho přidělit jednou a vybrat ho do kontextu zařízení pokaždé, když je potřeba. Nezapomeňte takový objekt odstranit, pokud ho již nepotřebujete.

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Jedna fáze a dvoufázové konstrukce grafických objektů](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Příklad konstrukce pera v jedné a dvou fázích](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Výběr grafického objektu v kontextu zařízení](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Kontexty zařízení](../mfc/device-contexts.md)

## <a name="see-also"></a>Viz také:

[Objekty oken](../mfc/window-objects.md)
