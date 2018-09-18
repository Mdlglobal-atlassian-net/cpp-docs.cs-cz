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
ms.openlocfilehash: 554fddbb778a19555fc7342f08eaac2e5642d815
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019442"
---
# <a name="active-template-library-atl-concepts"></a>Koncepty knihovny ATL (Active Template Library)

Aktivní šablony knihovny (ATL) je sada šablonových tříd jazyka C++ a, které vám umožňují vytvořit malé, rychlé objekty modelu COM (Component Object). Má zvláštní podporu pro klíčové funkce modelu COM, včetně uložené implementace, duální rozhraní, standardní rozhraní čítače modelu COM, spojovací body, odtržených rozhraní a ovládací prvky ActiveX.

Pokud provedete mnoho programování knihovny ATL, můžete další informace o atributech, nová funkce v aplikaci Visual C++ .NET, který je navržené pro zjednodušení programování v modelu COM. Další informace najdete v tématu [programování s přidělenými atributy](../windows/attributed-programming-concepts.md).

## <a name="in-this-section"></a>V tomto oddílu

[ATL – tutoriál](../atl/active-template-library-atl-tutorial.md)<br/>
Vás provede vytvořením ovládacího prvku a ukazuje některé ATL – principy vytváření v procesu.

[Úvod do modelu COM a knihovny ATL](../atl/introduction-to-com-and-atl.md)<br/>
Představuje hlavní koncepty za modelu COM (Component Object). Tento článek také krátce vysvětluje, co je knihovny ATL a kdy byste měli použít.

[Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)<br/>
Tento článek popisuje vztah mezi různými ATL – třídy a jak se implementují tyto třídy.

[Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)<br/>
Popisuje duální rozhraní z hlediska ATL.

[ATL – kolekce a výčty](../atl/atl-collections-and-enumerators.md)<br/>
Popisuje implementaci a vytvoření kolekce a výčty v knihovně ATL

[Principy vytváření složených prvků](../atl/atl-composite-control-fundamentals.md)<br/>
Poskytuje podrobné pokyny pro vytvoření složeného ovládacího prvku. Složený ovládací prvek je typu ovládacího prvku ActiveX, který může obsahovat další ovládací prvky ActiveX nebo ovládací prvky Windows.

[Nejčastější dotazy k používání kontejnerů ovládacích prvků v knihovně ATL](../atl/atl-control-containment-faq.md)<br/>
Popisuje základní otázky související s hostování ovládacích prvků s knihovnou ATL.

[ATL COM – stránky vlastností](../atl/atl-com-property-pages.md)<br/>
Ukazuje, jak určit a implementovat com – stránky vlastností.

[ATL – podpora ovládacích prvků DHTML](../atl/atl-support-for-dhtml-controls.md)<br/>
Obsahuje podrobné pokyny pro vytvoření ovládacího prvku DHTML.

[ATL – body připojení](../atl/atl-connection-points.md)<br/>
Vysvětluje, co jsou spojovací body a jak je ATL implementuje.

[Zpracování událostí a ATL](../atl/event-handling-and-atl.md)<br/>
Popisuje kroky, které musíte provést pro zpracování událostí modelu COM s použitím ATL [IDispEventImpl](../atl/reference/idispeventimpl-class.md) a [idispeventsimpleimpl –](../atl/reference/idispeventsimpleimpl-class.md) třídy.

[ATL a volné zařazování vláken](../atl/atl-and-the-free-threaded-marshaler.md)<br/>
Poskytuje podrobné informace o ATL Průvodce jednoduchým objektem na možnost, která umožňuje vaší třídy k agregaci volné zařazování vláken (FTM).

[Určení modelu vláken projektu](../atl/specifying-the-threading-model-for-a-project-atl.md)<br/>
Popisuje makra, které jsou dostupné pro řízení výkonu související s dělení na vlákna ve vašem projektu.

[ATL – třídy modulů](../atl/atl-module-classes.md)<br/>
Tento článek popisuje nové třídy modulu pro knihovny ATL 7.0. Třídy modulů implementaci základních funkcí vyžaduje ATL.

[Služby ATL](../atl/atl-services.md)<br/>
Obsahuje řadu událostí, ke kterým dochází při implementaci služby. Také hovoří o tom, některé koncepty související s vývojem služby.

[ATL – třídy oken](../atl/atl-window-classes.md)<br/>
Popisuje postup vytvoření, nadřazené třídy a podtřídu windows v knihovně ATL ATL – třídy oken nejsou tříd modelu COM.

[ATL – třídy kolekce](../atl/atl-collection-classes.md)<br/>
Popisuje způsob použití pole a mapuje v knihovně ATL

[Komponenta knihovny ATL registru (Registrar)](../atl/atl-registry-component-registrar.md)<br/>
Tento článek popisuje ATL skriptování syntaxi a nahraditelné parametry. Také vysvětluje, jak nastavit statickou odkaz na doménový Registrátor.

[Programování s použitím knihovny ATL a běhového kódu jazyka C](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
Tento článek popisuje výhody propojení staticky nebo dynamicky do knihovny Run-Time C (CRT).

[Programování pomocí třídy CComBSTR](../atl/programming-with-ccombstr-atl.md)<br/>
Tento článek popisuje několik situací, které vyžadují opatrní při programování s `CComBSTR`.

[Referenční dokumentace ke kódování](../atl/atl-encoding-reference.md)<br/>
Poskytuje funkce a makra, které podporují kódování v celou řadu běžných standardů aplikace Internet například uuencode šestnáctkové a UTF8 atlenc.h.

[Referenční dokumentace k nástrojům](../atl/atl-utilities-reference.md)<br/>
Poskytuje kód pro práci s cestami a adresy URL ve formě [cpatht –](../atl/reference/cpatht-class.md) a [CUrl](../atl/reference/curl-class.md). Fondu vláken, [cthreadpool –](../atl/reference/cthreadpool-class.md), lze použít ve svých vlastních aplikacích. Tento kód lze nalézt v atlpath.h a atlutil.h.

## <a name="related-sections"></a>Související oddíly

[Ukázky knihovny ATL](../visual-cpp-samples.md)<br/>
Poskytuje popisy a odkazy na knihovny ATL ukázkové programy.

[Vytvoření projektu ATL](../atl/reference/creating-an-atl-project.md)<br/>
Obsahuje informace o Průvodce projektem ATL.

[Průvodce ovládacími prvky ATL](../atl/reference/atl-control-wizard.md)<br/>
Popisuje, jak přidat třídy.

[Programování s atributy](../windows/attributed-programming-concepts.md)<br/>
Poskytuje přehled o použití atributů pro zjednodušení programování v modelu COM plus seznam obsahuje odkazy na podrobnější témata.

[Přehled třídy ATL](../atl/atl-class-overview.md)<br/>
Poskytuje referenční informace a odkazy na ATL – třídy.

