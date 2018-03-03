---
title: "Aktivní dokumenty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC]
- active documents [MFC], requirements
- view objects [MFC], requirements
- OLE [MFC], active documents
- views [MFC], active documents
- active documents [MFC], views
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52f3165f69d47f63fc52ae01bbbd1947e7755a43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="active-documents"></a>Aktivní dokumenty
Aktivní dokumenty rozšířit složeného dokumentu technologie OLE. Tato rozšíření jsou uvedeny v podobě další rozhraní, které spravují zobrazení, tak, aby fungovala v rámci kontejnerů a ještě zachovat kontrolu nad jejich zobrazení a tisk funkce objekty. Tento proces umožní zobrazování dokumentů v cizí snímků (například Microsoft modul vazby sady Office nebo aplikace Microsoft Internet Explorer) i v nativní rámce (třeba portů zobrazení produkt vlastní).  
  
 Tato část popisuje funkční [požadavky pro aktivní dokumenty](#requirements_for_active_documents). Aktivní dokument vlastní sadu dat a má přístup k úložišti, kde můžete data uložit a načíst. Je-li vytvořit a spravovat jeden nebo více zobrazení na jeho data. Vedle podpory obvyklé vložení a aktivace na místě rozhraní OLE – dokumenty, aktivní dokument komunikuje schopnost vytvářet zobrazení prostřednictvím `IOleDocument`. Prostřednictvím tohoto rozhraní můžete pokládat kontejner vytvořit (a případně vytvořit výčet) zobrazení, která můžete zobrazit aktivní dokument. Prostřednictvím tohoto rozhraní aktivní dokument zadat také různé informace o sobě, například zda podporuje více zobrazení nebo komplexní obdélníky.  
  
 Tady je **IOleDocument** rozhraní. Všimněte si, že **IEnumOleDocumentViews** rozhraní je standardní enumerátor OLE pro **IOleDocumentView \***  typy.  
  
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
  
 Všechny aktivní dokument musí mít zprostředkovatele rámce zobrazení s tímto rozhraním. Pokud dokument není vložených v rámci kontejneru, musíte zadat samotný server aktivní dokument rámečku zobrazení. Pokud aktivní dokument je vložen kontejner, poskytuje kontejner ale rámečku zobrazení.  
  
 Aktivní dokument můžete vytvořit jeden nebo více typy [zobrazení](#requirements_for_view_objects) svých dat (například normální popisují, stránky rozložení a tak dále). Zobrazení fungovat stejně jako filtry, pomocí kterých můžete zobrazit data. I v případě, že pouze jeden typ zobrazení má dokument, může stále chcete podporovat více zobrazení jako prostředek podporuje nové funkce okno (například **nové okno** položku **okno** nabídky v Office aplikace).  
  
##  <a name="requirements_for_active_documents"></a>Požadavky pro aktivní dokumenty  
 Aktivní dokument, který lze zobrazit v kontejner musí:  
  
-   Složené soubory na OLE použít jako svůj mechanismus úložiště implementací `IPersistStorage`.  
  
-   Podporují základní funkce vnoření OLE dokumentů, včetně **vytvořit ze souboru**. To vyžaduje rozhraní `IPersistFile`, `IOleObject`, a `IDataObject`.  
  
-   Podpora jedno nebo více zobrazení, z nichž každý je schopen aktivace na místě. To znamená, zobrazení musí podporovat rozhraní `IOleDocumentView` i rozhraní `IOleInPlaceObject` a `IOleInPlaceActiveObject` (pomocí kontejneru **IOleInPlaceSite** a **IOleInPlaceFrame** rozhraní).  
  
-   Podpora rozhraní standardní aktivní dokument `IOleDocument`, `IOleCommandTarget`, a `IPrint`.  
  
 Znalost, kdy a jak používat rozhraní straně kontejneru je zahrnuta v těchto požadavků.  
  
##  <a name="requirements_for_view_objects"></a>Požadavky pro objekty zobrazení  
 Aktivní dokument můžete vytvořit jeden nebo více zobrazení jeho data. Tato zobrazení jsou funkčně, jako porty na konkrétní metodu pro zobrazení data. Pokud aktivní dokument podporuje pouze jedno zobrazení, aktivní dokument a že jednoho zobrazení můžete implementovat pomocí jedné třídy. **IOleDocument::CreateView** vrátí stejný objekt `IOleDocumentView` ukazatel rozhraní.  
  
 A nelze je v rámci kontejner, musí podporovat komponentu zobrazení **IOleInPlaceObject** a **IOleInPlaceActiveObject** kromě `IOleDocumentView`:  
  
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
  
 Každé zobrazení má přidružené zobrazení lokality, který zapouzdřuje rámečku zobrazení a zobrazení port (HWND a obdélníkovou oblast v okně). Web zpřístupňuje tuto funkci, ale standardní **IOleInPlaceSite** rozhraní. Všimněte si, že je možné, že více než jeden port zobrazení na jednom HWND.  
  
 Každý typ zobrazení má obvykle znázornění různých tištěné. Proto zobrazení a odpovídající lokality zobrazení musí implementovat rozhraní tisk Pokud `IPrint` a `IContinueCallback`, v uvedeném pořadí. Zobrazení rámečku musí si vyjednat s poskytovateli zobrazení prostřednictvím **IPrint –** při tisku začne, tak, aby správně vytištěn záhlaví, zápatí, okraje a související prvky. Zprostředkovatel zobrazení upozorní rámečku události související s tiskem prostřednictvím `IContinueCallback`. Další informace o použití těchto rozhraní najdete v tématu [programový tisk](../mfc/programmatic-printing.md).  
  
 Všimněte si, že pokud aktivní dokument podporuje pouze jedno zobrazení, pak aktivní dokument a že jednoho zobrazení lze implementovat pomocí jedné konkrétní třídy. **IOleDocument::CreateView** jednoduše vrátí stejný objekt `IOleDocumentView` ukazatel rozhraní. Stručně řečeno není nutné, který existovat dvě instance samostatný objekt Pokud je nutné použít pouze jedno zobrazení.  
  
 Objekt zobrazení může být také cíl příkazu. Implementací `IOleCommandTarget` zobrazení může přijímat příkazy, které pocházejí z kontejneru uživatelské rozhraní (například **nový**, **otevřete**, **uložit jako**,  **Tisk** na **soubor** nabídky; a **kopie**, **vložení**, **vrátit zpět** na **upravit** nabídky). Další informace najdete v tématu [zpracování zpráv a cíle příkazů](../mfc/message-handling-and-command-targets.md).  
  
## <a name="see-also"></a>Viz také  
 [Zahrnutí aktivního dokumentu](../mfc/active-document-containment.md)

