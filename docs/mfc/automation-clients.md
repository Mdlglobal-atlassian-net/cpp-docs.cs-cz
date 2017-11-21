---
title: Klienti automatizace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5c239aa86921f00e9f25a9960451a4c15586d74d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="automation-clients"></a>Klienti automatizace
Automatizace umožňuje aplikaci k manipulaci s objekty, které jsou implementovány v jiné aplikaci, nebo je vystavit objekty, budou se dá upravit. Klientem automatizace je aplikace, která můžete upravit zveřejněné objekty, které patří do jiné aplikace. Automatizační server se nazývá aplikaci, která poskytuje objekty. Klient umožňuje pracovat s objekty aplikací serveru díky přístupu k těmto objektům vlastnosti a funkce.  
  
### <a name="types-of-automation-clients"></a>Typy klientů automatizace  
 Existují dva typy klienti automatizace:  
  
-   Klienti, kteří dynamicky (za běhu) získat informace o vlastnostech a operací serveru.  
  
-   Klienti, kteří budou mít statické informací (uvedených v době kompilace), který určuje vlastnosti a operací serveru.  
  
 Klienti první druhu získat informace o metody a vlastnosti serveru dotazováním systému OLE `IDispatch` mechanismus. I když je vhodné použít pro dynamické klienty `IDispatch` je obtížné používat pro statické klienty, které objekty se řídí musí být známo v doba kompilace. Pro statické vázaný klienty, zadejte třídy Microsoft Foundation [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md) třídy.  
  
 Statické vázané klienti používat třídu proxy, který je staticky propojené s klientskou aplikaci. Tato třída poskytuje zapouzdření C++ bezpečnost typů vlastností a operace serverová aplikace.  
  
 Třída `COleDispatchDriver` poskytuje hlavní podporu automatizace na straně klienta. Pomocí `Add New Item` dialogové okno, vytváření třídy odvozené od `COleDispatchDriver`.  
  
 Potom zadejte soubor knihovny typů popisující vlastnosti a funkce serveru aplikační objekt. Dialogové okno Přidat položku čte tento soubor a vytvoří `COleDispatchDriver`-odvozené třídy s členské funkce, které aplikace můžete volat k způsobem typově bezpečný přístup k objektům serverová aplikace v jazyce C++. Další funkce zděděno z `COleDispatchDriver` zjednodušuje proces volání správné automatizační server.  
  
### <a name="handling-events-in-automation-clients"></a>Zpracování událostí v klienti automatizace  
 Pokud chcete ke zpracování událostí ve vašeho klienta automatizace, je nutné přidat podřízený rozhraní. MFC poskytuje podporu průvodce Přidat podřízený rozhraní pro ovládací prvky ActiveX, ale pro další servery COM nepodporuje. Informace o tom, jak přidat podřízený rozhraní MFC klientovi pro zdroje rozhraní popsané COM servery v najdete v tématu Postupy: vytváření rozhraní jímka v klientovi COM MFC-Based (KB 181845) v [http://support.microsoft.com/default.aspxscid=kb;en-us; 181845](http://support.microsoft.com/default.aspxscid=kb;en-us;181845).  
  
## <a name="see-also"></a>Viz také  
 [Klienti automatizace: Použití knihoven typů](../mfc/automation-clients-using-type-libraries.md)   
 [Automatizace](../mfc/automation.md)   
 [MFC – Průvodce aplikací](../mfc/reference/mfc-application-wizard.md)

