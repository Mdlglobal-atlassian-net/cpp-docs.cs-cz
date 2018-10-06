---
title: Klienti automatizace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4a4327e1c3e4d65c5bdc3b822cf2cdfc1ec0353
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820591"
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

Pokud chcete zpracovávat události v klientovi služby automation, musíte přidat rozhraní jímky. Knihovna MFC poskytuje podporu průvodce přidat rozhraní jímky pro ovládací prvky ActiveX, ale není podporován pro ostatní servery COM. Informace o tom, jak přidat rozhraní stoku v klientovi knihovny MFC pro rozhraní zdroje popsal serverů modelu COM, naleznete v tématu Postupy: vytváření rozhraní stoku v ovládací klient modelu COM (KB 181845) na [ http://support.microsoft.com/default.aspxscid=kb; 181845](http://support.microsoft.com/default.aspxscid=kb;181845).

## <a name="see-also"></a>Viz také

[Klienti automatizace: Použití knihoven typů](../mfc/automation-clients-using-type-libraries.md)<br/>
[Automatizace](../mfc/automation.md)<br/>
[MFC – průvodce aplikací](../mfc/reference/mfc-application-wizard.md)

