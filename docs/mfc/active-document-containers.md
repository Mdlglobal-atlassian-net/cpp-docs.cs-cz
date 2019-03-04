---
title: Kontejnery pro aktivní dokument
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: 6e4defaf347f0d539ef023ee9c0e1e85dd2390db
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288958"
---
# <a name="active-document-containers"></a>Kontejnery pro aktivní dokument

Kontejner pro aktivní dokument, jako je například Microsoft modul vazby sady Office nebo aplikace Internet Explorer umožňuje pracovat s několika dokumenty těchto různých typů v rámci jednoho snímku (místo vynucení můžete vytvářet a používat více aplikací snímků pro každý Typ dokumentu).

Knihovna MFC poskytuje plná podpora pro kontejnery pro aktivní dokument v `COleDocObjectItem` třídy. Můžete použít Průvodce aplikací knihovny MFC a vytvoří kontejner aktivního dokumentu výběrem **kontejner pro aktivní dokument** zaškrtávací políčko na **Podpora složených dokumentů** stránky Průvodce aplikací knihovny MFC. Další informace najdete v tématu [vytvoření aplikace kontejnerů pro aktivní dokument](../mfc/creating-an-active-document-container-application.md).

Další informace o kontejnery pro aktivní dokument naleznete v tématu:

- [Požadavků na kontejner](#container_requirements)

- [Objekty lokality dokumentu](#document_site_objects)

- [Zobrazit objekty lokality](#view_site_objects)

- [Orámovat objekt](#frame_object)

- [Slučování nabídek nápovědy](../mfc/help-menu-merging.md)

- [Tisk prostřednictvím kódu programu](../mfc/programmatic-printing.md)

- [Cíle příkazů](../mfc/message-handling-and-command-targets.md)

##  <a name="container_requirements"></a> Požadavků na kontejner

Podpora aktivního dokumentu v aktivním dokumentu kontejneru znamená víc než jenom implementace rozhraní: také vyžaduje znalost pomocí rozhraní obsažený objekt. Totéž platí i pro aktivní dokument rozšíření, kde kontejneru musíte taky vědět jak pomocí těchto rozhraní rozšíření na samotných dokumentech aktivní.

Kontejner pro aktivní dokument, který integruje aktivní dokumenty musí:

- Být schopné úložišti objektů pomocí `IPersistStorage` rozhraní, to znamená, je nutné zadat `IStorage` instance pro každý aktivní dokument.

- Podpora základní vkládání funkce dokumenty OLE, proto je nutné objekty "lokalit" (jeden na dokument nebo vkládání), které implementují `IOleClientSite` a `IAdviseSink`.

- Podpora aktivace na místě vložené objekty nebo aktivní dokumenty. Musíte implementovat objekty lokality kontejneru `IOleInPlaceSite` a je nutné zadat objekt rámce kontejneru `IOleInPlaceFrame`.

- Podpora rozšíření aktivní dokumenty implementací `IOleDocumentSite` mechanismus pro kontejner ke komunikaci s dokumentu. Volitelně můžete kontejner implementovat rozhraní aktivní dokument `IOleCommandTarget` a `IContinueCallback` ke sbírání jednoduchých příkazů, jako je například tisku nebo uložení.

Orámovat objekt zobrazit objekty a objekt kontejneru může volitelně implementovat `IOleCommandTarget` pro podporu odeslání některé příkazy, jak je popsáno v [cíle příkazů](../mfc/message-handling-and-command-targets.md). Zobrazení a kontejneru objektů lze také v případě potřeby implementovat `IPrint` a `IContinueCallback`pro zajištění podpory tisk prostřednictvím kódu programu, jak je popsáno v [programový tisk](../mfc/programmatic-printing.md).

Následující obrázek znázorňuje koncepční vztah mezi kontejneru a jeho součástí (vlevo) a aktivní dokument a jeho zobrazení (vpravo). Aktivní dokument spravuje úložiště a data a zobrazí nebo volitelně vypíše data zobrazení. Rozhraní tučným písmem jsou povinné pro aktivní dokument účast; tučné písmo a kurzíva jsou volitelné. Všechny ostatní rozhraní jsou povinné.

![Rozhraní kontejner aktivního dokumentu](../mfc/media/vc37gj1.gif "rozhraní kontejner aktivního dokumentu")

Dokument, který podporuje pouze jedno zobrazení můžete implementovat součásti zobrazení i dokumentu (to znamená, že jejich odpovídající rozhraní) na jednu konkrétní třídu. Kontejner lokality, která podporuje pouze jedno zobrazení najednou kromě toho můžete kombinovat webu dokumentů a zobrazení webu do jedné lokality konkrétní třídy. Orámovat objekt kontejneru, ale musí zůstat distinct a součást dokumentu kontejneru pouze zde zahrnuta poskytnout ucelený přehled o architektuře; není ovlivněna architektura zahrnutí aktivního dokumentu.

##  <a name="document_site_objects"></a> Objekty lokality dokumentu

V architektuře zahrnutí aktivního dokumentu webu dokumentů je stejný jako objekt lokality klienta v dokumentech OLE a uveďte `IOleDocument` rozhraní:

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

Web dokumentů se koncepčně kontejner pro jeden nebo více objektů "zobrazení webu". Každý objekt lokality zobrazení souvisí s objekty jednotlivých zobrazení dokumentu spravovány lokalitou dokumentu. Pokud kontejner podporuje pouze jedno zobrazení na webu dokumentů, pak ho můžete implementovat webu dokumentů a zobrazení webu pomocí jedné konkrétní třídy.

##  <a name="view_site_objects"></a> Zobrazit objekty lokality

Objekt kontejneru zobrazení webu spravuje prostor pro zobrazení pro určité zobrazení dokumentu. Kromě podpory standard `IOleInPlaceSite` rozhraní, zobrazení webu také obecně implementuje `IContinueCallback` programový tisk ovládacího prvku. (Všimněte si, že objekt zobrazení nikdy dotazuje `IContinueCallback` tak ji ve skutečnosti může být implementováno na některý objekt kontejneru verzi.)

Kontejner, který podporuje několik zobrazení musí být schopen vytvořit více zobrazení objektů webu v rámci webu dokumentů. Každé zobrazení to poskytuje samostatné aktivace a deaktivace služby poskytované prostřednictvím `IOleInPlaceSite`.

##  <a name="frame_object"></a> Orámovat objekt

Orámovat objekt kontejneru je ve většině případů stejné rámce, který se používá pro aktivace na místě v dokumenty OLE, to znamená, ten, který zpracuje vyjednávání nabídek a panelů nástrojů. Objekt zobrazení má přístup k tomuto objektu rámce prostřednictvím `IOleInPlaceSite::GetWindowContext`, která navíc poskytuje přístup ke kontejneru objekt reprezentující dokument kontejneru (která může zpracovávat vyjednávání úrovni podokna nástrojů a výčet obsaženého objektu).

Kontejner pro aktivní dokument můžete rozšířit rámce přidáním `IOleCommandTarget`. Umožní vám to přijímá příkazy, které pocházejí z aktivního dokumentu uživatelské rozhraní stejným způsobem, že toto rozhraní umožňuje kontejner k odesílání stejných příkazů (například **nový soubor**, **otevřít**,  **Uložit jako**, **tisk**; **Upravit kopii**, **vložit**, **zpět**a další) pro aktivní dokument. Další informace najdete v tématu [cíle příkazů](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Viz také:

[Zahrnutí aktivního dokumentu](../mfc/active-document-containment.md)
