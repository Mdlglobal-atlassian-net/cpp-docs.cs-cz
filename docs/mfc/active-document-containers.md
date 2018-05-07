---
title: Kontejnery pro aktivní dokument | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a47db4f9715c539ecf9bcbfb78e48b7e8edbc94b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="active-document-containers"></a>Kontejnery pro aktivní dokument
Kontejner pro aktivní dokument, jako je například Microsoft Office Binder nebo Internet Exploreru umožňuje pracovat s jinou aplikaci typů v rámci jedné (namísto nutnosti vytvořit a použít více snímků aplikace pro každou několik dokumentů Typ dokumentu).  
  
 MFC plně podporuje kontejnery pro aktivní dokument v `COleDocObjectItem` třídy. Průvodce aplikací MFC můžete vytvořit kontejner výběrem **kontejner pro aktivní dokument** v zaškrtávací políčko **složené podporu dokumentu** stránky Průvodce aplikací MFC. Další informace najdete v tématu [vytvoření aplikace kontejnerů pro aktivní dokument](../mfc/creating-an-active-document-container-application.md).  
  
 Další informace o kontejnery pro aktivní dokument najdete v tématu:  
  
-   [Požadavky na kontejneru](#container_requirements)  
  
-   [Objekty dokumentu lokality](#document_site_objects)  
  
-   [Objekty zobrazení lokality](#view_site_objects)  
  
-   [Objekt rámce](#frame_object)  
  
-   [Slučování nabídek nápovědy](../mfc/help-menu-merging.md)  
  
-   [Tisk prostřednictvím kódu programu](../mfc/programmatic-printing.md)  
  
-   [Cíle příkazů](../mfc/message-handling-and-command-targets.md)  
  
##  <a name="container_requirements"></a> Požadavky na kontejneru  
 Podpora aktivního dokumentu v kontejner znamená více než jen implementace rozhraní: se také vyžaduje znalost pomocí rozhraní obsažený objekt. Totéž platí i pro aktivní dokument rozšíření, kde kontejneru musí také vědět, jak používat tyto rozšíření rozhraní na aktivní dokumenty sami.  
  
 Kontejner pro aktivní dokument, který se integruje aktivní dokumenty musí:  
  
-   Být umožňuje zpracovávat úložiště objektů prostřednictvím **IPersistStorage** rozhraní, to znamená, je nutné zadat `IStorage` instance pro každý aktivní dokument.  
  
-   Podporují základní funkce vnoření OLE – dokumenty, očekávání objekty "server", (jeden na každý dokument nebo vložení) implementující **IOleClientSite** a **IAdviseSink**.  
  
-   Podpora aktivace na místě vložené objekty nebo aktivní dokumenty. Musíte implementovat objekty lokality kontejneru `IOleInPlaceSite` a musíte zadat objekt rámečku kontejneru **IOleInPlaceFrame**.  
  
-   Podpora aktivní dokumenty rozšíření implementací `IOleDocumentSite` zajistit mechanismus pro kontejner, aby komunikoval s dokumentu. Volitelně můžete kontejneru implementovat rozhraní aktivní dokument `IOleCommandTarget` a `IContinueCallback` na vyzvednutí jednoduché příkazy jako tisku nebo uložení.  
  
 Volitelně můžete implementovat objekt rámečku, objekty zobrazení a objekt kontejneru **IOleCommandTarget** pro podporu od odeslání určité příkazy, jak je popsáno v [cíle příkazů](../mfc/message-handling-and-command-targets.md). Zobrazení a kontejneru objektů můžete volitelně také můžete implementovat `IPrint` a `IContinueCallback`, pro podporu tisk prostřednictvím kódu programu, jak je popsáno v [programový tisk](../mfc/programmatic-printing.md).  
  
 Následující obrázek znázorňuje koncepční vztahy mezi kontejner a jeho komponenty (na levé straně) a aktivní dokument a jeho zobrazení (vpravo). Aktivní dokument spravuje úložiště a data a zobrazení zobrazí nebo volitelně vytiskne tato data. Rozhraní tučným písmem jsou požadované pro aktivní dokument účast; tučné písmo a kurzíva jsou volitelné. Všechny ostatní rozhraní jsou povinné.  
  
 ![Aktivní dokument kontejneru rozhraní](../mfc/media/vc37gj1.gif "vc37gj1")  
  
 Dokument, který podporuje pouze jedno zobrazení můžete implementovat zobrazení a dokumentu součásti (tedy příslušných rozhraní) u jedné konkrétní třídy. Kontejner lokalitu, která podporuje pouze jedno zobrazení současně kromě toho můžete kombinovat webu dokumentů a zobrazení lokality do jedné lokality konkrétní třídy. Objekt rámečku kontejneru, však musí zůstat odlišné a kontejneru dokumentu součást jenom zde zahrnuta poskytnout úplný přehled o architektuře; nemá vliv architektura zahrnutí aktivního dokumentu.  
  
##  <a name="document_site_objects"></a> Objekty dokumentu lokality  
 V architektuře zahrnutí aktivního dokumentu lokalitu dokumentu je stejný jako objekt lokality klienta v dokumentech OLE a uveďte `IOleDocument` rozhraní:  
  
 `interface IOleDocumentSite : IUnknown`  
  
 `{`  
  
 `HRESULT ActivateMe(IOleDocumentView *pViewToActivate);`  
  
 `}`  
  
 Web dokumentů je koncepčně kontejner pro jeden nebo více objektů "zobrazení server". Každý objekt lokality zobrazení je spojen s objekty jednotlivých zobrazení dokumentu spravovány lokalitou dokumentu. Pokud kontejner podporuje pouze jedno zobrazení na webu dokumentů, pak je můžete implementovat webu dokumentů a zobrazení lokalitu s jedné konkrétní třídy.  
  
##  <a name="view_site_objects"></a> Objekty zobrazení lokality  
 Objekt lokality zobrazení kontejneru spravuje místo zobrazení v konkrétním zobrazení dokumentu. Také podporuje standardní `IOleInPlaceSite` rozhraní zobrazit web také obecně implementuje `IContinueCallback` pro programové řízení tisku. (Všimněte si, že objekt zobrazení nikdy dotazuje na `IContinueCallback` , ve skutečnosti se dá implementovat na některý objekt kontejneru přání.)  
  
 Kontejner, který podporuje více zobrazení musí být schopen vytvořit více zobrazení objekty lokality v rámci lokality dokumentu. To poskytuje jednotlivých zobrazení samostatné aktivace a deaktivace služby podle prostřednictvím `IOleInPlaceSite`.  
  
##  <a name="frame_object"></a> Objekt rámce  
 Objekt rámečku kontejneru je ve většině případů stejné rámce, který slouží k aktivaci na místě v dokumentech OLE, který je, ten, který zpracuje vyjednávání nabídek a panelů nástrojů. Objekt zobrazení má přístup k tomuto objektu rámce prostřednictvím **IOleInPlaceSite::GetWindowContext**, která také poskytuje přístup k objektu kontejneru reprezentující dokument kontejneru (který může zpracovat vyjednávání úrovni podokně panelu nástrojů a výčty obsažených objektů).  
  
 Kontejner můžete posílení rámečku přidáním `IOleCommandTarget`. To umožní přijímat příkazy, které pocházejí v uživatelském rozhraní aktivní dokument stejným způsobem, že toto rozhraní můžete povolit kontejner odeslat stejné příkazy (například **nový soubor**, **otevřete**,  **Uložit jako**, **tiskových**; **Upravit kopie**, **vložení**, **vrátit zpět**a jiné) pro aktivní dokument. Další informace najdete v tématu [cíle příkazů](../mfc/message-handling-and-command-targets.md).  
  
## <a name="see-also"></a>Viz také  
 [Zahrnutí aktivního dokumentu](../mfc/active-document-containment.md)

