---
title: Kontejnery pro aktivní dokument
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: e2005ffed592fa1de278e0f6339d94687a20fd06
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377383"
---
# <a name="active-document-containers"></a>Kontejnery pro aktivní dokument

Aktivní kontejner dokumentů, například Microsoft Office Binder nebo Internet Explorer, umožňuje pracovat s několika dokumenty různých typů aplikací v rámci jednoho rámce (namísto vynucení vytvoření a použití více rámců aplikace pro každý typ dokumentu).

Knihovna MFC poskytuje plnou podporu `COleDocObjectItem` pro kontejnery aktivních dokumentů ve třídě. Průvodce aplikací knihovny MFC můžete použít k vytvoření kontejneru aktivního dokumentu zaškrtnutím políčka **Aktivní kontejner dokumentu** na stránce Podpora **složeného dokumentu** průvodce aplikací knihovny MFC. Další informace naleznete [v tématu Vytvoření aplikace kontejneru aktivních dokumentů](../mfc/creating-an-active-document-container-application.md).

Další informace o aktivních kontejnerech dokumentů naleznete v tématu:

- [Požadavky na kontejnery](#container_requirements)

- [Objekty webu dokumentu](#document_site_objects)

- [Zobrazit objekty webu](#view_site_objects)

- [Objekt rámce](#frame_object)

- [Slučování nabídek nápovědy](../mfc/help-menu-merging.md)

- [Tisk prostřednictvím kódu programu](../mfc/programmatic-printing.md)

- [Cíle příkazů](../mfc/message-handling-and-command-targets.md)

## <a name="container-requirements"></a><a name="container_requirements"></a>Požadavky na kontejnery

Aktivní podpora dokumentů v kontejneru aktivního dokumentu znamená více než jen implementace rozhraní: vyžaduje také znalost použití rozhraní obsaženého objektu. Totéž platí pro rozšíření aktivní ho dokumentu, kde kontejner musí také vědět, jak používat tato rozhraní rozšíření na aktivní dokumenty samotné.

Kontejner aktivních dokumentů, který integruje aktivní dokumenty, musí:

- Být schopen zpracování objektu `IPersistStorage` úložiště prostřednictvím rozhraní, `IStorage` to znamená, že musí poskytnout instanci pro každý aktivní dokument.

- Podpora základních funkcí vkládání dokumentů OLE, které vyžadují objekty "webu" (jeden `IOleClientSite` pro `IAdviseSink`dokument nebo vložení), které implementují a .

- Podpora aktivace vložených objektů nebo aktivních dokumentů na místě. Objekty webu kontejneru `IOleInPlaceSite` musí implementovat a objekt `IOleInPlaceFrame`rámce kontejneru musí poskytnout .

- Podporujte rozšíření aktivních dokumentů implementací, `IOleDocumentSite` která poskytuje mechanismus pro kontejner pro rozhovor s dokumentem. Volitelně kontejner může implementovat rozhraní `IOleCommandTarget` aktivního dokumentu a `IContinueCallback` vyzvednout jednoduché příkazy, jako je například tisk nebo uložení.

Objekt rámce, objekty zobrazení a objekt kontejneru `IOleCommandTarget` mohou volitelně implementovat pro podporu odesílání určitých příkazů, jak je popsáno v [command targets](../mfc/message-handling-and-command-targets.md). Objekty zobrazení a kontejneru `IPrint` `IContinueCallback`mohou také volitelně implementovat a podporují programový tisk, jak je popsáno v [programatickém tisku](../mfc/programmatic-printing.md).

Následující obrázek znázorňuje koncepční vztahy mezi kontejnerem a jeho součástmi (vlevo) a aktivním dokumentem a jeho zobrazeními (vpravo). Aktivní dokument spravuje úložiště a data a zobrazení tato data zobrazí nebo volitelně vytiskne. Rozhraní tučně jsou rozhraní potřebná pro aktivní účast na dokumentu; ty tučné a kurzívou jsou volitelné. Všechna ostatní rozhraní jsou povinná.

![Rozhraní kontejneru aktivních dokumentů](../mfc/media/vc37gj1.gif "Rozhraní kontejneru aktivních dokumentů")

Dokument, který podporuje pouze jedno zobrazení, může implementovat součásti zobrazení i dokumentu (tj. jejich odpovídající rozhraní) do jedné konkrétní třídy. Kromě toho může web kontejneru, který podporuje pouze jedno zobrazení najednou, kombinovat web dokumentu a web zobrazení do jedné konkrétní třídy webu. Objekt rámečku kontejneru však musí zůstat odlišný a součást dokumentu kontejneru je zde zahrnuta pouze proto, aby poskytla úplný obraz o architektuře; není ovlivněna architekturou uzavření aktivního dokumentu.

## <a name="document-site-objects"></a><a name="document_site_objects"></a>Objekty webu dokumentu

V architektuře uzavření aktivního dokumentu je web dokumentu stejný jako objekt klientského `IOleDocument` webu v dokumentu OLE Documents s přidáním rozhraní:

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

Web dokumentu je koncepčně kontejner pro jeden nebo více objektů "zobrazit web". Každý objekt webu zobrazení je přidružen k jednotlivým objektům zobrazení dokumentu spravovaného webem dokumentu. Pokud kontejner podporuje pouze jedno zobrazení na web dokumentu, může implementovat web dokumentu a web zobrazení s jedinou konkrétní třídou.

## <a name="view-site-objects"></a><a name="view_site_objects"></a>Zobrazit objekty webu

Objekt lokality zobrazení kontejneru spravuje prostor zobrazení pro konkrétní zobrazení dokumentu. Kromě podpory standardního `IOleInPlaceSite` rozhraní se web zobrazení obecně `IContinueCallback` implementuje také pro programový tisk. (Všimněte si, že objekt `IContinueCallback` zobrazení nikdy dotazy pro tak, že může být skutečně implementována na libovolný objekt kontejneru touží.)

Kontejner, který podporuje více zobrazení, musí být schopen vytvořit více objektů webu zobrazení v rámci webu dokumentu. To poskytuje každému zobrazení samostatné aktivační a deaktivační služby poskytované prostřednictvím `IOleInPlaceSite`.

## <a name="frame-object"></a><a name="frame_object"></a>Objekt rámce

Objekt rámce kontejneru je z větší části stejný rámec, který se používá pro aktivaci na místě v dokumentech OLE, to znamená ten, který zpracovává vyjednávání nabídky a panelu nástrojů. Objekt zobrazení má přístup k `IOleInPlaceSite::GetWindowContext`tomuto objektu rámce prostřednictvím aplikace , která také poskytuje přístup k objektu kontejneru představujícímu dokument kontejneru (který dokáže zpracovat vyjednávání panelu nástrojů na úrovni podokna a výčet obsahujícího objektu).

Aktivní kontejner dokumentu může rozšířit `IOleCommandTarget`rámeček přidáním . To mu umožňuje přijímat příkazy, které pocházejí z uživatelského rozhraní aktivního dokumentu stejným způsobem, jakým toto rozhraní může umožnit kontejneru odesílat stejné příkazy (například **File New**, **Open**, **Save As**, **Print**; **Úprava kopírovat**, **vložit**, **zpět**a další) do aktivního dokumentu. Další informace naleznete v [tématu Command Targets](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Viz také

[Zahrnutí aktivního dokumentu](../mfc/active-document-containment.md)
