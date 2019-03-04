---
title: Obslužné rutiny pro standardní zprávy Windows
ms.date: 11/04/2016
f1_keywords:
- afx_msg
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
ms.openlocfilehash: d60ae52225ddd993c1768d0b5ce1989ab0192e45
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275386"
---
# <a name="handlers-for-standard-windows-messages"></a>Obslužné rutiny pro standardní zprávy Windows

Výchozí obslužné rutiny pro standardní zprávy Windows (**WM_**) jsou předdefinovány v třídě `CWnd`. Knihovna tříd základů názvy pro tyto obslužné rutiny na název zprávy. Například obslužné rutiny pro **WM_PAINT** zprávy je deklarován v `CWnd` jako:

`afx_msg void OnPaint();`

**Afx_msg** – klíčové slovo navrhuje efekt C++ **virtuální** – klíčové slovo rozlišuje obslužné rutiny z jiných `CWnd` členské funkce. Upozorňujeme, že tyto funkce nejsou ve skutečnosti virtuální; Místo toho implementaci prostřednictvím mapy zpráv. Mapy zpráv závisí výhradně na standardní makra preprocesoru, nikoli na rozšíření jazyka C++. **Afx_msg** – klíčové slovo se překládá na prázdné místo po předběžném zpracování.

K přepsání obslužná rutina definovaná v základní třídě, stačí Definujte funkci s stejný prototyp v odvozené třídě a aby položka mapy zpráv pro obslužnou rutinu. Vaše obslužná rutina "přepisuje" Obslužná rutina se stejným názvem v některém z základních třídách této třídy.

V některých případech se vaše obslužná rutina by měly volat obslužnou rutinu přepsané v základní třídě tak základní třídy a Windows může pracovat ve zprávě. Pokud voláte obslužnou rutinu základní třídy v přepsání závisí na okolnostech. Někdy musíte nejprve volat obslužnou rutinu základní třídy a někdy naposledy. Někdy je volat obslužnou rutinu základní třídy podmíněně, pokud jste vybrali možnost zpracovávat zprávy sami. V některých případech by měla volat obslužnou rutinu základní třídy a pak podmíněně spustit vlastní kód obslužné rutiny, v závislosti na hodnotu nebo stav vrácený obslužnou rutinu základní třídy.

> [!CAUTION]
>  Není bezpečné upravit argumentů předaných do obslužné rutiny, pokud máte v úmyslu předat obslužnou rutinu základní třídy. Například můžete mít tendenci k úpravě *nChar* argument `OnChar` obslužná rutina (k převodu na velká písmena, například). Toto chování je poměrně skrytého, ale pokud potřebujete k dosažení tohoto efektu `CWnd` členskou funkci `SendMessage` místo.

Jak se určují správný způsob, jak přepsat danou zprávu, když v okně Vlastnosti zapíše kostru obslužné rutiny pro danou zprávu – `OnCreate` obslužné rutiny pro **WM_CREATE**, například – výkresy ho ve formuláři Doporučené přepsané členskou funkci. V následujícím příkladu se doporučuje, aby obslužná rutina nejprve volat obslužnou rutinu základní třídy a pokračovat pouze za předpokladu, že nevrací hodnotu -1.

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

Podle úmluvy názvy tyto obslužné rutiny začínají předponou "Na". Některé z těchto obslužných rutin nepřebírají žádné argumenty, zatímco jiné přijímají několik. Některé také mít návratový typ jiný než **void**. Výchozích obslužných rutin pro všechny **WM_** zprávy jsou dokumentovány v článku *odkaz knihovny MFC* jako členské funkce třídy `CWnd` jejichž názvy začínají řetězcem "Na". V deklaraci členské funkce `CWnd` mají předponu **afx_msg**.

## <a name="see-also"></a>Viz také:

[Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)
