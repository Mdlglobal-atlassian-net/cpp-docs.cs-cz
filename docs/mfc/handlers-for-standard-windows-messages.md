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
ms.openlocfilehash: 9a136caf3a1d22151cb9cfd48e1cd3f999ab51ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370492"
---
# <a name="handlers-for-standard-windows-messages"></a>Obslužné rutiny pro standardní zprávy Windows

Výchozí obslužné**WM_** rutiny pro standardní `CWnd`zprávy systému Windows ( WM_ ) jsou předdefinovány ve třídě . Knihovna tříd zakládá názvy těchto obslužných rutin na názvu zprávy. Například obslužná rutina `CWnd` pro zprávu **WM_PAINT** je deklarována jako:

`afx_msg void OnPaint();`

Klíčové slovo **afx_msg** naznačuje efekt **virtuálního** klíčového slova Jazyka C++ odlišením obslužných rutin od ostatních `CWnd` členských funkcí. Všimněte si však, že tyto funkce nejsou ve skutečnosti virtuální; jsou místo toho implementovány prostřednictvím map zpráv. Mapy zpráv závisí výhradně na standardních makerách preprocesoru, nikoli na rozšířeních jazyka C++. Klíčové slovo **afx_msg** se po předběžném zpracování překládá na prázdné místo.

Chcete-li přepsat obslužnou rutinu definovanou v základní třídě, jednoduše definujte funkci se stejným prototypem v odvozené třídě a vytvořte položku mapy zprávy pro obslužnou rutinu. Obslužná rutina "přepíše" všechny obslužné rutiny se stejným názvem v některé ze základních tříd vaší třídy.

V některých případech by měla obslužná rutina volat obslužnou rutinu v základní třídě, aby základní třídy (y) a systém Windows mohly pracovat se zprávou. Kde zavoláte obslužnou rutinu základní třídy v přepsání závisí na okolnostech. Někdy je nutné nejprve zavolat obslužnou rutinu základní třídy a někdy i poslední. Někdy zavoláte obslužnou rutinu základní třídy podmíněně, pokud se rozhodnete nezpracovat zprávu sami. Někdy byste měli volat obslužnou rutinu základní třídy a pak podmíněně spustit vlastní kód obslužné rutiny v závislosti na hodnotě nebo stavu vráceném obslužnou rutinou základní třídy.

> [!CAUTION]
> Není bezpečné změnit argumenty předané do obslužné rutiny, pokud máte v úmyslu předat je obslužné rutině základní třídy. Můžete být například v pokušení upravit argument *nChar* `OnChar` obslužné rutiny (například převést na velká písmena). Toto chování je poměrně obskurní, ale `CWnd` pokud `SendMessage` potřebujete dosáhnout tohoto efektu, použijte místo toho členská funkce.

Jak určit správný způsob, jak přepsat danou zprávu Když [Průvodce třídou](reference/mfc-class-wizard.md) zapíše kostru `OnCreate` funkce obslužné rutiny pro danou zprávu – například obslužnou rutinu pro **WM_CREATE**– načrtne ve formě doporučené přepsané členské funkce. Následující příklad doporučuje, aby obslužná rutina nejprve volání obslužné rutiny základní třídy a pokračovat pouze za podmínky, že nevrátí -1.

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

Podle konvence názvy těchto obslužných rutin začínají předponou "Zapnuto". Některé z těchto obslužných rutin neberou žádné argumenty, zatímco jiné trvat několik. Některé mají také návratový typ než **void**. Výchozí obslužné rutiny pro všechny **WM_** zprávy jsou `CWnd` popsány v *odkaz knihovny MFC* jako členské funkce třídy, jejíž názvy začínají "On". Deklarace členské funkce `CWnd` v je předpona s **afx_msg**.

## <a name="see-also"></a>Viz také

[Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)
