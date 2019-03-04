---
title: Třídy ovládacích pruhů
ms.date: 11/04/2016
f1_keywords:
- vc.classes.control
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: 3426d84eab888a6fe78b663945776fff2fe708dd
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302244"
---
# <a name="control-bar-classes"></a>Třídy ovládacích pruhů

Ovládací pruhy jsou připojeny k okno rámce. Obsahují tlačítka, stav podoken nebo šablony dialogového okna. Plovoucí ovládací pruhy, také nazývané nástroj palety, jsou implementovány jejich připojením [cminiframewnd –](../mfc/reference/cminiframewnd-class.md) objektu.

## <a name="framework-control-bars"></a>Rozhraní Framework ovládací pruhy

Tyto ovládací pruhy jsou nedílnou součástí rozhraní MFC. Se snadněji používá a výkonnější, než Windows řídit pruhy integrovaná se službami rozhraní framework. Většina aplikací knihovny MFC pomocí těchto ovládacích pruhů spíše než ovládacích panelů Windows.

[CControlBar](../mfc/reference/ccontrolbar-class.md)<br/>
Základní třída pro MFC – ovládací pruhy uvedené v této části. Ovládací panel je okno zarovnané k okraji okna rámce. Ovládací panel obsahuje buď `HWND`– na základě podřízených ovládacích prvků nebo není založen na ovládací prvky `HWND`, jako jsou tlačítka na panelu nástrojů.

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
Ovládací panel, který je založen na šablony dialogového okna.

[CReBar](../mfc/reference/crebar-class.md)<br/>
Podporuje, který může obsahovat další podřízená okna do formuláře ovládací prvky panelu nástrojů.

[CToolBar](../mfc/reference/ctoolbar-class.md)<br/>
Na základě windows ovládacího prvku panel nástrojů, obsahující příkazová tlačítka rastrového obrázku není `HWND`. Většina aplikací MFC, použijte tuto třídu spíše než `CToolBarCtrl`.

[CStatusBar](../mfc/reference/cstatusbar-class.md)<br/>
Základní třída pro ovládací prvek stavového systému windows. Většina aplikací MFC, použijte tuto třídu spíše než `CStatusBarCtrl`.

## <a name="windows-control-bars"></a>Windows ovládací pruhy

Tyto ovládací pruhy jsou dynamického zajišťování obálky pro odpovídající ovládací prvky Windows. Protože se bude integrovat s použitím rozhraní framework, jsou obtížnější než ovládací pruhy výše uvedených. Většina aplikací knihovny MFC používá ovládací pruhy výše uvedených.

[CRebarCtrl](../mfc/reference/crebarctrl-class.md)<br/>
Implementuje interního řízení `CRebar` objektu.

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
Vodorovné okno obvykle rozdělena na dvě podokna, ve kterých může aplikace zobrazit informace o stavu.

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Poskytuje funkce pro Windows nástrojů běžný ovládací prvek.

## <a name="related-classes"></a>Související třídy

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
Malého vyskakovacího okna, která zobrazuje jeden řádek textu popisujícího účel nástroje v aplikaci.

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
Zpracovává ukotvení data o stavu pro ovládacích pruhů trvalého úložiště.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
