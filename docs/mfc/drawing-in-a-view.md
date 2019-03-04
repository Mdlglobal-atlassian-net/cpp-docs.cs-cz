---
title: Kreslení v zobrazení
ms.date: 11/04/2016
helpviewer_keywords:
- drawing [MFC], in views
- views [MFC], printing
- views [MFC], updating
- printing [MFC], views
- views [MFC], rendering
- printing views [MFC]
- paint messages in view class [MFC]
- device contexts, screen drawings
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
ms.openlocfilehash: 77844ebd31f624229870d27c72b08a987b7533bd
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280768"
---
# <a name="drawing-in-a-view"></a>Kreslení v zobrazení

Téměř všechny kreslení ve vaší aplikaci dochází v zobrazení `OnDraw` členská funkce, které je nutné přepsat ve třídě zobrazení. (Výjimkou je myši kreslení, popsané v [interpretace vstupu uživatele prostřednictvím zobrazení](../mfc/interpreting-user-input-through-a-view.md).) Vaše `OnDraw` přepsat:

1. Získá data voláním členské funkce, které poskytnete dokumentu.

1. Zobrazí data voláním členské funkce objektu kontextu zařízení, která se předá rozhraní framework `OnDraw`.

Při změně dat dokumentu nějakým způsobem, musí být vystavena zobrazení tak, aby odrážely změny. Obvykle se to stane, když uživatel provede změny prostřednictvím zobrazení v dokumentu. V takovém případě volá zobrazení dokumentu [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) členskou funkci oznámit všechna zobrazení na stejný dokument aktualizovat sami. `UpdateAllViews` každé zobrazení volá [OnUpdate](../mfc/reference/cview-class.md#onupdate) členskou funkci. Výchozí implementace `OnUpdate` zruší platnost celou klientskou oblast zobrazení. Můžete přepsat tak zneplatnit pouze ty oblasti od klientské oblasti, které mapují na změněné části dokumentu.

`UpdateAllViews` Členské funkce třídy `CDocument` a `OnUpdate` členské funkce třídy `CView` umožňují předat informace, které popisují, které části dokumentu byly upraveny. Tento mechanismus "Nápověda" umožňuje omezit oblasti, která musí ho překreslit zobrazení. `OnUpdate` přebírá dva argumenty "Nápověda". První s názvem *lHint*, typu **LPARAM**, vám umožní předat žádná data, která vám vyhovuje, zatímco druhý *pHint*, typu `CObject`*, vám umožní předat ukazatel na libovolný objekt, odvozený z `CObject`.

Při zobrazení níže uvedených situací, Windows odešle ji **WM_PAINT** zprávy. Zobrazení [OnPaint](../mfc/reference/cwnd-class.md#onpaint) funkci obslužné rutiny reaguje na zprávy tak, že vytvoříte objekt kontextu zařízení třídy [cpaintdc –](../mfc/reference/cpaintdc-class.md) a volá do zobrazení `OnDraw` členskou funkci. Obvykle nemáte pro zápis přepsání `OnPaint` funkci obslužné rutiny.

A [kontextu zařízení](../mfc/device-contexts.md) je datová struktura Windows, který obsahuje informace o vykreslování atributy zařízení, jako je například tiskárnu nebo zobrazení. Všechna volání kreslení probíhají prostřednictvím objektů kontextu zařízení. Pro kreslení na obrazovce `OnDraw` je předán `CPaintDC` objektu. Pro kreslení na tiskárně, je předán [CDC](../mfc/reference/cdc-class.md) objekt nastavení pro aktuální tiskárny.

Váš kód pro kreslení v zobrazení nejprve načte ukazatel na dokument, pak provede volání kreslení pomocí kontextu zařízení. Následující jednoduchý `OnDraw` příklad znázorňuje proces:

[!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]

V tomto příkladu byste definovali `GetData` fungovat jako člen třídy odvozené dokumentu.

Tento příklad vytiskne jakýkoli řetězec získá z dokumentu, zarovnání na střed v zobrazení. Pokud `OnDraw` volání je pro vykreslování obrazovky `CDC` objekt předaný v *primárního řadiče domény* je `CPaintDC` jejíž konstruktor již volána `BeginPaint`. Volání funkce vykreslování se provádějí přes ukazatel kontextu zařízení. Informace o volání kreslení a kontexty zařízení najdete v tématu třídy [CDC](../mfc/reference/cdc-class.md) v *odkaz knihovny MFC* a [práce s objekty oken](../mfc/working-with-window-objects.md).

Další příklady o tom, jak psát `OnDraw`, najdete v článku [ukázky knihovny MFC](../visual-cpp-samples.md).

## <a name="see-also"></a>Viz také:

[Použití zobrazení](../mfc/using-views.md)
