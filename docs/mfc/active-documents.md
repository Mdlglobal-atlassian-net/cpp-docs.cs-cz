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
ms.openlocfilehash: cbea3e032932477006820c5a71fbbf3e40123bdf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322072"
---
# <a name="active-documents"></a>Aktivní dokumenty

Aktivní dokumenty rozšiřují technologii složeného dokumentu OLE. Tato rozšíření jsou k dispozici ve formě dalších rozhraní, která spravují zobrazení, takže objekty mohou fungovat v rámci kontejnerů a přesto zachovat kontrolu nad jejich zobrazení a tiskové funkce. Tento proces umožňuje zobrazit dokumenty v cizích rámcích (například Microsoft Office Binder nebo Microsoft Internet Explorer) a v nativních rámcích (například v portech zobrazení).

Tato část popisuje funkční [požadavky na aktivní dokumenty](#requirements_for_active_documents). Aktivní dokument vlastní sadu dat a má přístup k úložišti, kde lze data uložit a načíst. Může vytvářet a spravovat jedno nebo více zobrazení na svých datech. Kromě podpory obvyklých vkládání a aktivačních rozhraní ole dokumentů na místě, aktivní dokument sděluje svou schopnost vytvářet zobrazení prostřednictvím `IOleDocument`. Prostřednictvím tohoto rozhraní kontejneru můžete požádat o vytvoření (a případně výčet) zobrazení, které lze zobrazit aktivní dokument. Prostřednictvím tohoto rozhraní aktivní dokument může také poskytnout různé informace o sobě, například zda podporuje více zobrazení nebo složité obdélníky.

Následuje `IOleDocument` rozhraní. Všimněte `IEnumOleDocumentViews` si, že rozhraní je standardní `IOleDocumentView*` ole čítač výčtu pro typy.

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

Každý aktivní dokument musí mít s tímto rozhraním zprostředkovatele rámce zobrazení. Pokud dokument není vložen do kontejneru, aktivní dokument server sám musí poskytnout rámec zobrazení. Pokud je však aktivní dokument vložen do aktivního kontejneru dokumentu, kontejner poskytuje rámeček zobrazení.

Aktivní dokument může vytvořit jeden nebo více typů [zobrazení](#requirements_for_view_objects) dat (například normální, osnova, rozložení stránky a tak dále). Zobrazení fungují jako filtry, jejichž prostřednictvím lze data vidět. I v případě, že dokument má pouze jeden typ zobrazení, můžete stále chtít podporovat více zobrazení jako prostředek podpory nové funkce okna (například položku **Nové okno** v nabídce **Okno** v aplikacích sady Office).

## <a name="requirements-for-active-documents"></a><a name="requirements_for_active_documents"></a>Požadavky na aktivní dokumenty

Aktivní dokument, který lze zobrazit v kontejneru aktivního dokumentu, musí:

- Použití OLE složené soubory jako mechanismus `IPersistStorage`úložiště implementací .

- Podpora základních funkcí vkládání dokumentů OLE, včetně **funkce Vytvořit ze souboru**. To vyžaduje rozhraní `IPersistFile`, `IOleObject`a `IDataObject`.

- Podpořte jedno nebo více zobrazení, z nichž každé je schopno aktivace na místě. To znamená, že zobrazení `IOleDocumentView` musí podporovat rozhraní, `IOleInPlaceObject` `IOleInPlaceActiveObject` stejně jako rozhraní `IOleInPlaceSite` `IOleInPlaceFrame` a (pomocí kontejneru a rozhraní).

- Podporují standardní rozhraní aktivních `IOleDocument` `IOleCommandTarget`dokumentů `IPrint`, a .

Znalost, kdy a jak používat rozhraní na straně kontejneru je implikována v těchto požadavcích.

## <a name="requirements-for-view-objects"></a><a name="requirements_for_view_objects"></a>Požadavky na zobrazit objekty

Aktivní dokument může vytvořit jedno nebo více zobrazení jeho dat. Funkčně jsou tato zobrazení jako porty na konkrétní metodu pro zobrazení dat. Pokud aktivní dokument podporuje pouze jedno zobrazení, aktivní dokument a toto jediné zobrazení lze implementovat pomocí jedné třídy. `IOleDocument::CreateView`vrátí ukazatel rozhraní `IOleDocumentView` stejného objektu.

Aby byla komponenta zobrazení reprezentována v `IOleInPlaceObject` `IOleInPlaceActiveObject` aktivním `IOleDocumentView`kontejneru dokumentů, musí podporovat a doplňovat:

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

Každé zobrazení má přidružený web zobrazení, který zapouzdřuje rámec zobrazení a port zobrazení (HWND a obdélníkovou oblast v tomto okně). Web zveřejňuje tuto funkci přes `IOleInPlaceSite` standardní rozhraní. Všimněte si, že je možné mít více než jeden port zobrazení na jednom HWND.

Každý typ zobrazení má obvykle jinou tištěnou reprezentaci. Proto zobrazení a odpovídající zobrazení stránky by `IPrint` měly implementovat tiskové rozhraní, pokud a `IContinueCallback`, resp. Rámeček zobrazení musí vyjednávat `IPrint` s poskytovatelem zobrazení při zahájení tisku, aby byla správně vytištěna záhlaví, zápatí, okraje a související prvky. Zprostředkovatel zobrazení upozorní rámec událostí souvisejících s `IContinueCallback`tiskem prostřednictvím aplikace . Další informace o použití těchto rozhraní naleznete v tématu [Programatický tisk](../mfc/programmatic-printing.md).

Všimněte si, že pokud aktivní dokument podporuje pouze jedno zobrazení, pak aktivní dokument a toto jediné zobrazení lze implementovat pomocí jedné konkrétní třídy. `IOleDocument::CreateView`jednoduše vrátí ukazatel rozhraní `IOleDocumentView` stejného objektu. Stručně řečeno, není nutné, aby existovaly dvě samostatné instance objektu, pokud je vyžadováno pouze jedno zobrazení.

Objekt zobrazení může být také cílem příkazu. Implementací `IOleCommandTarget` zobrazení můžete přijímat příkazy, které pocházejí z uživatelského rozhraní kontejneru (například **New**, **Open**, **Save As**, **Tisk** v nabídce **Soubor;** a **Kopírovat**, **Vložit**, **Vrátit do** akce v nabídce **Úpravy).** Další informace naleznete v [tématu Zpracování zpráv a příkaz cíle](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Viz také

[Zahrnutí aktivního dokumentu](../mfc/active-document-containment.md)
