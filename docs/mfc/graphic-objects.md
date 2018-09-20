---
title: Grafické objekty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- HRGN
- HFONT
- HBITMAP
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b62acb002c9035dfa7fa63aaf5efb23f9939c25b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415188"
---
# <a name="graphic-objects"></a>Grafické objekty

Windows poskytuje celou řadu nástrojů pro použití v kontextech zařízení pro kreslení. Poskytuje pera kreslení čar štětce pro výplň vnitřek a písma pro vykreslení textu. Knihovna MFC poskytuje třídy grafických objektů ekvivalentní nástrojů pro kreslení ve Windows. Následující tabulka uvádí dostupné třídy a ekvivalentní Windows grafiky zařízení rozhraní GDI systému popisovač typů.

> [!NOTE]
>  Další informace najdete v dokumentaci sady SDK rozhraní GDI + na: [ https://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp ](https://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp).

Tento článek vysvětluje použití těchto tříd grafických objektů:

### <a name="classes-for-windows-gdi-objects"></a>Třídy pro objektů Windows GDI

|Třída|Typ popisovače Windows|
|-----------|-------------------------|
|[CPen](../mfc/reference/cpen-class.md)|`HPEN`|
|[Cbrush –](../mfc/reference/cbrush-class.md)|`HBRUSH`|
|[Cfont –](../mfc/reference/cfont-class.md)|**HFONT**|
|[CBitmap](../mfc/reference/cbitmap-class.md)|`HBITMAP`|
|[CPalette](../mfc/reference/cpalette-class.md)|`HPALETTE`|
|[CRgn](../mfc/reference/crgn-class.md)|**HRGN**|

> [!NOTE]
>  Třída [služby cimage ve](../atl-mfc-shared/reference/cimage-class.md) poskytuje podporu pro rozšířené rastrového obrázku.

Každá třída grafických objektů v knihovně tříd má konstruktor, který umožňuje vytváření grafických objektů této třídy, které s odpovídající vytvořit funkci, musíte následně inicializujete, jako `CreatePen`.

Každá třída grafických objektů v knihovně tříd má operátor přetypování, který bude přetypovat objekt knihovny MFC do přidružené popisovače Windows. Výsledný popisovač je platná, dokud ho odpojí přidruženého objektu. Použití objektu `Detach` členská funkce se odpojit popisovač.

Následující kód přetypování `CPen` objektu na popisovač Windows:

[!code-cpp[NVC_MFCDocViewSDI#5](../mfc/codesnippet/cpp/graphic-objects_1.cpp)]

#### <a name="to-create-a-graphic-object-in-a-device-context"></a>Vytvoření grafického objektu v kontextu zařízení

1. Definujte grafického objektu v rámci zásobníku. Inicializace objektu s specifické pro typ. vytvořit funkci, například `CreatePen`. Můžete také inicializují objekt v konstruktoru. Najdete v diskuzi o [vytváření jednofázová a dvoufázová](../mfc/one-stage-and-two-stage-construction-of-objects.md), která poskytuje ukázkový kód.

1. [Vyberte objekt, do aktuálního kontextu zařízení](../mfc/selecting-a-graphic-object-into-a-device-context.md), před ukládání staré grafický objekt, který jste vybrali.

1. Až budete hotovi s aktuální grafického objektu, vyberte původní grafického objektu zpět do kontextu zařízení obnovíte jeho stav.

1. Povolte rámec přidělených grafický objekt, který má být automaticky odstraněn, pokud obor je byl ukončen.

> [!NOTE]
>  Pokud budete používat grafického objektu opakovaně, můžete přidělit jednou a pokaždé, když je potřeba vybrat kontextu zařízení. Nezapomeňte odstranit takového objektu, když ho už nepotřebují.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Jednofázová a dvoufázová konstrukce objektů grafiky](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Příklad vytvoření pera ve fázi 1 a 2](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Výběr grafického objektu v kontextu zařízení](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Kontexty zařízení](../mfc/device-contexts.md)

## <a name="see-also"></a>Viz také

[Objekty oken](../mfc/window-objects.md)

