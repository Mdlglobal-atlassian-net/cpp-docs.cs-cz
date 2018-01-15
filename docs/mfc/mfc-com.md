---
title: MFC COM | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MFC COM (MFC)
dev_langs: C++
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 827bef034eeb7fc46b397c50f5ddf0c4cb6e48fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-com"></a>MFC COM
Podmnožinu MFC slouží k podpory modelu COM, zatímco většina Active šablony Library (ATL) slouží pro programování COM. Témata v této části popisuje podporu pro knihovny MFC pro COM.  
  
 Technologie Active (například ActiveX – ovládací prvky, obsahování pro aktivní dokument, OLE a tak dále) použít k povolení softwarové součásti pro vzájemné interakce v síťovém prostředí, bez ohledu na jazyk, se kterým byly modelu COM (Component Object) vytvořit. Technologie Active slouží k vytvoření aplikace, které běží na ploše nebo Internet. Další informace najdete v části [Úvod do modelu COM](../atl/introduction-to-com.md) nebo [The Component Object Model](http://msdn.microsoft.com/library/windows/desktop/ms694363).  
  
 Technologie Active patří klient i server technologií, včetně následujících:  
  
-   [Obsahování pro aktivní dokument](../mfc/active-document-containment.md), podporované ve verzích MFC 4.2 a novější, umožňuje uživatelům zobrazit [aktivní dokumenty](../mfc/active-documents.md) (například soubory aplikace Microsoft Excel nebo Word) a aktivujte rozhraní celého dokumentu nativní aplikace v oblasti celého klientského [kontejner pro aktivní dokument](../mfc/active-document-containers.md) například vazač Microsoft Office nebo aplikace Microsoft Internet Explorer. Kontejnery fungovat jako klienti, když dokumenty jsou poskytovány [servery pro aktivní dokumenty](../mfc/active-document-servers.md). Další informace o použití aktivní dokumenty v internetových aplikací najdete v tématu: [aktivní dokumenty na Internetu](../mfc/active-documents-on-the-internet.md).  
  
-   ActiveX – ovládací prvky jsou interaktivní objekty, které mohou být používány kontejnery, jako jsou webu. Další informace pro ovládací prvky ActiveX najdete v tématu:  
  
    -   [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)  
  
    -   [Ovládací prvky ActiveX na internetu](../mfc/activex-controls-on-the-internet.md)  
  
    -   [Přehled: Internet](../mfc/mfc-internet-programming-basics.md)  
  
    -   [Upgrade existujícího ovládacího prvku ActiveX k použití na Internetu](../mfc/upgrading-an-existing-activex-control.md)  
  
    -   [Ladění ovládacího prvku ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)  
  
-   Aktivní skriptování řídí chování integrované jeden nebo více ovládacích prvků ActiveX z prohlížeče nebo serveru. Další informace o aktivní skriptování najdete v tématu [technologie Active na Internetu](../mfc/active-technology-on-the-internet.md).  
  
-   [Automatizace](../mfc/automation.md) (dříve označované jako automatizace OLE) umožňuje pro jednu aplikaci k manipulaci s objekty, které jsou implementovány v jiné aplikaci, nebo "vystavit" objekty, budou se dá upravit.  
  
     Automatizované objekt může být místní nebo [vzdáleného](../mfc/remote-automation.md) (na jiném počítači přístupné přes síť). Automatizace je k dispozici pro objekty OLE a COM.  
  
-   Tato část také obsahuje informace o tom, jak psát komponenty modelu COM v MFC, například [spojovací body](../mfc/connection-points.md).  
  
 Informace o co stále nese OLE a co se nyní označuje jako technologie active, najdete v tématech na [OLE](../mfc/ole-in-mfc.md).  
  
 Navíc najdete v článku znalostní báze Knowledge Base Q248019: postupy: zabránit Server zaneprázdněn dialogové okno pole z zobrazování během náročná COM operace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zahrnutí aktivního dokumentu](../mfc/active-document-containment.md)  
  
 [Automatizace](../mfc/automation.md)  
  
 [Vzdálená automatizace](../mfc/remote-automation.md)  
  
 [Body připojení](../mfc/connection-points.md)  
  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../mfc/mfc-concepts.md)

