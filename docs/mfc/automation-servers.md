---
title: Automatizační servery | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 337d5a1ec25e8fc80cf867aecef0452b1d03fb2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="automation-servers"></a>Automatizační servery
Automatizace umožňuje aplikaci k manipulaci s objekty, které jsou implementovány v jiné aplikaci, nebo je vystavit objekty, budou se dá upravit. Automatizační server je aplikace, která zveřejňuje programovatelný objekty (označovaný jako objekty automatizace) k ostatním aplikacím (nazývá [klienti automatizace](../mfc/automation-clients.md)). Automatizační servery se někdy označuje jako komponenty pro automatizaci.  
  
 Vystavení objekty automatizace umožňuje klientům automatizovat některé postupy tak, že přímý přístup k objektům a zpřístupní funkce serveru. Vystavení objektů tímto způsobem je užitečné, když aplikace poskytují funkce, které jsou užitečné pro jiné aplikace. Například textový editor mohou být vystaveny jeho funkce pro kontrolu pravopisu tak, aby ho může použít jiné programy. Vystavení objektů proto umožňuje dodavatelům ke zlepšení funkce svých aplikacích pomocí připravených funkce jiných aplikací.  
  
 Tyto objekty automatizace mají vlastnosti a metody jako jejich externí rozhraní. Vlastnosti jsou pojmenovaných atributů objektu automatizace. Vlastnosti jsou stejné jako datové členy třídy C++. Metody jsou funkce, které fungují na objekty automatizace. Metody jsou stejné jako veřejné členské funkce třídy C++.  
  
> [!NOTE]
>  I když jsou vlastnosti jako C++ datových členů, nejsou přímo přístupné. Zajistit transparentní přístup, nastavte pro přístup k nim interní proměnné v objektu automatizace dvojice get/set členských funkcí.  
  
 Díky zpřístupnění funkcí aplikace pomocí běžných, dobře definované rozhraní, Automation umožňuje vytvářet aplikace v jednom Obecné programovací jazyk jako Microsoft Visual Basicu místo v různých, specifické pro aplikaci – makro jazyky.  
  
##  <a name="_core_support_for_automation_servers"></a> Podpora pro automatizační servery  
 Visual C++ a rozhraní MFC framework poskytuje rozsáhlou podporu pro automatizační servery. Jejich zpracování mnohem režie spojená při vytvoření serveru automatizace, abyste se mohli zaměřit vaše úsilí na funkci aplikace.  
  
 Rozhraní framework hlavní mechanismus pro podporu automatizace je odesílání mapa sadu makra, která rozšíří na deklarace a volání, které jsou potřebné ke zveřejnění metod a vlastností pro OLE. Mapy odesílání typické vypadá takto:  
  
 [!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/cpp/automation-servers_1.cpp)]  
  
 Vlastnosti – okno a zobrazení tříd usnadní zachování expediční mapy. Když přidáte nové metody nebo vlastnosti na třídu, Visual C++ přidá odpovídající `DISP_FUNCTION` nebo `DISP_PROPERTY` s parametry, která udává název třídy, externí i interní názvy metody nebo vlastnosti a datové typy.  
  
 **Přidat třídu** dialogové okno zjednodušuje i deklaraci třídy automatizace a řízení operací a jejich vlastnosti. Při pomocí dialogové okno Přidat třídu do projektu přidejte třídu, zadejte její základní třída. Pokud základní třída umožňuje automatizace, dialogové okno Přidat třídu zobrazí ovládací prvky, které se používá k určení, zda nová třída musí podporovat automatizace, jestli je "OLE vytvořitelné" (to znamená, zda objekty třídy lze vytvářet na vyžádání z klienta COM) a externí název klienta COM k použití.  
  
 **Přidat třídu** dialogové okno vytvoří deklaraci třídy, včetně příslušné makra pro OLE funkce zadali. Také přidá kostru kód pro implementaci třídy a členské funkce.  
  
 Průvodce aplikací MFC usnadňuje získávání vaše serverová aplikace automatizace vypnout základů kroky. Pokud jste vybrali **automatizace** zaškrtnutí políčka **upřesňující funkce** stránky, Průvodce aplikací MFC přidá do vaší aplikace `InitInstance` funkce volání k registraci vaší automatizace požadován objekty a spusťte aplikaci jako serveru automatizace.  
  
### <a name="what-do-you-want-to-do"></a>Co chcete udělat  
  
-   [Další informace o klienti automatizace](../mfc/automation-clients.md)  
  
-   [Další informace o CCmdTarget – třída](../mfc/reference/ccmdtarget-class.md)  
  
-   [Další informace o třídě COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)  
  
## <a name="see-also"></a>Viz také  
 [Automatizace](../mfc/automation.md)   
 [MFC – průvodce aplikací](../mfc/reference/mfc-application-wizard.md)

