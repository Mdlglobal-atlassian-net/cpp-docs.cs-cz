---
title: Výstupní třídy (třídy kontextu zařízení)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.output
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
ms.openlocfilehash: 1d76570e7bfd4ce587b3803235394ec5406d30b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410197"
---
# <a name="output-device-context-classes"></a>Výstupní třídy (třídy kontextu zařízení)

Tyto třídy zapouzdřují různé druhy kontexty zařízení ve Windows.

Většina následující třídy zapouzdření popisovač kontextu zařízení Windows. Kontext zařízení je objekt Windows, který obsahuje informace o vykreslování atributy zařízení, jako je například tiskárnu nebo zobrazení. Všechna volání kreslení probíhají prostřednictvím objektů kontextu zařízení. Další třídy odvozené z `CDC` zapouzdřují funkce specializované kontextu zařízení, včetně podpory pro Windows metasoubory.

[CDC](../mfc/reference/cdc-class.md)<br/>
Základní třída pro kontext zařízení. Použít přímo pro přístup k celé zobrazení a pro přístup k nondisplay kontextů, jako jsou tiskárny.

[CPaintDC](../mfc/reference/cpaintdc-class.md)<br/>
Zobrazení kontext použitý v `OnPaint` členské funkce systému windows. Automaticky volá `BeginPaint` konstrukcí a `EndPaint` při destrukci.

[CClientDC](../mfc/reference/cclientdc-class.md)<br/>
Kontext zobrazení pro klientské oblasti okna. Používá, například, chcete-li nakreslit v okamžitou reakci na události myši.

[CWindowDC](../mfc/reference/cwindowdc-class.md)<br/>
Kontext zobrazení pro celý systém windows, včetně jak klientská a neklientská oblast.

[CMetaFileDC](../mfc/reference/cmetafiledc-class.md)<br/>
Kontext zařízení pro Windows metasoubory. Windows metafile obsahuje posloupnost grafiky zařízení (GDI) příkazy, které můžete vytvořit bitovou kopii znovu přehrát. Volání členské funkce `CMetaFileDC` se zaznamenávají do metasouboru.

## <a name="related-classes"></a>Související třídy

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Obsahuje dvojice souřadnic (x, y).

[Csize –](../atl-mfc-shared/reference/csize-class.md)<br/>
Obsahuje vzdálenost, relativní pozice nebo dvojice hodnot.

[Crect –](../atl-mfc-shared/reference/crect-class.md)<br/>
Obsahuje souřadnice obdélníkového oblastí.

[CRgn](../mfc/reference/crgn-class.md)<br/>
Zapouzdřuje oblast rozhraní GDI pro manipulaci s elipsy, mnohoúhelníkové nebo nepravidelného oblast v rámci časového období. Používá ve spojení s výstřižek členské funkce ve třídě `CDC`.

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
Zobrazí a zpracovává uživatelské rozhraní pro změnu velikosti a přesunutí obdélníkový objekty.

[CColorDialog](../mfc/reference/ccolordialog-class.md)<br/>
Poskytuje standardní dialogové okno pro výběr barvy.

[CFontDialog](../mfc/reference/cfontdialog-class.md)<br/>
Poskytuje standardní dialogové okno pro výběr písma.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Poskytuje standardní dialogové okno pro tisk souboru.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
