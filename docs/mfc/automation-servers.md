---
title: Automatizační servery
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
ms.openlocfilehash: 391cb2f6ff5673296f40e21113e3a6510f71d475
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370837"
---
# <a name="automation-servers"></a>Automatizační servery

Automatizace umožňuje pro vaše aplikace manipulovat s objekty implementovanými v jiné aplikaci nebo vystavit objekty tak, aby s nimi bylo možné manipulovat. Automatizační server je aplikace, která zpřístupňuje programovatelné objekty (nazývané objekty automatizace) jiným aplikacím [(nazývaným klienti automatizace](../mfc/automation-clients.md)). Automatizační servery se někdy nazývají součásti automatizace.

Vystavení objektů automatizace umožňuje klientům automatizovat určité postupy přímým přístupem k objektům a funkcím, které server zpřístupní. Vystavení objektů tímto způsobem je výhodné, když aplikace poskytují funkce, které jsou užitečné pro jiné aplikace. Textový procesor může například vystavit jeho funkce kontroly pravopisu tak, aby ji mohly používat jiné programy. Expozice objektů tak umožňuje dodavatelům zlepšit funkčnost svých aplikací pomocí hotových funkcí jiných aplikací.

Tyto Automation objekty mají vlastnosti a metody jako jejich externí rozhraní. Vlastnosti jsou pojmenovány atributy Automation objektu. Vlastnosti jsou jako datové členy třídy C++. Metody jsou funkce, které pracují na objektech automatizace. Metody jsou jako veřejné členské funkce třídy C++.

> [!NOTE]
> Přestože vlastnosti jsou jako datové členy jazyka C++, nejsou přímo přístupné. Chcete-li zajistit transparentní přístup, nastavte interní proměnnou v objektu Automation s dvojicí členských funkcí get/set pro přístup k nim.

Vystavením funkce aplikace prostřednictvím společného, dobře definované rozhraní automatizace umožňuje vytvářet aplikace v jednom obecném programovacím jazyce, jako je Microsoft Visual Basic namísto v různých jazycích maker specifických pro aplikaci.

## <a name="support-for-automation-servers"></a><a name="_core_support_for_automation_servers"></a>Podpora automatizačních serverů

Visual C++ a rozhraní MFC poskytují rozsáhlou podporu pro automatizační servery. Zpracovávají velkou část režie, která se podílí na vytváření serveru automatizace, takže můžete své úsilí zaměřit na funkčnost vaší aplikace.

Hlavní mechanismus rozhraní pro podporu automatizace je odeslání mapy, sada maker, která se rozbalí do deklarací a volání potřebných k vystavení metody a vlastnosti ole. Typická mapa odeslání vypadá takto:

[!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/cpp/automation-servers_1.cpp)]

[Průvodce třídou](reference/mfc-class-wizard.md) a zobrazení tříd pomáhají při údržbě expedičních map. Když přidáte novou metodu nebo vlastnost do třídy, Visual Studio přidá odpovídající `DISP_FUNCTION` nebo `DISP_PROPERTY` makro s parametry označující název třídy, externí a interní názvy metody nebo vlastnosti a datové typy.

Dialogové okno **Přidat třídu** také zjednodušuje deklaraci tříd automatizace a správu jejich vlastností a operací. Při použití dialogového okna Přidat třídu k přidání třídy do projektu zadáte její základní třídu. Pokud základní třída umožňuje automatizaci, zobrazí se v dialogovém okně Přidat třídu ovládací prvky, které slouží k určení, zda má nová třída podporovat automatizaci, zda je "Ole creatable" (to znamená, zda lze objekty třídy vytvořit na žádost klienta modelu COM) a externí název pro klienta MODELU COM, který má být používán.

Dialogové okno **Přidat třídu** pak vytvoří deklaraci třídy, včetně příslušných maker pro zadané prvky OLE. Také přidá kód kostry pro implementaci členských funkcí vaší třídy.

Průvodce aplikací knihovny MFC zjednodušuje kroky spojené s tím, jak získat aplikaci automatizačního serveru ze země. Pokud zaškrtnete políčko **Automatizace** na stránce **Upřesnit funkce,** Průvodce `InitInstance` aplikací knihovny MFC přidá do funkce aplikace volání potřebná k registraci objektů Automation a spuštění aplikace jako serveru automatizace.

### <a name="what-do-you-want-to-do"></a>Co chcete dělat

- [Další informace o klientech automatizace](../mfc/automation-clients.md)

- [Další informace o třídě CCmdTarget](../mfc/reference/ccmdtarget-class.md)

- [Další informace o třídě COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)

## <a name="see-also"></a>Viz také

[Automation](../mfc/automation.md)<br/>
[MFC – průvodce aplikací](../mfc/reference/mfc-application-wizard.md)
