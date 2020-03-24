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
ms.openlocfilehash: a68cc85062f9ca711c453ef98f69a7c5ea114d94
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214354"
---
# <a name="containers-advanced-features"></a>Kontejnery: Pokročilé funkce

Tento článek popisuje kroky potřebné k začlenění volitelných pokročilých funkcí do stávajících aplikací kontejneru. Jsou to tyto funkce:

- [Aplikace, která je kontejnerem i serverem](#_core_creating_a_container_server_application)

- [Propojení OLE s vloženým objektem](#_core_links_to_embedded_objects)

##  <a name="creating-a-containerserver-application"></a><a name="_core_creating_a_container_server_application"></a>Vytvoření aplikace typu kontejner/server

Aplikace typu kontejner/server je aplikace, která funguje jako kontejner i server. Příkladem je Microsoft Word pro Windows. Word pro dokumenty Windows můžete vložit do jiných aplikací a můžete také vkládat položky do Wordu pro dokumenty Windows. Proces pro úpravu aplikace typu kontejner tak, aby byl současně kontejnerem i úplným serverem (nemůžete vytvořit kombinaci kontejneru/aplikace v miniserver), je podobný procesu pro vytvoření úplného serveru.

Článek [servery: implementace serveru](../mfc/servers-implementing-a-server.md) obsahuje řadu úkolů potřebných k implementaci serverové aplikace. Převedete-li aplikaci typu kontejner na aplikaci typu kontejner/server, je nutné provést některé z těchto stejných úloh a přidat kód do kontejneru. Následující seznam obsahuje důležité informace, které je potřeba vzít v úvahu:

- Kód kontejneru vytvořený průvodcem aplikací již inicializuje Podsystém OLE. Pro tuto podporu nebudete muset měnit ani přidávat žádné další.

- Bez ohledu na to, kde je základní třída třídy dokumentu `COleDocument`, změňte základní třídu na `COleServerDoc`.

- Přepište `COleClientItem::CanActivate`, aby nedošlo k úpravě položek na místě, zatímco se server sám používá k úpravám.

   Například ukázková [OCLIENT](../overview/visual-cpp-samples.md) knihovny MFC OLE má vloženou položku vytvořenou v rámci aplikace kontejneru nebo serveru. Otevřete aplikaci OCLIENT a místní upravte položku vytvořenou v rámci aplikace kontejneru nebo serveru. Při úpravách položky vaší aplikace se rozhodnete, že chcete vložit položku vytvořenou v ukázce [HIERSVR](../overview/visual-cpp-samples.md)knihovny MFC OLE. K tomu nemůžete použít místní aktivaci. Chcete-li aktivovat tuto položku, je nutné plně otevřít HIERSVR. Protože knihovna Microsoft Foundation Class nepodporuje tuto funkci OLE, přepisování `COleClientItem::CanActivate` umožňuje kontrolu této situace a zabránit možné chybě v době běhu v aplikaci.

Pokud vytváříte novou aplikaci a chcete, aby fungovala jako aplikace typu kontejner/server, vyberte tuto možnost v dialogovém okně Možnosti OLE v Průvodci aplikací a tato podpora bude vytvořena automaticky. Další informace naleznete v článku [Přehled: vytvoření kontejneru ovládacího prvku ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md). Informace o ukázkách MFC naleznete v tématu [MFC Samples](../overview/visual-cpp-samples.md#mfc-samples).

Všimněte si, že aplikaci MDI nelze vložit do sebe samé. Aplikaci, která je kontejnerem nebo serverem, nelze vložit do sebe samé, pokud se nejedná o aplikaci SDI.

##  <a name="links-to-embedded-objects"></a><a name="_core_links_to_embedded_objects"></a>Odkazy na vložené objekty

Funkce odkazy na vložené objekty umožňuje uživateli vytvořit dokument s odkazem OLE na vložený objekt uvnitř vaší aplikace typu kontejner. Můžete například vytvořit dokument v textovém procesoru obsahujícím vloženou tabulku. Pokud vaše aplikace podporuje odkazy na vložené objekty, může vložit odkaz na tabulku obsaženou v dokumentu procesoru aplikace Word. Tato funkce umožňuje, aby vaše aplikace používala informace obsažené v tabulce bez znalosti, kde textový procesor původně získal.

#### <a name="to-link-to-embedded-objects-in-your-application"></a>Připojení k vloženým objektům ve vaší aplikaci

1. Odvodit třídu dokumentu z `COleLinkingDoc` místo `COleDocument`.

1. Vytvořte identifikátor třídy OLE (**CLSID**) pro vaši aplikaci pomocí generátoru ID třídy, který je součástí vývojářských nástrojů OLE.

1. Zaregistrujte aplikaci pomocí technologie OLE.

1. Vytvořte objekt `COleTemplateServer` jako člen třídy vaší aplikace.

1. Ve svojí členské funkci `InitInstance` třídy aplikace proveďte následující:

   - Připojte objekt `COleTemplateServer` k vašim šablonám dokumentů voláním členské funkce objektu `ConnectTemplate`.

   - Zavolejte členskou funkci `COleTemplateServer::RegisterAll` pro registraci všech objektů třídy se systémem OLE.

   - Zavolejte `COleTemplateServer::UpdateRegistry`. Jediným parametrem `UpdateRegistry` by měl být *OAT_CONTAINER* , pokud aplikace není spuštěna s přepínačem "/Embedded". Tím se aplikace zaregistruje jako kontejner, který může podporovat odkazy na vložené objekty.

      Pokud se aplikace spustí s přepínačem "/Embedded", neměl by zobrazovat své hlavní okno, podobně jako serverová aplikace.

Tuto funkci implementuje ukázková [OCLIENT](../overview/visual-cpp-samples.md) knihovny MFC OLE. Příklad toho, jak to lze provést, naleznete v tématu funkce `InitInstance` v *OCLIENT. Soubor CPP* této ukázkové aplikace

## <a name="see-also"></a>Viz také

[Kontejnery](../mfc/containers.md)<br/>
[Servery](../mfc/servers.md)
