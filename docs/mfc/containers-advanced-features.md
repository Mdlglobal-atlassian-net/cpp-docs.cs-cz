---
title: "Kontejnery: Pokročilé funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- links [MFC], to embedded OLE objects
- containers [MFC], links to embedded OLE objects
- containers [MFC], advanced features
- container/server applications [MFC]
- embedded objects [MFC]
- OLE controls [MFC], containers
- OLE containers [MFC], advanced features
- server/container applications [MFC]
- containers [MFC], container applications
ms.assetid: 221fd99c-b138-40fa-ad6a-974e3b3ad1f8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6e55ed4fec962fcafa97b155d8688fcf62c1f2fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="containers-advanced-features"></a>Kontejnery: Pokročilé funkce
Tento článek popisuje kroky potřebné k začlenit volitelné pokročilých funkcí do existující aplikace typu kontejner. Tyto funkce jsou:  
  
-   [Aplikace, která je kontejner a server](#_core_creating_a_container_server_application)  
  
-   [Propojení OLE k vložený objekt](#_core_links_to_embedded_objects)  
  
##  <a name="_core_creating_a_container_server_application"></a>Vytvoření aplikace typu Server/kontejner  
 Aplikace typu server/kontejner je aplikace, která slouží jako kontejner a server. Microsoft Word pro Windows je příkladem. Můžete vložit dokumenty aplikace Word pro Windows v ostatních aplikacích a můžete také vložit položek v dokumentech aplikace Word pro Windows. Proces úpravy aplikace kontejneru kontejner a celého serveru (nelze vytvořit kontejner nebo miniserver aplikaci na kombinaci) je podobný procesu pro vytváření celého serveru.  
  
 Článek [servery: implementace serveru](../mfc/servers-implementing-a-server.md) uvádí počet úlohy, které vyžadují k implementaci serverové aplikace. Pokud převedete kontejnerové aplikace k aplikaci typu server/kontejner, bude nutné provést některé z těchto úloh, přidání kódu do kontejneru. Následuje seznam důležitých věcí, které je třeba zvážit:  
  
-   Kód kontejneru vytvořené průvodcem aplikací již inicializuje subsystém OLE. Nebudete muset změnit nebo přidat nic, pro které podporují.  
  
-   Kdekoli základní třída dokumentové třídy je `COleDocument`, změňte základní třídu pro `COleServerDoc`.  
  
-   Přepsání `COleClientItem::CanActivate` předejdete úpravy položek na místě, zatímco samotný server je používána pro upravit na místě.  
  
     Například MFC OLE vzorku [OCLIENT](../visual-cpp-samples.md) obsahuje vložené položky vytvořené aplikaci typu server/kontejner. Otevřete aplikaci OCLIENT a místní upravit položka vytvořená aplikace typu server/kontejner. Při úpravách položka vaší aplikace, rozhodnete, kterou chcete vložit položky vytvořené ukázka MFC OLE [HIERSVR](../visual-cpp-samples.md). Chcete-li to provést, nemůžete použít aktivace na místě. Je nutné otevřít plně HIERSVR k aktivaci této položky. Protože knihovny Microsoft Foundation Class nepodporuje tuto funkci OLE, přepsání `COleClientItem::CanActivate` umožňuje kontrolovat této situaci a zabránit možná chyba běhu ve vaší aplikaci.  
  
 Pokud vytváříte novou aplikaci a má fungovat jako aplikaci typu server/kontejner, zvolte možnost v dialogovém okně Možnosti OLE v Průvodce vytvořením aplikace a tato podpora se vytvoří automaticky. Další informace najdete v článku [přehled: vytvoření kontejneru ovládacího prvku ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md). Informace o MFC ukázky najdete v tématu MFC ukázky.  
  
 Všimněte si, že aplikace MDI nelze vložit do sebe sama. Aplikace, která je server/kontejner nelze vložit do sebe, pokud je aplikace SDI.  
  
##  <a name="_core_links_to_embedded_objects"></a>Odkazy na vložené objekty  
 Odkazy na vložené objekty funkce umožňuje uživateli vytvořit dokument s OLE odkaz na objekt uvnitř kontejneru aplikace. Můžete například vytvořte dokument v textovém editoru, který obsahuje vložené tabulky. Pokud vaše aplikace podporuje odkazy na vložené objekty, může vložit odkaz na tabulku obsažené v dokumentu textového procesoru. Tato funkce umožňuje vaší aplikace použijte informace obsažené v tabulce aniž by věděly, kde textového procesoru původně získali ho.  
  
#### <a name="to-link-to-embedded-objects-in-your-application"></a>Propojit s vložené objekty v aplikaci  
  
1.  Odvození třídě dokumentu z `COleLinkingDoc` místo `COleDocument`.  
  
2.  Vytvoření ID třídy OLE (**CLSID**) pro vaši aplikaci pomocí generátoru ID třídy součástí nástroje OLE vývoj.  
  
3.  Zaregistrujte aplikaci s OLE.  
  
4.  Vytvoření `COleTemplateServer` objektu jako člena třídy vaší aplikace.  
  
5.  Ve třídě aplikace `InitInstance` člen fungovat, postupujte takto:  
  
    -   Připojit vaše `COleTemplateServer` objekt, který má vaše šablony dokumentu voláním objektu `ConnectTemplate` – členská funkce.  
  
    -   Volání **COleTemplateServer::RegisterAll** – členská funkce k registraci všechny objekty třídy OLE systému.  
  
    -   Volání `COleTemplateServer::UpdateRegistry`. Parametr pouze pro `UpdateRegistry` by měla být `OAT_CONTAINER` Pokud aplikace není spuštěn s přepínačem "/ Embedded". Tato aplikace zaregistruje jako kontejner, který může podporovat odkazy na vložené objekty.  
  
         Pokud je aplikace spuštěna s přepínačem "/ Embedded", by neměla zobrazit jeho hlavní okno podobné serverová aplikace.  
  
 Ukázka MFC OLE [OCLIENT](../visual-cpp-samples.md) implementuje tuto funkci. Příklad, jak to provést, najdete v článku `InitInstance` funkce v OCLIENT. Soubor CPP této ukázkové aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Kontejnery](../mfc/containers.md)   
 [Servery](../mfc/servers.md)

