---
title: Automatizační servery
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
ms.openlocfilehash: 0c7f3a3bd37c5f7f5696de363aa646f5376f4e75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468793"
---
# <a name="automation-servers"></a>Automatizační servery

Automatizace umožňuje aplikaci k manipulaci s objekty, které jsou implementovány v jiné aplikaci, nebo ke zveřejnění objekty, lze manipulovat. Server služby Automation je aplikace, která zveřejňuje programovatelné objekty (označované jako objekty automatizace) k ostatním aplikacím (volá [klientům automatizace](../mfc/automation-clients.md)). Automatizační servery jsou někdy označovány jako součásti služby Automation.

Zveřejnění objekty automatizace umožňuje klientům k automatizaci některých postupů přímým přístupem objekty a funkce serveru zpřístupňuje. Zveřejnění objekty tímto způsobem je vhodné v případě aplikace poskytují funkce, které jsou užitečné pro jiné aplikace. Například textový procesor může zveřejnit funkčnost kontrolu pravopisu, tak, aby mohou použít jiné programy. Vystavení objektů tak umožňuje dodavatelům zlepšit funkčnost svých aplikací s použitím předdefinované funkce jiných aplikací.

Tyto objekty automatizace mají vlastnosti a metody jako jejich externí rozhraní. Vlastnosti jsou pojmenovaných atributů objektu automatizace. Vlastnosti jsou podobné datové členy třídy jazyka C++. Metody jsou funkce, které fungují na objekty automatizace. Metody jsou stejně jako veřejné členské funkce třídy jazyka C++.

> [!NOTE]
>  I když jsou vlastnosti jako C++ datové členy, nejsou přímo přístupné. Pokud chcete poskytnout transparentní přístup, nastavení pro přístup k nim interní proměnné v automatizační objekt s párem členské funkce get/set.

Zveřejněním funkčnost aplikace přes běžné, dobře definovaných rozhraní automatizace díky tomu je možné vytvářet aplikace v jedné Obecné programovací jazyk jako je Microsoft Visual Basicu místo v různých, specifické pro aplikaci – makro jazyky.

##  <a name="_core_support_for_automation_servers"></a> Podpora pro automatizační servery

Visual C++ a rozhraní MFC framework poskytuje rozsáhlou podporu u automatizačních serverů. Velká část režiím zapojených při vytvoření serveru automatizace, abyste se mohli soustředit své úsilí na funkcích aplikace zpracovávají.

V rámci hlavní mechanismus pro podporu automatizace je mapa odeslání, sadu makra, která rozšíří na deklarace a volání potřeba zpřístupnit metody a vlastnosti pro OLE. Mapa odeslání typické vypadá takto:

[!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/cpp/automation-servers_1.cpp)]

V okně Vlastnosti a zobrazení tříd pomůcku pro zachování expediční mapy. Když přidáte novou metodu nebo vlastnost třídy, Visual C++ přidá odpovídající `DISP_FUNCTION` nebo `DISP_PROPERTY` makru s parametry určující název třídy, externí a interní názvy typů metodu nebo vlastnost a data.

**Přidat třídu** dialogové okno zjednodušuje i deklaraci třídy automatizace a řízení jejich vlastností a operací. Při přidání třídy do projektu použijete dialogové okno Přidat třídu, zadejte její základní třídě. Pokud základní třída umožňuje automatizaci, zobrazí se dialogové okno Přidat třídu ovládací prvky, které se používá k určení, zda by měl novou třídu podporu automatizace, ať už jde o "OLE vytvořitelné" (to znamená, zda objekty třídy se dají vytvořit na žádosti od klientů modelu COM) a název externí klienti modelu COM, měli používat.

**Přidat třídu** dialogové okno vytvoří deklaraci třídy, včetně makra vhodná pro OLE obsahuje jste zadali. Přidá také kostru kód pro implementaci členských funkcí vaší třídy.

Průvodce aplikací MFC zjednodušuje kroky při získávání vaší aplikaci automatizačního serveru firmu. Pokud vyberete **automatizace** zaškrtnutí políčka **rozšířené funkce** stránce, Průvodce aplikací MFC přidá do vaší aplikace `InitInstance` volání požadovaných k registraci vaší automatizace funkcí objekty, a spusťte aplikaci jako server automatizace.

### <a name="what-do-you-want-to-do"></a>Co chcete udělat

- [Další informace o klientech služby Automation](../mfc/automation-clients.md)

- [Další informace o CCmdTarget – třída](../mfc/reference/ccmdtarget-class.md)

- [Další informace o třídě COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)

## <a name="see-also"></a>Viz také

[Automatizace](../mfc/automation.md)<br/>
[MFC – průvodce aplikací](../mfc/reference/mfc-application-wizard.md)

