---
title: Klienti automatizace
ms.date: 11/04/2016
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
ms.openlocfilehash: 30511ec6c9f0e00f4cec51e00f85ea5e32453327
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465491"
---
# <a name="automation-clients"></a>Klienti automatizace

Automatizace umožňuje aplikaci k manipulaci s objekty, které jsou implementovány v jiné aplikaci, nebo ke zveřejnění objekty, lze manipulovat. Klient služby Automation je aplikace, která můžete pracovat s vystavené objekty, které patří do jiné aplikace. Aplikace, která zveřejňuje objekty se nazývá automatizační server. Klient zpracovává objekty serverových aplikací díky přístupu do vlastností a funkcí těchto objektů.

### <a name="types-of-automation-clients"></a>Typy klientů služby Automation

Existují dva typy klientů služby Automation:

- Klienti, kteří dynamicky (za běhu) získat informace o vlastnosti a operace serveru.

- Klienti, kteří mají poskytnutých statických údajů (v době kompilace), která určuje vlastnosti a operace serveru.

Klienti první druh získat informace o metodách a vlastnostech serveru dotazováním OLE systému `IDispatch` mechanismus. I když je vhodné použít pro dynamické klienty `IDispatch` je obtížné pro klienty, použijte statické, kde objekty se řízené musí být známo v době kompilace. Pro statické vázat klientů, Microsoft Foundation classes poskytuje [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md) třídy.

Statické vázané klienti používat třídu proxy, která je staticky propojena s klientskou aplikací. Tato třída poskytuje zapouzdření C++ zajišťující bezpečnost typů vlastností a operací serverová aplikace.

Třída `COleDispatchDriver` poskytuje instančního objektu podporu pro stranu klienta služby Automation. Použití **přidat novou položku** dialogovém okně vytvořit třídu odvozenou z `COleDispatchDriver`.

Pak zadejte soubor knihovny typů popisující vlastnosti a funkce serveru aplikační objekt. Dialogové okno Přidat položku čtení tohoto souboru a vytvoří `COleDispatchDriver`-odvozené třídy pomocí členské funkce, které vaše aplikace můžou zavolat způsobem typově bezpečný přístup k objektům serverová aplikace v jazyce C++. Další funkce zděděno z `COleDispatchDriver` zjednodušuje proces voláním řádného automatizační server.

### <a name="handling-events-in-automation-clients"></a>Zpracování událostí u klientů automatizace

Pokud chcete zpracovávat události v klientovi služby automation, musíte přidat rozhraní jímky. Knihovna MFC poskytuje podporu průvodce přidat rozhraní jímky pro ovládací prvky ActiveX, ale není podporován pro ostatní servery COM.

## <a name="see-also"></a>Viz také

[Klienti automatizace: Použití knihoven typů](../mfc/automation-clients-using-type-libraries.md)<br/>
[Automatizace](../mfc/automation.md)<br/>
[MFC – průvodce aplikací](../mfc/reference/mfc-application-wizard.md)

