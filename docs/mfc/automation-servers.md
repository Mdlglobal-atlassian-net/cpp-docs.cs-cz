---
title: Automatizační servery
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
ms.openlocfilehash: 510acfa032ca4303962164a19130ecd1971060fc
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907963"
---
# <a name="automation-servers"></a>Automatizační servery

Automatizace umožňuje vaší aplikaci manipulovat s objekty implementovanými v jiné aplikaci nebo zpřístupnit objekty, aby mohly být manipulovány. Automatizační server je aplikace, která zpřístupňuje programovatelné objekty (nazývané automatizační objekty) jiným aplikacím (nazývaným [Klienti automatizace](../mfc/automation-clients.md)). Automatizační servery se někdy nazývají komponenty automatizace.

Vystavení automatizačních objektů umožňuje klientům automatizovat určité postupy přímým přístupem k objektům a funkcím, které server zpřístupňuje. Vystavení objektů tímto způsobem je výhodné, když aplikace poskytují funkce, které jsou užitečné pro ostatní aplikace. Textový procesor může například vystavit svou funkci kontroly pravopisu, aby ho mohli používat ostatní programy. Vystavení objektů umožní dodavatelům zlepšit funkce aplikací pomocí předem připravených funkcí jiných aplikací.

Tyto automatizační objekty mají vlastnosti a metody jako jejich externí rozhraní. Vlastnosti jsou pojmenované atributy objektu automatizace. Vlastnosti jsou podobné datovým členům C++ třídy. Metody jsou funkce, které fungují na automatizačních objektech. Metody jsou jako veřejné členské funkce C++ třídy.

> [!NOTE]
>  I když jsou vlastnosti C++ jako datové členy, nejsou přímo přístupné. Pro zajištění transparentního přístupu nastavte interní proměnnou v objektu Automation pomocí dvojice funkcí get/set členů pro přístup k nim.

Díky vystavení funkcionality aplikace pomocí společného, dobře definovaného rozhraní umožňuje automatizace sestavovat aplikace v jednom obecném programovacím jazyce, jako je Microsoft Visual Basic, nikoli v různých makrech specifických pro aplikace. jazyky.

##  <a name="_core_support_for_automation_servers"></a>Podpora pro automatizační servery

Visual C++ a MFC Framework poskytují rozsáhlou podporu pro automatizační servery. Zpracovávají značnou režii při vytváření automatizačního serveru, takže se můžete zaměřit na své úsilí na funkčnost aplikace.

Hlavním mechanismem rozhraní pro podporu automatizace je mapa odeslání, sada maker, která se rozbalí do deklarací a volání potřebných k vystavení metod a vlastností pro OLE. Typická mapa odeslání vypadá takto:

[!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/cpp/automation-servers_1.cpp)]

[Průvodce třídami](reference/mfc-class-wizard.md) a zobrazení tříd pomáhat při údržbě map odesílání. Když do třídy přidáte novou metodu nebo vlastnost, Visual Studio přidá odpovídající `DISP_FUNCTION` nebo `DISP_PROPERTY` makro s parametry, které označují název třídy, externí a interní názvy metody nebo vlastnosti a datové typy.

Dialogové okno **Přidat třídu** také zjednodušuje deklaraci tříd automatizace a správu jejich vlastností a operací. Když použijete dialogové okno Přidat třídu pro přidání třídy do projektu, zadáte svou základní třídu. Pokud základní třída umožňuje automatizaci, dialogové okno Přidat třídu zobrazí ovládací prvky, které slouží k určení, zda má nová třída podporovat automatizaci, zda je "OLE" vytvořitelné (to znamená, zda lze objekty třídy vytvořit v požadavku z klienta modelu COM). a externí název klienta modelu COM, který chcete použít.

Dialogové okno **Přidat třídu** potom vytvoří deklaraci třídy, včetně vhodných maker pro funkce OLE, které jste zadali. Přidává také kostru kódu pro implementaci členských funkcí vaší třídy.

Průvodce aplikací knihovny MFC zjednodušuje kroky spojené s tím, že aplikace Automation Server je mimo zemi. Pokud zaškrtnete políčko **Automatizace** na stránce **Pokročilé funkce** , Průvodce aplikací knihovny MFC přidá do `InitInstance` funkce aplikace volání požadovaná k registraci objektů automatizace a spuštění aplikace jako Automatizační server.

### <a name="what-do-you-want-to-do"></a>Co chcete udělat

- [Další informace o klientech automatizace](../mfc/automation-clients.md)

- [Další informace o třídě CCmdTarget](../mfc/reference/ccmdtarget-class.md)

- [Další informace o třídě COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)

## <a name="see-also"></a>Viz také:

[Automatizace](../mfc/automation.md)<br/>
[MFC – průvodce aplikací](../mfc/reference/mfc-application-wizard.md)
