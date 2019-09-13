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
ms.openlocfilehash: 4f512c3b9a7fce5cddd582fa774742d2b1ac0967
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907430"
---
# <a name="handlers-for-standard-windows-messages"></a>Obslužné rutiny pro standardní zprávy Windows

Výchozí obslužné rutiny pro standardní zprávy systému Windows (**WM_** ) jsou `CWnd`předdefinované ve třídě. Knihovna tříd je založena na názvech těchto obslužných rutin. Například obslužná rutina pro zprávu **WM_PAINT** je deklarována v `CWnd` podobě:

`afx_msg void OnPaint();`

Klíčové slovo **afx_msg** navrhuje vliv C++ klíčového slova **Virtual** pomocí rozlišení obslužných rutin od ostatních `CWnd` členských funkcí. Všimněte si ale, že tyto funkce nejsou ve skutečnosti virtuální; místo toho jsou implementovány prostřednictvím map zpráv. Mapy zpráv závisí výhradně na standardních makrech preprocesoru, nikoli na žádném rozšíření C++ jazyka. Klíčové slovo **afx_msg** se po předzpracování převede na prázdné místo.

Pro přepsání obslužné rutiny definované v základní třídě stačí definovat funkci se stejným prototypem v odvozené třídě a vytvořit položku mapování zpráv pro obslužnou rutinu. Vaše obslužná rutina "Přepisuje" všechny obslužné rutiny se stejným názvem v kterékoli ze základních tříd vaší třídy.

V některých případech by obslužná rutina měla volat přepsanou obslužnou rutinu v základní třídě, aby základní třídy a systém Windows mohly pracovat se zprávou. Místo volání obslužné rutiny základní třídy v přepsání závisí na okolnostech. Někdy je nutné zavolat rutinu základní třídy jako první a někdy poslední. Někdy je volána rutina základní třídy, pokud se rozhodnete Nezpracovávat zprávu sami. Někdy byste měli zavolat obslužnou rutinu základní třídy a pak podmíněně spustit vlastní kód obslužné rutiny v závislosti na hodnotě nebo stavu vráceném obslužnou rutinou základní třídy.

> [!CAUTION]
>  V případě, že je v úmyslu předat obslužné rutině základní třídy, není bezpečné upravovat argumenty předané obslužné rutině. Můžete například zvážit úpravu argumentu `OnChar` *nchar* obslužné rutiny (pro převod na velká písmena, například). Toto chování je poměrně zakryté, ale pokud k tomu potřebujete, použijte `CWnd` místo toho členskou funkci. `SendMessage`

Jak určíte správný způsob, jak přepsat danou zprávu, když [Průvodce třídou](reference/mfc-class-wizard.md) zapíše kostru funkce obslužné rutiny pro danou zprávu – `OnCreate` obslužná rutina pro **WM_CREATE**, například, se náčrtuje ve formě Doporučené přepsaná členská funkce Následující příklad doporučuje, aby obslužná rutina nejprve volala obslužnou rutinu základní třídy a pokračovala pouze za podmínkou, že nevrátí-1.

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

Podle konvence názvy těchto obslužných rutin začínají předponou "on". Některé z těchto obslužných rutin nevyužívají žádné argumenty, zatímco jiné vybírají několik. Některé mají také návratový typ jiný než **void**. Výchozí obslužné rutiny pro všechny zprávy **WM_** jsou zdokumentovány v *Referenci knihovny MFC* jako členské funkce `CWnd` třídy, jejichž názvy začínají na "on". Deklarace členské funkce v `CWnd` mají předponu **afx_msg**.

## <a name="see-also"></a>Viz také:

[Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)
