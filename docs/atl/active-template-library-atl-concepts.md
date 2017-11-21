---
title: Koncepty Active Template Library (ATL) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 01bd114c92b7056ead29b57c70801d2cbbacb554
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="active-template-library-atl-concepts"></a>Koncepty knihovny ATL (Active Template Library)
Aktivní šablony Library (ATL) je sada na základě šablon C++ třídy, které vám umožní vytvořit malé, rychlé objekty modelu COM (Component Object). Má speciální podporu klíče COM funkcí, včetně uložených implementace, duální rozhraní, standardní rozhraní pro výčty COM, spojovací body, úplné vypnutí rozhraní a ovládací prvky ActiveX.  
  
 Pokud uděláte spoustu ATL programování, můžete další informace o atributech, nová funkce v aplikaci Visual C++ .NET, který je navržený tak, aby se zjednodušila programování COM. Další informace najdete v tématu [programování s atributy](../windows/attributed-programming-concepts.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ATL – tutoriál](../atl/active-template-library-atl-tutorial.md)  
 Vás provede vytvoření ovládacího prvku a ukazuje základy některé knihovny ATL v procesu.  
  
 [Úvod do modelu COM a knihovny ATL](../atl/introduction-to-com-and-atl.md)  
 Představuje hlavní koncepty za modelu COM (Component Object). Tento článek také krátce vysvětluje, co je ATL a kdy byste měli použít.  
  
 [Základy ATL COM – objekty](../atl/fundamentals-of-atl-com-objects.md)  
 Popisuje vztah mezi různé třídy ATL a jak jsou implementované tyto třídy.  
  
 [Duální rozhraní a knihovny ATL](../atl/dual-interfaces-and-atl.md)  
 Duální rozhraní z hlediska ATL popisuje.  
  
 [ATL – kolekce a výčty](../atl/atl-collections-and-enumerators.md)  
 Popisuje provádění a vytvoření kolekce a výčty v ATL.  
  
 [Principy vytváření složených prvků](../atl/atl-composite-control-fundamentals.md)  
 Poskytuje podrobné pokyny pro vytvoření složeného ovládacího prvku. Složeného ovládacího prvku je typ ovládacího prvku ActiveX, který může obsahovat další ovládací prvky ActiveX nebo ovládací prvky systému Windows.  
  
 [Uzavření ovládacího prvku ATL – nejčastější dotazy](../atl/atl-control-containment-faq.md)  
 Popisuje základní otázky související s hostování ovládacích prvků s ATL.  
  
 [ATL COM – stránky vlastností](../atl/atl-com-property-pages.md)  
 Ukazuje, jak určit a implementovat COM – stránky vlastností.  
  
 [ATL – podpora pro ovládací prvky jazyka DHTML](../atl/atl-support-for-dhtml-controls.md)  
 Poskytuje podrobné pokyny pro vytvoření ovládacího prvku DHTML.  
  
 [ATL – body připojení](../atl/atl-connection-points.md)  
 Vysvětluje, co jsou spojovací body a jak je ATL implementuje.  
  
 [Zpracování událostí a ATL](../atl/event-handling-and-atl.md)  
 Popisuje kroky, které je třeba provést při zpracování událostí modelu COM pomocí knihovny ATL pro [IDispEventImpl](../atl/reference/idispeventimpl-class.md) a [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) třídy.  
  
 [ATL a volné zařazování vláken](../atl/atl-and-the-free-threaded-marshaler.md)  
 Poskytuje podrobné informace o ATL Simple Object Wizard na možnost, která umožňuje třídě k agregaci volné zařazování vláken (FTM).  
  
 [Určení modelu vláken pro projekt](../atl/specifying-the-threading-model-for-a-project-atl.md)  
 Popisuje makra, které jsou dostupné pro řízení běhu výkonu související s dělení na vlákna ve vašem projektu.  
  
 [ATL – třídy modulů](../atl/atl-module-classes.md)  
 Popisuje nové modulu třídy pro ATL 7.0. Třídy modulů implementaci základních funkcí vyžaduje ATL.  
  
 [Služby ATL](../atl/atl-services.md)  
 Popisuje řadu událostí, které nastat, pokud je implementován. Také hovoří o některé pojmy týkající se vývoje služby.  
  
 [ATL – třídy oken](../atl/atl-window-classes.md)  
 Popisuje postup vytvoření, supertřídě a podtřídami windows v ATL. Třídy oken ATL nejsou třídy COM.  
  
 [ATL – třídy kolekce](../atl/atl-collection-classes.md)  
 Popisuje, jak použít pole a mapy v ATL.  
  
 [Součást knihovny ATL registru (Registrar)](../atl/atl-registry-component-registrar.md)  
 Popisuje ATL skriptování syntaxe a nahraditelné parametry. Také vysvětluje, jak nastavit statickou odkaz registrátora.  
  
 [Programování s použitím knihovny ATL a běhového kódu jazyka C](../atl/programming-with-atl-and-c-run-time-code.md)  
 Popisuje výhody propojení staticky nebo dynamicky k běhové knihovny jazyka C (CRT).  
  
 [Programování pomocí třídy CComBSTR](../atl/programming-with-ccombstr-atl.md)  
 Popisuje několik situací, které vyžadují opatrní při programování s `CComBSTR`.  
  
 [Referenční dokumentace ke kódování](../atl/atl-encoding-reference.md)  
 Poskytuje funkcemi a makry podporující kódování řadu běžných Internetové standardy, jako je uuencode šestnáctkové, a UTF8 v atlenc.h.  
  
 [Referenční dokumentace k nástrojům](../atl/atl-utilities-reference.md)  
 Obsahuje kód pro manipulaci s cesty a adresy URL ve formě [CPathT](../atl/reference/cpatht-class.md) a [CUrl](../atl/reference/curl-class.md). Fondu vláken, [CThreadPool](../atl/reference/cthreadpool-class.md), lze v aplikaci. Tento kód lze nalézt v atlpath.h a atlutil.h.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ukázky knihovny ATL](../visual-cpp-samples.md)  
 Obsahuje popisy a odkazy na ATL ukázkové aplikace.  
  
 [Vytvoření projektu knihovny ATL](../atl/reference/creating-an-atl-project.md)  
 Obsahuje informace o Průvodci projektu knihovny ATL.  
  
 [Průvodce ovládacím prvkem knihovny ATL](../atl/reference/atl-control-wizard.md)  
 Popisuje, jak přidat třídy.  
  
 [Programování s atributy](../windows/attributed-programming-concepts.md)  
 Poskytuje přehled o používání atributů pro zjednodušení programování COM plus seznam odkazy na podrobnější témata.  
  
 [Přehled třídy ATL](../atl/atl-class-overview.md)  
 Poskytuje informace a odkazy na třídy ATL.

