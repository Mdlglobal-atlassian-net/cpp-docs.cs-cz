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
ms.openlocfilehash: cf130bf8dead5c59548821658b979785c4d54726
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376487"
---
# <a name="containers-advanced-features"></a>Kontejnery: Pokročilé funkce

Tento článek popisuje kroky nezbytné k začlenění volitelných pokročilých funkcí do existujících aplikací kontejneru. Jedná se o tyto funkce:

- [Aplikace, která je kontejnerem i serverem](#_core_creating_a_container_server_application)

- [Propojení OLE s vloženým objektem](#_core_links_to_embedded_objects)

## <a name="creating-a-containerserver-application"></a><a name="_core_creating_a_container_server_application"></a>Vytvoření aplikace kontejneru nebo serveru

Aplikace kontejneru nebo serveru je aplikace, která funguje jako kontejner i jako server. Příkladem toho je aplikace Microsoft Word pro Systém Windows. Dokumenty Wordu pro Windows můžete vložit do jiných aplikací a můžete také vložit položky do dokumentů Wordu pro Windows. Proces úpravy aplikace kontejneru jako kontejneru a úplného serveru (nelze vytvořit kombinaci kontejneru nebo aplikace miniserveru) je podobný procesu pro vytvoření úplného serveru.

Článek [Servery: Implementace serveru](../mfc/servers-implementing-a-server.md) obsahuje seznam úloh potřebných k implementaci serverové aplikace. Pokud převedete aplikaci kontejneru na aplikaci kontejneru nebo serveru, budete muset provést některé z těchto stejných úloh a přidat do kontejneru kód. V následujícím textu jsou uvedeny důležité věci, které je třeba zvážit:

- Kód kontejneru vytvořený průvodcem aplikací již inicializuje podsystém OLE. Nebudete muset měnit nebo přidávat nic pro tuto podporu.

- Všude tam, kde je `COleDocument`základní třída třídy dokladu , změňte základní třídu na `COleServerDoc`.

- Přepsání, `COleClientItem::CanActivate` aby se zabránilo úpravám položek na místě, zatímco samotný server je používán k úpravám na místě.

   Například ukázkový objekt [OCLIENT](../overview/visual-cpp-samples.md) knihovny MFC OLE vložil položku vytvořenou aplikací kontejneru nebo serveru. Otevřete aplikaci OCLIENT a na místě upravit položku vytvořenou aplikací kontejneru/serveru. Při úpravách položky aplikace se rozhodnete vložit položku vytvořenou ukázkou [knihovny OLE knihovny MFC HIERSVR](../overview/visual-cpp-samples.md). Chcete-li to provést, nelze použít aktivaci na místě. Chcete-li aktivovat tuto položku, musíte plně otevřít HIERSVR. Vzhledem k tomu, že knihovna tříd `COleClientItem::CanActivate` Microsoft Foundation nepodporuje tuto funkci OLE, přepsání umožňuje zkontrolovat tuto situaci a zabránit možné chybě za běhu v aplikaci.

Pokud vytváříte novou aplikaci a chcete, aby fungovala jako aplikace kontejner/server, zvolte tuto možnost v dialogovém okně Možnosti OLE v průvodci aplikací a tato podpora bude vytvořena automaticky. Další informace naleznete v článku [Přehled: Vytvoření kontejneru ovládacího prvku ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md). Informace o ukázkách knihovny MFC naleznete v [tématu Ukázky knihovny MFC](../overview/visual-cpp-samples.md#mfc-samples).

Všimněte si, že nelze vložit aplikaci MDI do sebe. Aplikace, která je kontejner/server nelze vložit do sebe, pokud se nejedná o aplikaci SDI.

## <a name="links-to-embedded-objects"></a><a name="_core_links_to_embedded_objects"></a>Odkazy na vložené objekty

Funkce Odkazy na vložené objekty umožňuje uživateli vytvořit dokument s odkazem OLE na vložený objekt uvnitř aplikace kontejneru. Můžete například vytvořit dokument v textovém editoru obsahujícím vloženou tabulku. Pokud aplikace podporuje odkazy na vložené objekty, může vložit odkaz na tabulku obsaženou v dokumentu textového procesoru. Tato funkce umožňuje aplikaci používat informace obsažené v tabulce, aniž by věděl, kde textový procesor původně dostal.

#### <a name="to-link-to-embedded-objects-in-your-application"></a>Propojení s vloženými objekty v aplikaci

1. Odvodit `COleLinkingDoc` třídu `COleDocument`dokumentu z aplikace .

1. Vytvořte ID třídy OLE **(CLSID**) pro vaši aplikaci pomocí generátoru ID třídy, který je součástí vývojových nástrojů OLE.

1. Zaregistrujte aplikaci pomocí technologie OLE.

1. Vytvořte `COleTemplateServer` objekt jako člen třídy aplikace.

1. V `InitInstance` členské funkci třídy aplikace postupujte takto:

   - Připojte `COleTemplateServer` objekt k šablonám dokumentů voláním `ConnectTemplate` členské funkce objektu.

   - Volání `COleTemplateServer::RegisterAll` členské funkce zaregistrovat všechny objekty třídy se systémem OLE.

   - Zavolejte `COleTemplateServer::UpdateRegistry`. Jediný parametr `UpdateRegistry` by měl být *OAT_CONTAINER,* pokud aplikace není spuštěna s přepínačem "/Embedded". Tím se zaregistruje aplikace jako kontejner, který může podporovat odkazy na vložené objekty.

      Pokud je aplikace spuštěna s přepínačem "/Embedded", neměla by zobrazovat své hlavní okno, podobně jako serverová aplikace.

Ukázka [knihovny MFC](../overview/visual-cpp-samples.md) OLE implementuje tuto funkci. Příklad, jak se to provádí, `InitInstance` naleznete funkce v *OCLIENT. Soubor CPP* této ukázkové aplikace.

## <a name="see-also"></a>Viz také

[Containers](../mfc/containers.md)<br/>
[Servery](../mfc/servers.md)
