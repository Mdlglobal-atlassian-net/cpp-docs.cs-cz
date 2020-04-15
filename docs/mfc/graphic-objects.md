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
ms.openlocfilehash: 0201e53114b71c02877762f89cc65fc46d17700c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370529"
---
# <a name="graphic-objects"></a>Grafické objekty

Systém Windows poskytuje různé kreslicí nástroje, které lze použít v kontextech zařízení. Poskytuje pera kreslit čáry, stopy vyplnit interiéry a písma k tomu text. Knihovna MFC poskytuje třídy grafických objektů ekvivalentní kreslicím nástrojům v systému Windows. V následující tabulce jsou uvedeny dostupné třídy a ekvivalentní typy popisovačů rozhraní GDI (Windows graphics device interface).

> [!NOTE]
> Další informace naleznete v [dokumentaci k gdi+ sdk .](/windows/win32/gdiplus/-gdiplus-gdi-start)

Tento článek vysvětluje použití těchto tříd grafického objektu:

### <a name="classes-for-windows-gdi-objects"></a>Třídy pro objekty GDI systému Windows

|Třída|Typ popisovače systému Windows|
|-----------|-------------------------|
|[CPen](../mfc/reference/cpen-class.md)|`HPEN`|
|[CBrush](../mfc/reference/cbrush-class.md)|`HBRUSH`|
|[CPísmo](../mfc/reference/cfont-class.md)|**HFONT**|
|[CBitmap](../mfc/reference/cbitmap-class.md)|`HBITMAP`|
|[CPaleta](../mfc/reference/cpalette-class.md)|`HPALETTE`|
|[CRgn](../mfc/reference/crgn-class.md)|**HRGN**|

> [!NOTE]
> Třída [CImage](../atl-mfc-shared/reference/cimage-class.md) poskytuje rozšířenou podporu bitmap.

Každá třída grafického objektu v knihovně tříd má konstruktor, který umožňuje vytvářet grafické objekty této třídy, které je pak nutné inicializovat pomocí příslušné funkce create, například `CreatePen`.

Každá třída grafického objektu v knihovně tříd má operátor přetypádka, který přetypovat objekt knihovny MFC do přidruženého popisovače systému Windows. Výsledný popisovač je platný, dokud jej přidružený objekt neodpojí. Pomocí `Detach` členské funkce objektu odpojte úchyt.

Následující kód přetypuje `CPen` objekt do popisovače systému Windows:

[!code-cpp[NVC_MFCDocViewSDI#5](../mfc/codesnippet/cpp/graphic-objects_1.cpp)]

#### <a name="to-create-a-graphic-object-in-a-device-context"></a>Vytvoření grafického objektu v kontextu zařízení

1. Definujte grafický objekt v rámečku zásobníku. Inicializovat objekt pomocí funkce vytvoření specifické `CreatePen`pro typ, například . Případně inicializovat objekt v konstruktoru. Podívejte se na diskusi o [jednofázové a dvoufázové vytvoření](../mfc/one-stage-and-two-stage-construction-of-objects.md), který poskytuje ukázkový kód.

1. [Vyberte objekt do aktuálního kontextu zařízení](../mfc/selecting-a-graphic-object-into-a-device-context.md)a ušetřete starý grafický objekt, který byl vybrán dříve.

1. Po dokončení s aktuálním grafickým objektem vyberte starý grafický objekt zpět do kontextu zařízení, abyste obnovili jeho stav.

1. Povolit automatické odstranění grafického objektu přiděleného rámcem při ukončení oboru.

> [!NOTE]
> Pokud budete grafický objekt používat opakovaně, můžete jej přidělit jednou a vybrat jej do kontextu zařízení pokaždé, když je potřeba. Ujistěte se, že odstranit takový objekt, když již nepotřebujete.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Jednostupňová a dvoustupňová konstrukce grafických objektů](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Příklad konstrukce pera v jedné a dvou fázích](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Výběr grafického objektu v kontextu zařízení](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Kontexty zařízení](../mfc/device-contexts.md)

## <a name="see-also"></a>Viz také

[Objekty oken](../mfc/window-objects.md)
