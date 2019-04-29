---
title: Aktivní dokumenty
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC]
- active documents [MFC], requirements
- view objects [MFC], requirements
- OLE [MFC], active documents
- views [MFC], active documents
- active documents [MFC], views
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
ms.openlocfilehash: 519dd51ab9b46adf862999104e97c6e478ccd86b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394946"
---
# <a name="active-documents"></a>Aktivní dokumenty

Aktivní dokumenty rozšiřovat technologii složeného dokumentu OLE. Tato rozšíření jsou k dispozici ve formě další rozhraní, které spravují zobrazení, tak, aby fungovala v rámci kontejnerů a ještě zachovat kontrolu nad jejich zobrazení a tisk funkce objektů. Tento proces umožňuje zobrazování dokumentů v cizím snímků (například modul vazby sady Office Microsoft nebo Microsoft Internet Explorer) a v nativní rámce (jako je například produkt vlastní zobrazení portů).

Tato část popisuje funkční [požadavky pro aktivní dokumenty](#requirements_for_active_documents). Aktivní dokument vlastní sadu dat a má přístup k úložišti, kde můžete uložit a načíst data. To můžete vytvářet a spravovat jeden nebo více zobrazení na svoje data. Kromě podpory obvykle vkládání a aktivace na místě rozhraní OLE – dokumenty, aktivní dokument komunikuje schopnost vytvářet zobrazení prostřednictvím `IOleDocument`. Prostřednictvím tohoto rozhraní kontejneru chtějí vytvořit (a případně vytvořit výčet) zobrazení, která můžete zobrazit aktivní dokument. Prostřednictvím tohoto rozhraní aktivní dokument můžete také zadat různé informace o sobě, jako je například, jestli podporuje více zobrazení nebo komplexní obdélníků.

Tady je `IOleDocument` rozhraní. Všimněte si, že `IEnumOleDocumentViews` rozhraní je standardní čítač OLE pro `IOleDocumentView*` typy.

```
interface IOleDocument : IUnknown
    {
    HRESULT CreateView(
        [in] IOleInPlaceSite *pIPSite,
        [in] IStream *pstm,
        [in] DWORD dwReserved,
        [out] IOleDocumentView **ppView);

    HRESULT GetDocMiscStatus([out] DWORD *pdwStatus);

    HRESULT EnumViews(
        [out] IEnumOleDocumentViews **ppEnum,
        [out] IOleDocumentView **ppView);
    }
```

Každý aktivní dokument musí mít zprostředkovatele rámce zobrazení s tímto rozhraním. Pokud dokument není vložená v rámci kontejneru, musíte zadat samotný server aktivní dokument zobrazení snímku. Ale při vložení aktivního dokumentu v aktivním dokumentu kontejneru kontejneru poskytuje zobrazení snímku.

Aktivní dokument můžete vytvořit jeden nebo více typů [zobrazení](#requirements_for_view_objects) jeho data (například, Normální, osnovy, rozložení stránky a tak dále). Zobrazení fungují jako filtry, pomocí kterých lze data zobrazit. I v případě, dokument obsahuje pouze jeden typ zobrazení, může stále chcete zajistit podporu více zobrazení jako způsob podporuje nové funkce okno (například **nové okno** položku **okno** nabídku v systému Office aplikace).

##  <a name="requirements_for_active_documents"></a> Požadavky pro aktivní dokumenty

Musí být aktivní dokument, které mohou být zobrazeny v kontejneru prvku aktivního dokumentu:

- Použít složené soubory OLE jako svůj mechanismus úložiště pomocí implementace `IPersistStorage`.

- Podporují základní funkce vložení OLE dokumentů, včetně **vytvořit ze souboru**. To vyžaduje rozhraní `IPersistFile`, `IOleObject`, a `IDataObject`.

- Podpora jedno nebo více zobrazení, z nichž každý je schopen aktivace na místě. To znamená, zobrazení musí podporovat rozhraní `IOleDocumentView` a také rozhraní `IOleInPlaceObject` a `IOleInPlaceActiveObject` (pomocí kontejneru `IOleInPlaceSite` a `IOleInPlaceFrame` rozhraní).

- Podpora rozhraní pro standardní aktivní dokument `IOleDocument`, `IOleCommandTarget`, a `IPrint`.

Znalost, kdy a jak používat rozhraní straně kontejneru je vyjádřena v těchto požadavků.

##  <a name="requirements_for_view_objects"></a> Požadavky pro zobrazení objektů

Aktivní dokument můžete vytvořit jeden nebo více zobrazení jeho data. Tato zobrazení jsou funkčně, jako porty na konkrétní metodu pro zobrazení dat. Pokud aktivní dokument podporuje pouze jedno zobrazení, aktivní dokument a jednotné zobrazení je možné implementovat pomocí jednu třídu. `IOleDocument::CreateView` vrací stejný objekt `IOleDocumentView` ukazatel rozhraní.

A nelze je reprezentovat aktivního dokumentu kontejneru, musí podporovat komponentu zobrazení `IOleInPlaceObject` a `IOleInPlaceActiveObject` kromě `IOleDocumentView`:

```
interface IOleDocumentView : IUnknown
    {
    HRESULT SetInPlaceSite([in] IOleInPlaceSite *pIPSite);
    HRESULT GetInPlaceSite([out] IOleInPlaceSite **ppIPSite);
    HRESULT GetDocument([out] IUnknown **ppunk);
    [input_sync] HRESULT SetRect([in] LPRECT prcView);
    HRESULT GetRect([in] LPRECT prcView);
    [input_sync] HRESULT SetRectComplex(
        [in] LPRECT prcView,
        [in] LPRECT prcHScroll,
        [in] LPRECT prcVScroll,
        [in] LPRECT prcSizeBox);
    HRESULT Show([in] BOOL fShow);
    HRESULT UIActivate([in] BOOL fUIActivate);
    HRESULT Open(void);
    HRESULT CloseView([in] DWORD dwReserved);
    HRESULT SaveViewState([in] IStream *pstm);
    HRESULT ApplyViewState([in] IStream *pstm);
    HRESULT Clone(
        [in] IOleInPlaceSite *pIPSiteNew,
        [out] IOleDocumentView **ppViewNew);
    }
```

Každé zobrazení má přidružené zobrazení webu, který zapouzdřuje rámce zobrazení a zobrazení portů (HWND a obdélníkovou oblast v tomto okně). Web zpřístupňuje tuto funkci, i když standardní `IOleInPlaceSite` rozhraní. Všimněte si, že je možné mít více než jeden port zobrazení na jeden HWND.

Obvykle každý typ zobrazení má jiný tištěné reprezentaci. Proto zobrazení a odpovídající lokality zobrazení by měly implementovat rozhraní tisk Pokud `IPrint` a `IContinueCallback`v uvedeném pořadí. Zobrazení snímků musí si vyjednat s poskytovateli zobrazení prostřednictvím `IPrint` tisk začátku, tak, aby záhlaví, zápatí, okrajů a související prvky jsou zobrazeny správně. Zprostředkovatel zobrazení upozorní rámce události související s tiskem prostřednictvím `IContinueCallback`. Další informace týkající se použití těchto rozhraní najdete v tématu [tisk prostřednictvím kódu programu](../mfc/programmatic-printing.md).

Všimněte si, že pokud aktivní dokument podporuje pouze jedno zobrazení, pak aktivního dokumentu a jednotné zobrazení je možné implementovat pomocí jedné konkrétní třídy. `IOleDocument::CreateView` jednoduše vrací stejný objekt `IOleDocumentView` ukazatel rozhraní. Stručně řečeno není nutné, který existovat dvě instance samostatný objekt Pokud je nutné použít pouze jedno zobrazení.

Zobrazení objektů lze také cíli příkazu. Implementací `IOleCommandTarget` zobrazení může přijímat příkazy, které pocházejí z kontejneru uživatelského rozhraní (například **nový**, **otevřít**, **uložit jako**,  **Tisk** na **souboru** nabídky; a **kopírování**, **vložit**, **zpět** na **upravit** nabídky). Další informace najdete v tématu [zpracování zpráv a cíle příkazů](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Viz také:

[Zahrnutí aktivního dokumentu](../mfc/active-document-containment.md)
