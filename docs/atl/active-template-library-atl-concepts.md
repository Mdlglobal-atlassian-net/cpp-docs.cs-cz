---
title: Koncepty Active Template Library (ATL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bb07807934dcc5c665f0058ef869f62f0b2d3ea
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755421"
---
# <a name="active-template-library-atl-concepts"></a>Koncepty knihovny ATL (Active Template Library)

Aktivní šablony knihovny (ATL) je sada šablonových tříd jazyka C++ a, které vám umožňují vytvořit malé, rychlé objekty modelu COM (Component Object). Má zvláštní podporu pro klíčové funkce modelu COM, včetně uložené implementace, duální rozhraní, standardní rozhraní čítače modelu COM, spojovací body, odtržených rozhraní a ovládací prvky ActiveX.

Pokud provedete mnoho programování knihovny ATL, můžete další informace o atributech, nová funkce v aplikaci Visual C++ .NET, který je navržené pro zjednodušení programování v modelu COM. Další informace najdete v tématu [programování s přidělenými atributy](../windows/attributed-programming-concepts.md).

## <a name="in-this-section"></a>V tomto oddílu

[ATL – tutoriál](../atl/active-template-library-atl-tutorial.md)  
Vás provede vytvořením ovládacího prvku a ukazuje některé ATL – principy vytváření v procesu.

[Úvod do modelu COM a knihovny ATL](../atl/introduction-to-com-and-atl.md)  
Představuje hlavní koncepty za modelu COM (Component Object). Tento článek také krátce vysvětluje, co je knihovny ATL a kdy byste měli použít.

[Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)  
Tento článek popisuje vztah mezi různými ATL – třídy a jak se implementují tyto třídy.

[Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)  
Popisuje duální rozhraní z hlediska ATL.

[ATL – kolekce a výčty](../atl/atl-collections-and-enumerators.md)  
Popisuje implementaci a vytvoření kolekce a výčty v knihovně ATL

[Principy vytváření složených prvků](../atl/atl-composite-control-fundamentals.md)  
Poskytuje podrobné pokyny pro vytvoření složeného ovládacího prvku. Složený ovládací prvek je typu ovládacího prvku ActiveX, který může obsahovat další ovládací prvky ActiveX nebo ovládací prvky Windows.

[Nejčastější dotazy k používání kontejnerů ovládacích prvků v knihovně ATL](../atl/atl-control-containment-faq.md)  
Popisuje základní otázky související s hostování ovládacích prvků s knihovnou ATL.

[ATL COM – stránky vlastností](../atl/atl-com-property-pages.md)  
Ukazuje, jak určit a implementovat com – stránky vlastností.

[ATL – podpora ovládacích prvků DHTML](../atl/atl-support-for-dhtml-controls.md)  
Obsahuje podrobné pokyny pro vytvoření ovládacího prvku DHTML.

[ATL – body připojení](../atl/atl-connection-points.md)  
Vysvětluje, co jsou spojovací body a jak je ATL implementuje.

[Zpracování událostí a ATL](../atl/event-handling-and-atl.md)  
Popisuje kroky, které musíte provést pro zpracování událostí modelu COM s použitím ATL [IDispEventImpl](../atl/reference/idispeventimpl-class.md) a [idispeventsimpleimpl –](../atl/reference/idispeventsimpleimpl-class.md) třídy.

[ATL a volné zařazování vláken](../atl/atl-and-the-free-threaded-marshaler.md)  
Poskytuje podrobné informace o ATL Průvodce jednoduchým objektem na možnost, která umožňuje vaší třídy k agregaci volné zařazování vláken (FTM).

[Určení modelu vláken projektu](../atl/specifying-the-threading-model-for-a-project-atl.md)  
Popisuje makra, které jsou dostupné pro řízení výkonu související s dělení na vlákna ve vašem projektu.

[ATL – třídy modulů](../atl/atl-module-classes.md)  
Tento článek popisuje nové třídy modulu pro knihovny ATL 7.0. Třídy modulů implementaci základních funkcí vyžaduje ATL.

[Služby ATL](../atl/atl-services.md)  
Obsahuje řadu událostí, ke kterým dochází při implementaci služby. Také hovoří o tom, některé koncepty související s vývojem služby.

[ATL – třídy oken](../atl/atl-window-classes.md)  
Popisuje postup vytvoření, nadřazené třídy a podtřídu windows v knihovně ATL ATL – třídy oken nejsou tříd modelu COM.

[ATL – třídy kolekce](../atl/atl-collection-classes.md)  
Popisuje způsob použití pole a mapuje v knihovně ATL

[Komponenta knihovny ATL registru (Registrar)](../atl/atl-registry-component-registrar.md)  
Tento článek popisuje ATL skriptování syntaxi a nahraditelné parametry. Také vysvětluje, jak nastavit statickou odkaz na doménový Registrátor.

[Programování s použitím knihovny ATL a běhového kódu jazyka C](../atl/programming-with-atl-and-c-run-time-code.md)  
Tento článek popisuje výhody propojení staticky nebo dynamicky do knihovny Run-Time C (CRT).

[Programování pomocí třídy CComBSTR](../atl/programming-with-ccombstr-atl.md)  
Tento článek popisuje několik situací, které vyžadují opatrní při programování s `CComBSTR`.

[Referenční dokumentace ke kódování](../atl/atl-encoding-reference.md)  
Poskytuje funkce a makra, které podporují kódování v celou řadu běžných standardů aplikace Internet například uuencode šestnáctkové a UTF8 atlenc.h.

[Referenční dokumentace k nástrojům](../atl/atl-utilities-reference.md)  
Poskytuje kód pro práci s cestami a adresy URL ve formě [cpatht –](../atl/reference/cpatht-class.md) a [CUrl](../atl/reference/curl-class.md). Fondu vláken, [cthreadpool –](../atl/reference/cthreadpool-class.md), lze použít ve svých vlastních aplikacích. Tento kód lze nalézt v atlpath.h a atlutil.h.

## <a name="related-sections"></a>Související oddíly

[Ukázky knihovny ATL](../visual-cpp-samples.md)  
Poskytuje popisy a odkazy na knihovny ATL ukázkové programy.

[Vytvoření projektu ATL](../atl/reference/creating-an-atl-project.md)  
Obsahuje informace o Průvodce projektem ATL.

[Průvodce ovládacími prvky ATL](../atl/reference/atl-control-wizard.md)  
Popisuje, jak přidat třídy.

[Programování s atributy](../windows/attributed-programming-concepts.md)  
Poskytuje přehled o použití atributů pro zjednodušení programování v modelu COM plus seznam obsahuje odkazy na podrobnější témata.

[Přehled třídy ATL](../atl/atl-class-overview.md)  
Poskytuje referenční informace a odkazy na ATL – třídy.

