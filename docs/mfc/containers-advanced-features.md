---
title: 'Kontejnery: Pokročilé funkce'
ms.date: 11/04/2016
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
ms.openlocfilehash: 350431975a4335fc06e436237b7e0d3388faab64
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769560"
---
# <a name="containers-advanced-features"></a>Kontejnery: Pokročilé funkce

Tento článek popisuje kroky potřebné k začlenit volitelné pokročilé funkce do stávajících aplikací typu kontejner. Tyto funkce jsou:

- [Aplikace, která je kontejner a server](#_core_creating_a_container_server_application)

- [Propojení na vložený objekt OLE](#_core_links_to_embedded_objects)

##  <a name="_core_creating_a_container_server_application"></a> Vytvoření aplikace typu Server/kontejner

Aplikace typu server/kontejner je aplikace, která funguje jako kontejner a serverem. Aplikace Microsoft Word pro Windows je příkladem. V jiných aplikacích můžete vložit dokumenty aplikace Word pro Windows a položky můžete také vložit do dokumentů aplikace Word pro Windows. Proces pro úpravu svou aplikaci typu kontejner kontejneru a plnou instalaci systému server (nelze vytvořit aplikace typu kontejner/miniserver kombinaci) je podobný procesu pro vytváření plnou instalaci systému server.

Tento článek [serverů: Implementace serveru](../mfc/servers-implementing-a-server.md) uvádí počet úloh potřebných k implementaci serverové aplikace. Pokud převedete aplikace typu kontejner pro aplikace typu server/kontejner, musíte provést některé z těchto stejných úkolů, přidání kódu do kontejneru. Následující seznam obsahuje důležité věci k uvážení:

- Kód kontejneru už vytvořené průvodcem aplikací inicializuje subsystému OLE. Nemusíte změnit nebo přidat cokoli pro, které podporují.

- Všude, kde je k základní třídě této třídy dokumentu `COleDocument`, změňte základní třídu na `COleServerDoc`.

- Přepsat `COleClientItem::CanActivate` nechcete úpravu položky na místě samotný server se používá k úpravě na místě.

   Například MFC OLE ukázky [OCLIENT](../overview/visual-cpp-samples.md) obsahuje vložené položky vytvořené aplikace typu server/kontejner. Otevřete aplikaci OCLIENT a místní úpravy položky vytvořené aplikace typu server/kontejner. Při úpravách položky vaší aplikace, rozhodnete chcete vložit položky vytvořené v rámci MFC OLE ukázky [HIERSVR](../overview/visual-cpp-samples.md). Chcete-li to provést, nelze použít aktivace na místě. Je nutné otevřít plně HIERSVR k aktivaci této položky. Protože knihovny Microsoft Foundation Class nepodporuje tuto funkci OLE, přepisování `COleClientItem::CanActivate` můžete zkontrolovat v této situaci a zabránit možných chyb za běhu ve vaší aplikaci.

Pokud vytváříte novou aplikaci a chcete, aby fungovala jako aplikace typu server/kontejner, zvolte možnost v dialogovém okně Možnosti OLE v Průvodci aplikací a tato podpora se vytvoří automaticky. Další informace najdete v článku [přehled: Vytvoření kontejneru ovládacího prvku ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md). Informace o ukázky knihovny MFC naleznete v tématu ukázky knihovny MFC.

Všimněte si, že aplikace MDI nelze vložit do sebe sama. Aplikace, která je server/kontejner nelze vložit do sebe sama, pokud je aplikace SDI.

##  <a name="_core_links_to_embedded_objects"></a> Odkazy na vložené objekty

Odkazy na vložené objekty funkce umožňuje uživateli vytvoření dokumentu pomocí propojení OLE do vloženého objektu uvnitř svou aplikaci typu kontejner. Například vytvořte dokument v textovém editoru, který obsahuje vložené tabulky. Pokud vaše aplikace podporuje odkazy na vložené objekty, může vložit odkaz na tabulku obsažené v dokumentu aplikace word procesoru. Tato funkce umožňuje vaší aplikaci použít informace obsažené v tabulce bez znalosti, ve kterém textový procesor původně rozumím.

#### <a name="to-link-to-embedded-objects-in-your-application"></a>Odkaz na vložené objekty v aplikaci

1. Odvodit vaše dokumentové třídy z `COleLinkingDoc` místo `COleDocument`.

1. Vytvoření ID OLE – třídy (**CLSID**) pro vaši aplikaci s využitím generátoru ID třídy součástí OLE nástroje pro vývoj.

1. Zaregistrujte aplikaci s OLE.

1. Vytvoření `COleTemplateServer` objektu jako člen třídy aplikace.

1. Ve své třídě aplikace `InitInstance` členské funkce, postupujte takto:

   - Připojení vaší `COleTemplateServer` objektu do dokumentu šablon voláním objektu `ConnectTemplate` členskou funkci.

   - Volání `COleTemplateServer::RegisterAll` členskou funkci k registraci všech objektů třídy OLE systému.

   - Volání `COleTemplateServer::UpdateRegistry`. Jediný parametr `UpdateRegistry` by měl být *OAT_CONTAINER* Pokud aplikace není spuštěna s přepínačem "/ Embedded". To registruje aplikaci jako kontejner, který může podporovat odkazy na vložené objekty.

         If the application is launched with the "/Embedded" switch, it should not show its main window, similar to a server application.

Ukázky knihovny MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) implementuje tuto funkci. Příklad, jak to lze provést, najdete v článku `InitInstance` fungovat v *OCLIENT. CPP* souboru této ukázkové aplikaci.

## <a name="see-also"></a>Viz také:

[Kontejnery](../mfc/containers.md)<br/>
[Servery](../mfc/servers.md)
