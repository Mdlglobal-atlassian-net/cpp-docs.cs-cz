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
ms.openlocfilehash: 227c4614bad42706893301c69882c3f40af12e2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214341"
---
# <a name="drawing-in-a-view"></a>Kreslení v zobrazení

Téměř všechny kresby v aplikaci jsou k dis`OnDraw` členské funkce zobrazení, které je nutné přepsat ve vaší třídě zobrazení. (Výjimkou je vykreslování myší, popsané v tématu [Interpretace vstupu uživatele prostřednictvím zobrazení](../mfc/interpreting-user-input-through-a-view.md).) Vaše `OnDraw` přepsat:

1. Načte data voláním členských funkcí dokumentu, které zadáte.

1. Zobrazí data voláním členských funkcí objektu kontextu zařízení, který rozhraní předává `OnDraw`.

Když se změní data dokumentu nějakým způsobem, je nutné zobrazení překreslit, aby odráželo změny. K tomu obvykle dochází, když uživatel provede změnu zobrazení dokumentu. V tomto případě zobrazení volá členskou funkci [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) dokumentu, aby upozornila všechna zobrazení na stejný dokument, aby se aktualizovala. `UpdateAllViews` volá členskou funkci [Update](../mfc/reference/cview-class.md#onupdate) jednotlivých zobrazení. Výchozí implementace `OnUpdate` neověřuje celou klientskou oblast zobrazení. Můžete ji přepsat tak, aby zrušila platnost pouze těch oblastí klientské oblasti, které jsou mapovány na upravené části dokumentu.

Členská funkce `UpdateAllViews` třídy `CDocument` a členská funkce `OnUpdate` třídy `CView` vám umožní předat informace popisující, které části dokumentu byly změněny. Tento mechanismus "Hint" umožňuje omezit oblast, kterou musí být zobrazení překreslit. `OnUpdate` přebírají dva argumenty "Hint". První *lHint*typu **lParam**umožňuje předat libovolná data, která se vám líbí, zatímco druhá *pHint*typu `CObject`* vám umožní předat ukazatel na libovolný objekt odvozený od `CObject`.

Když bude zobrazení neplatné, Windows pošle **WM_PAINT** zprávu. Obslužná rutina funkce [Propainta](../mfc/reference/cwnd-class.md#onpaint) pro zobrazení reaguje na zprávu vytvořením objektu kontextu zařízení třídy [CPaintDC –](../mfc/reference/cpaintdc-class.md) a voláním členské funkce zobrazení `OnDraw`. Nemusíte normálně psát překrytou funkci `OnPaint` obslužných rutin.

[Kontext zařízení](../mfc/device-contexts.md) je datová struktura systému Windows, která obsahuje informace o atributech kreslení zařízení, jako je například displej nebo tiskárna. Všechna volání vykreslování jsou vytvořena pomocí objektu kontextu zařízení. Pro kreslení na obrazovce `OnDraw` k předanému objektu `CPaintDC`. Pro kreslení na tiskárně je předán objekt [CDC](../mfc/reference/cdc-class.md) nastavený pro aktuální tiskárnu.

Váš kód pro kreslení v zobrazení nejprve načte ukazatel na dokument a pak provede vykreslování v kontextu zařízení. Následující příklad jednoduchého `OnDraw` ilustruje proces:

[!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]

V tomto příkladu byste definovali funkci `GetData` jako člen odvozené třídy dokumentu.

Tento příklad vytiskne libovolný řetězec, který získá z dokumentu, na střed v zobrazení. Pokud je volání `OnDraw` pro kreslení obrazovky, předaný objekt `CDC` v *primárním řadiči domény* je `CPaintDC` jehož konstruktor již byl volán `BeginPaint`. Volání funkcí kreslení se provádí přes ukazatel kontextu zařízení. Informace o kontextech zařízení a kreslení voláních naleznete v tématu Class [CDC](../mfc/reference/cdc-class.md) v *Referenci knihovny MFC* a [práce s objekty okna](../mfc/working-with-window-objects.md).

Další příklady, jak zapisovat `OnDraw`, naleznete v tématu [MFC Samples](../overview/visual-cpp-samples.md#mfc-samples).

## <a name="see-also"></a>Viz také

[Použití zobrazení](../mfc/using-views.md)
