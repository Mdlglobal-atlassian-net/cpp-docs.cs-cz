---
title: COleServerDoc Class
ms.date: 11/04/2016
f1_keywords:
- COleServerDoc
- AFXOLE/COleServerDoc
- AFXOLE/COleServerDoc::COleServerDoc
- AFXOLE/COleServerDoc::ActivateDocObject
- AFXOLE/COleServerDoc::ActivateInPlace
- AFXOLE/COleServerDoc::DeactivateAndUndo
- AFXOLE/COleServerDoc::DiscardUndoState
- AFXOLE/COleServerDoc::GetClientSite
- AFXOLE/COleServerDoc::GetEmbeddedItem
- AFXOLE/COleServerDoc::GetItemClipRect
- AFXOLE/COleServerDoc::GetItemPosition
- AFXOLE/COleServerDoc::GetZoomFactor
- AFXOLE/COleServerDoc::IsDocObject
- AFXOLE/COleServerDoc::IsEmbedded
- AFXOLE/COleServerDoc::IsInPlaceActive
- AFXOLE/COleServerDoc::NotifyChanged
- AFXOLE/COleServerDoc::NotifyClosed
- AFXOLE/COleServerDoc::NotifyRename
- AFXOLE/COleServerDoc::NotifySaved
- AFXOLE/COleServerDoc::OnDeactivate
- AFXOLE/COleServerDoc::OnDeactivateUI
- AFXOLE/COleServerDoc::OnDocWindowActivate
- AFXOLE/COleServerDoc::OnResizeBorder
- AFXOLE/COleServerDoc::OnShowControlBars
- AFXOLE/COleServerDoc::OnUpdateDocument
- AFXOLE/COleServerDoc::RequestPositionChange
- AFXOLE/COleServerDoc::SaveEmbedding
- AFXOLE/COleServerDoc::ScrollContainerBy
- AFXOLE/COleServerDoc::UpdateAllItems
- AFXOLE/COleServerDoc::CreateInPlaceFrame
- AFXOLE/COleServerDoc::DestroyInPlaceFrame
- AFXOLE/COleServerDoc::GetDocObjectServer
- AFXOLE/COleServerDoc::OnClose
- AFXOLE/COleServerDoc::OnExecOleCmd
- AFXOLE/COleServerDoc::OnFrameWindowActivate
- AFXOLE/COleServerDoc::OnGetEmbeddedItem
- AFXOLE/COleServerDoc::OnReactivateAndUndo
- AFXOLE/COleServerDoc::OnSetHostNames
- AFXOLE/COleServerDoc::OnSetItemRects
- AFXOLE/COleServerDoc::OnShowDocument
helpviewer_keywords:
- COleServerDoc [MFC], COleServerDoc
- COleServerDoc [MFC], ActivateDocObject
- COleServerDoc [MFC], ActivateInPlace
- COleServerDoc [MFC], DeactivateAndUndo
- COleServerDoc [MFC], DiscardUndoState
- COleServerDoc [MFC], GetClientSite
- COleServerDoc [MFC], GetEmbeddedItem
- COleServerDoc [MFC], GetItemClipRect
- COleServerDoc [MFC], GetItemPosition
- COleServerDoc [MFC], GetZoomFactor
- COleServerDoc [MFC], IsDocObject
- COleServerDoc [MFC], IsEmbedded
- COleServerDoc [MFC], IsInPlaceActive
- COleServerDoc [MFC], NotifyChanged
- COleServerDoc [MFC], NotifyClosed
- COleServerDoc [MFC], NotifyRename
- COleServerDoc [MFC], NotifySaved
- COleServerDoc [MFC], OnDeactivate
- COleServerDoc [MFC], OnDeactivateUI
- COleServerDoc [MFC], OnDocWindowActivate
- COleServerDoc [MFC], OnResizeBorder
- COleServerDoc [MFC], OnShowControlBars
- COleServerDoc [MFC], OnUpdateDocument
- COleServerDoc [MFC], RequestPositionChange
- COleServerDoc [MFC], SaveEmbedding
- COleServerDoc [MFC], ScrollContainerBy
- COleServerDoc [MFC], UpdateAllItems
- COleServerDoc [MFC], CreateInPlaceFrame
- COleServerDoc [MFC], DestroyInPlaceFrame
- COleServerDoc [MFC], GetDocObjectServer
- COleServerDoc [MFC], OnClose
- COleServerDoc [MFC], OnExecOleCmd
- COleServerDoc [MFC], OnFrameWindowActivate
- COleServerDoc [MFC], OnGetEmbeddedItem
- COleServerDoc [MFC], OnReactivateAndUndo
- COleServerDoc [MFC], OnSetHostNames
- COleServerDoc [MFC], OnSetItemRects
- COleServerDoc [MFC], OnShowDocument
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
ms.openlocfilehash: eec94a32fa0963d4cf2eccae0fb9e2423e75ffdc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503811"
---
# <a name="coleserverdoc-class"></a>COleServerDoc Class

Základní třída pro dokumenty OLE serveru.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleServerDoc::COleServerDoc](#coleserverdoc)|`COleServerDoc` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleServerDoc::ActivateDocObject](#activatedocobject)|Aktivuje přidružený dokument DocObject.|
|[COleServerDoc::ActivateInPlace](#activateinplace)|Aktivuje dokument pro místní úpravy.|
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|Deaktivuje uživatelské rozhraní serveru.|
|[COleServerDoc::DiscardUndoState](#discardundostate)|Odstraní informace o stavu vrácení zpět.|
|[COleServerDoc::GetClientSite](#getclientsite)|Načte ukazatel na základní `IOleClientSite` rozhraní.|
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|Vrátí ukazatel na položku představující celý dokument.|
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|Vrátí aktuální obdélník oříznutí pro místní úpravy.|
|[COleServerDoc::GetItemPosition](#getitemposition)|Vrátí aktuální pozici obdélník vzhledem k klientské oblasti aplikace kontejneru pro místní úpravy.|
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|Vrátí faktor přiblížení v pixelech.|
|[COleServerDoc::IsDocObject](#isdocobject)|Určuje, zda je dokument DocObject.|
|[COleServerDoc::IsEmbedded](#isembedded)|Označuje, zda je dokument vložen do dokumentu kontejneru nebo zda je spuštěn samostatný.|
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|Vrátí hodnotu TRUE, pokud je položka aktuálně aktivována.|
|[COleServerDoc::NotifyChanged](#notifychanged)|Upozorní kontejnery, které uživatel změnil, v dokumentu.|
|[COleServerDoc::NotifyClosed](#notifyclosed)|Upozorní kontejnery, které uživatel dokument zavřel.|
|[COleServerDoc::NotifyRename](#notifyrename)|Upozorní kontejnery, které uživatel přejmenoval na dokument.|
|[COleServerDoc::NotifySaved](#notifysaved)|Upozorní kontejnery, které uživatel dokument uložil.|
|[COleServerDoc::OnDeactivate](#ondeactivate)|Volá se rozhraním, když uživatel deaktivuje položku, která se aktivovala na místě.|
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|Volá se rozhraním, aby se zničily ovládací prvky a jiné prvky uživatelského rozhraní vytvořené pro místní aktivaci.|
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|Volá se rozhraním, když se aktivuje nebo deaktivuje okno rámce dokumentu kontejneru.|
|[COleServerDoc::OnResizeBorder](#onresizeborder)|Volá se rozhraním, když se změní velikost okna rámce nebo okna dokumentu aplikace kontejneru.|
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|Volá se rozhraním, aby se zobrazily nebo skryly ovládací panely pro místní úpravy.|
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|Volá se rozhraním, když se uloží dokument serveru, který je vloženou položkou, a aktualizuje kopii této položky kontejneru.|
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|Změní umístění místního editačního snímku.|
|[COleServerDoc::SaveEmbedding](#saveembedding)|Instruuje aplikaci kontejneru, aby dokument ukládal.|
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|Posune dokument kontejneru.|
|[COleServerDoc::UpdateAllItems](#updateallitems)|Upozorní kontejnery, které uživatel změnil, v dokumentu.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|Volá se rozhraním, aby se vytvořilo okno rámce pro místní úpravy.|
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|Volá se rozhraním, aby se zničilo okno rámce pro místní úpravy.|
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|Přepsáním této funkce vytvoříte nový `CDocObjectServer` objekt a označíte, že tento dokument je kontejnerem DocObject.|
|[COleServerDoc::OnClose](#onclose)|Volá se rozhraním, když kontejner požaduje zavření dokumentu.|
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|Provede zadaný příkaz nebo zobrazí nápovědu k příkazu.|
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|Volá se rozhraním, když se aktivuje nebo deaktivuje okno rámce kontejneru.|
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|Volá se `COleServerItem` , aby se získal celý dokument, který se používá k získání vložené položky. Vyžaduje se implementace.|
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|Volá se rozhraním, aby se odvolaly změny provedené při místních úpravách.|
|[COleServerDoc::OnSetHostNames](#onsethostnames)|Volá se rozhraním, když kontejner nastaví název okna pro vložený objekt.|
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|Volá se rozhraním, aby se umístilo místní editační okno rámce v okně aplikace kontejneru.|
|[COleServerDoc::OnShowDocument](#onshowdocument)|Volá se rozhraním pro zobrazení nebo skrytí dokumentu.|

## <a name="remarks"></a>Poznámky

Dokument serveru může obsahovat objekty [odvozenou třídu COleServerItem](../../mfc/reference/coleserveritem-class.md) , které reprezentují serverové rozhraní pro vložené nebo propojené položky. Pokud je serverová aplikace spuštěna kontejnerem pro úpravu vložené položky, je položka načtena jako vlastní serverový dokument; objekt obsahuje pouze jeden `COleServerItem` objekt, který se skládá z celého dokumentu. `COleServerDoc` Pokud je serverová aplikace spuštěna kontejnerem pro úpravu propojené položky, je z disku načten existující dokument. část obsahu dokumentu je zvýrazněna, aby označovala propojenou položku.

`COleServerDoc`objekty mohou také obsahovat položky třídy [COleClientItem](../../mfc/reference/coleclientitem-class.md) . To vám umožní vytvářet aplikace kontejnerového serveru. Rozhraní poskytuje funkce pro správné uložení `COleClientItem` položek při `COleServerItem` údržbě objektů.

Pokud serverová aplikace nepodporuje odkazy, bude serverový dokument vždycky obsahovat jenom jednu položku serveru, která představuje celý vložený objekt jako dokument. Pokud vaše aplikace serveru podporuje odkazy, musí vytvořit položku serveru pokaždé, když se do schránky zkopíruje výběr.

Chcete- `COleServerDoc`li použít, odvodit z něj třídu a implementovat členskou funkci [funkci OnGetEmbeddedItem](#ongetembeddeditem) , která umožňuje serveru podporovat vložené položky. Odvodit třídu z `COleServerItem` k implementaci položek v dokumentech a vracet objekty této třídy z. `OnGetEmbeddedItem`

Pro podporu propojených položek `COleServerDoc` poskytuje členskou funkci [OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) . Můžete použít výchozí implementaci nebo ji přepsat, pokud máte vlastní způsob správy položek dokumentu.

Pro každý typ `COleServerDoc`dokumentu serveru, který podporuje vaše aplikace, potřebujete jednu odvozenou třídu. Například pokud vaše serverová aplikace podporuje listy a grafy, potřebujete dvě `COleServerDoc`odvozené třídy.

Další informace o serverech najdete v článku [servery: Implementace serveru](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[Objektu CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXOLE. h

##  <a name="activatedocobject"></a>COleServerDoc::ActivateDocObject

Aktivuje přidružený dokument DocObject.

```
void ActivateDocObject();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `COleServerDoc` nepodporuje aktivní dokumenty (také označované jako DocObjects). Pokud chcete povolit tuto podporu, přečtěte si téma [GetDocObjectServer](#getdocobjectserver) a class [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).

##  <a name="activateinplace"></a>COleServerDoc::ActivateInPlace

Aktivuje položku pro místní úpravy.

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak 0, což znamená, že položka je plně otevřená.

### <a name="remarks"></a>Poznámky

Tato funkce provádí všechny operace nezbytné k místní aktivaci. Vytvoří místní okno rámce, aktivuje ho a velikost na položku, nastaví sdílené nabídky a další ovládací prvky, posuňte položku na zobrazení a nastaví fokus na místní okno rámce.

Tato funkce je volána výchozí implementací [odvozenou třídu COleServerItem:: show](../../mfc/reference/coleserveritem-class.md#onshow). Tuto funkci volejte, pokud vaše aplikace podporuje jinou operaci pro místní aktivaci (například Play).

##  <a name="coleserverdoc"></a>COleServerDoc::COleServerDoc

`COleServerDoc` Vytvoří objekt bez připojení k systémovým knihovnám DLL systému OLE.

```
COleServerDoc();
```

### <a name="remarks"></a>Poznámky

Chcete-li otevřít komunikaci s OLE, je nutné zavolat [COleLinkingDoc:: Register](../../mfc/reference/colelinkingdoc-class.md#register) . Pokud používáte [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) v aplikaci `COleLinkingDoc::Register` , je `COleLinkingDoc`volána pro vás implementací `OnNewDocument`, `OnOpenDocument`a `OnSaveDocument`.

##  <a name="createinplaceframe"></a>COleServerDoc::CreateInPlaceFrame

Rozhraní volá tuto funkci, aby vytvořilo okno rámce pro místní úpravy.

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na nadřazené okno aplikace kontejneru.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na místní okno rámce nebo hodnotu NULL, pokud je neúspěšný.

### <a name="remarks"></a>Poznámky

Výchozí implementace používá pro vytvoření rámce informace zadané v šabloně dokumentu. Toto zobrazení je prvním zobrazením vytvořeným pro dokument. Toto zobrazení je dočasně odpojeno od původního rámce a připojeno k nově vytvořenému snímku.

Toto je pokročilá přepsatelné.

##  <a name="deactivateandundo"></a>COleServerDoc::D eactivateAndUndo

Tuto funkci volejte, pokud vaše aplikace podporuje vrácení zpět a uživatel klikne na tlačítko zpět po aktivaci položky, ale před jejím úpravou.

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové při úspěchu; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud je aplikace kontejneru zapisována pomocí knihovna Microsoft Foundation Class, volání této funkce způsobí, že je volána metoda [COleClientItem:: OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) , která deaktivuje uživatelské rozhraní serveru.

##  <a name="destroyinplaceframe"></a>  COleServerDoc::DestroyInPlaceFrame

Rozhraní volá tuto funkci, aby zničila místní okno rámce a vrátila okno dokumentu serverové aplikace do stavu před místní aktivací.

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parametry

*pFrameWnd*<br/>
Ukazatel na místní okno rámce, které má být zničeno.

### <a name="remarks"></a>Poznámky

Toto je pokročilá přepsatelné.

##  <a name="discardundostate"></a>COleServerDoc::D iscardUndoState

Pokud uživatel provede operaci úpravy, kterou nelze vrátit zpět, zavolejte tuto funkci, aby aplikace kontejneru vynutila zahození informací o stavu vrácení zpět.

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové při úspěchu; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce je k dispozici, takže servery, které podporují vrácení zpět, můžou uvolnit prostředky, které by jinak byly spotřebovány informacemi o stavu vrácení, které nelze použít.

##  <a name="getclientsite"></a>COleServerDoc::GetClientSite

Načte ukazatel na základní `IOleClientSite` rozhraní.

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>Návratová hodnota

Načte ukazatel na základní rozhraní [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite) .

##  <a name="getdocobjectserver"></a>  COleServerDoc::GetDocObjectServer

Přepište tuto funkci, pokud chcete `CDocObjectServer` vytvořit novou položku a vrátit na ni ukazatel.

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>Parametry

*pDocSite*<br/>
Ukazatel na `IOleDocumentSite` rozhraní, které bude připojit tento dokument k serveru.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CDocObjectServer`; Hodnota NULL, pokud se operace nezdařila.

### <a name="remarks"></a>Poznámky

Když je aktivován Server DocObject, vrátí se návratový ukazatel bez hodnoty NULL, který může klient podporovat DocObjects. Výchozí implementace vrací hodnotu NULL.

Typická implementace pro dokument, který podporuje DocObjects, jednoduše přidělí nový `CDocObjectServer` objekt a vrátí jej volajícímu. Příklad:

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

##  <a name="getembeddeditem"></a>COleServerDoc::GetEmbeddedItem

Voláním této funkce získáte ukazatel na položku představující celý dokument.

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na položku představující celý dokument; Hodnota NULL, pokud se operace nezdařila.

### <a name="remarks"></a>Poznámky

Volá [COleServerDoc:: funkci OnGetEmbeddedItem](#ongetembeddeditem), virtuální funkci bez výchozí implementace.

##  <a name="getitemcliprect"></a>COleServerDoc::GetItemClipRect

`GetItemClipRect` Zavolejte členskou funkci pro získání souřadnic obdélníku oříznutí položky, která je upravována na místě.

```
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>Parametry

*lpClipRect*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt, který získá souřadnice ořezového obdélníku položky.

### <a name="remarks"></a>Poznámky

Souřadnice jsou v pixelech vzhledem k klientské oblasti okna kontejneru aplikace.

K vykreslování by nemělo dojít mimo obdélník oříznutí. Vykreslování je obvykle automaticky omezeno. Pomocí této funkce lze určit, zda se uživatel přesunul mimo viditelnou část dokumentu. Pokud ano, posuňte dokument kontejneru podle potřeby prostřednictvím volání [ScrollContainerBy](#scrollcontainerby).

##  <a name="getitemposition"></a>COleServerDoc::GetItemPosition

`GetItemPosition` Zavolejte členskou funkci, aby se získaly souřadnice položky upravované na místě.

```
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt pro příjem souřadnic položky.

### <a name="remarks"></a>Poznámky

Souřadnice jsou v pixelech vzhledem k klientské oblasti okna kontejneru aplikace.

Pozice položky může být porovnána s aktuálním obdélníkem oříznutí, aby bylo možné určit rozsah, ve kterém je položka viditelná (nebo není viditelná) na obrazovce.

##  <a name="getzoomfactor"></a>COleServerDoc::GetZoomFactor

`GetZoomFactor` Členská funkce určuje "faktor přiblížení" položky, která byla aktivována pro místní úpravy.

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpSizeNum*<br/>
Ukazatel na objekt třídy `CSize` , který bude obsahovat čitatel faktoru přiblížení. Může mít hodnotu NULL.

*lpSizeDenom*<br/>
Ukazatel na objekt třídy `CSize` , který bude obsahovat jmenovatel faktoru přiblížení. Může mít hodnotu NULL.

*lpPosRect*<br/>
Ukazatel na objekt třídy `CRect` , který popisuje novou pozici položky. Pokud má argument hodnotu NULL, funkce použije aktuální pozici položky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je položka aktivována pro místní úpravy a její faktor přiblížení je jiný než 100% (1:1); v opačném případě 0.

### <a name="remarks"></a>Poznámky

Faktor přiblížení (v pixelech) je poměr velikosti položky k jeho aktuálnímu rozsahu. Pokud aplikace kontejneru nenastaví rozsah položky, použije se její přirozený rozsah (jak Určuje [odvozenou třídu COleServerItem:: OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)).

Funkce nastaví své první dva argumenty na čitatel a jmenovatel "faktor lupy položky". Pokud se položka neupravuje na místě, funkce nastaví tyto argumenty na výchozí hodnotu 100% (nebo 1:1) a vrátí hodnotu nula. Další informace naleznete v části technická Poznámka 40, [změny velikosti a zvětšení umístění v prostředích MFC/OLE](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

##  <a name="isdocobject"></a>COleServerDoc::IsDocObject

Určuje, zda je dokument DocObject.

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je dokument DocObject; v opačném případě FALSE.

##  <a name="isembedded"></a>COleServerDoc::-Embedded

`IsEmbedded` Zavolejte členskou funkci pro zjištění, zda dokument představuje objekt vložený do kontejneru.

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud `COleServerDoc` je objekt dokumentem, který představuje objekt vložený do kontejneru, jinak 0.

### <a name="remarks"></a>Poznámky

Dokument načtený ze souboru není vložený, i když ho může zpracovat aplikace typu kontejner jako odkaz. Dokument, který je vložený v dokumentu kontejneru, se považuje za vložený.

##  <a name="isinplaceactive"></a>COleServerDoc::IsInPlaceActive

`IsInPlaceActive` Zavolejte členskou funkci pro zjištění, zda je položka aktuálně na místě aktivního stavu.

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud `COleServerDoc` je objekt aktivní. v opačném případě 0.

##  <a name="notifychanged"></a>COleServerDoc::NotifyChanged

Voláním této funkce oznamujete všem propojeným položkám připojeným k dokumentu, že se dokument změnil.

```
void NotifyChanged();
```

### <a name="remarks"></a>Poznámky

Obvykle zavoláte tuto funkci poté, co uživatel změní některý z globálních atributů, jako je například dimenze dokumentu serveru. Pokud je položka OLE propojena s dokumentem pomocí automatického propojení, bude položka aktualizována, aby odrážela změny. V kontejnerových aplikacích napsaných pomocí knihovna Microsoft Foundation Class [](../../mfc/reference/coleclientitem-class.md#onchange) `COleClientItem` je volána členská funkce Change.

> [!NOTE]
>  Tato funkce je zahrnutá pro kompatibilitu s OLE 1. Nové aplikace by měly používat [UpdateAllItems](#updateallitems).

##  <a name="notifyclosed"></a>COleServerDoc::NotifyClosed

Voláním této funkce se upozorní na kontejnery, že dokument byl uzavřen.

```
void NotifyClosed();
```

### <a name="remarks"></a>Poznámky

Pokud uživatel zvolí příkaz Zavřít v nabídce soubor, `NotifyClosed` je `COleServerDoc`volána implementací členské funkce [OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument) . V kontejnerových aplikacích napsaných pomocí knihovna Microsoft Foundation Class [](../../mfc/reference/coleclientitem-class.md#onchange) `COleClientItem` je volána členská funkce Change.

##  <a name="notifyrename"></a>COleServerDoc::NotifyRename

Tuto funkci zavolejte poté, co uživatel přejmenuje dokument serveru.

```
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parametry

*lpszNewName*<br/>
Ukazatel na řetězec určující nový název dokumentu serveru; obvykle se jedná o plně kvalifikovanou cestu.

### <a name="remarks"></a>Poznámky

Když uživatel zvolí příkaz Uložit jako v nabídce soubor, `NotifyRename` je `COleServerDoc`volána implementací členské funkce [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument) . Tato funkce upozorní systémové knihovny DLL systému OLE, které zase upozorní kontejnery. V kontejnerových aplikacích napsaných pomocí knihovna Microsoft Foundation Class [](../../mfc/reference/coleclientitem-class.md#onchange) `COleClientItem` je volána členská funkce Change.

##  <a name="notifysaved"></a>COleServerDoc::NotifySaved

Tuto funkci zavolejte poté, co uživatel dokument serveru uloží.

```
void NotifySaved();
```

### <a name="remarks"></a>Poznámky

Když uživatel zvolí příkaz Uložit v nabídce soubor, `NotifySaved` je volána pro `COleServerDoc`vás implementací [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument). Tato funkce upozorní systémové knihovny DLL systému OLE, které zase upozorní kontejnery. V kontejnerových aplikacích napsaných pomocí knihovna Microsoft Foundation Class [](../../mfc/reference/coleclientitem-class.md#onchange) `COleClientItem` je volána členská funkce Change.

##  <a name="onclose"></a>COleServerDoc::-Close

Volá se rozhraním, když kontejner požaduje zavření dokumentu serveru.

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>Parametry

*dwCloseOption*<br/>
Hodnota z výčtu OLECLOSE. Tento parametr může mít jednu z následujících hodnot:

- OLECLOSE_SAVEIFDIRTY soubor se uloží, pokud byl upravený.

- OLECLOSE_NOSAVE soubor je zavřený bez uložení.

- OLECLOSE_PROMPTSAVE Pokud byl soubor upravený, zobrazí se uživateli výzva k jeho uložení.

### <a name="remarks"></a>Poznámky

Výchozí volání `CDocument::OnCloseDocument`implementace.

Další informace a další hodnoty naleznete v tématu [OLECLOSE](/windows/win32/api/oleidl/ne-oleidl-oleclose) v Windows SDK.

##  <a name="ondeactivate"></a>COleServerDoc:: deaktivovat

Volá se rozhraním, když uživatel deaktivuje vloženou nebo propojenou položku, která je aktuálně na místě aktivní.

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>Poznámky

Tato funkce obnoví uživatelské rozhraní aplikace typu kontejner do původního stavu a zničí všechny nabídky a další ovládací prvky, které byly vytvořeny pro místní aktivaci.

Informace o stavu vrácení zpět by měly být v tomto okamžiku bezpodmínečně uvolněny.

Další informace najdete v článku [Aktivace](../../mfc/activation-cpp.md)..

##  <a name="ondeactivateui"></a>COleServerDoc::OnDeactivateUI

Volá se, když uživatel deaktivuje položku, která se aktivovala na místě.

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>Parametry

*bUndoable*<br/>
Určuje, zda lze změny v úpravách vrátit zpět.

### <a name="remarks"></a>Poznámky

Tato funkce obnoví uživatelské rozhraní aplikace typu kontejner do původního stavu, skryje všechny nabídky a další ovládací prvky, které byly vytvořeny pro místní aktivaci.

Rozhraní vždy nastaví *bUndoable* na false. Pokud server podporuje vrácení zpět a existuje operace, která může být vrácena zpět, zavolejte implementaci základní třídy s *bUndoable* nastavenou na hodnotu true.

##  <a name="ondocwindowactivate"></a>  COleServerDoc::OnDocWindowActivate

Rozhraní volá tuto funkci, aby aktivovala nebo deaktivovala okno dokumentu pro místní úpravy.

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
Určuje, zda má být okno dokumentu aktivováno nebo dezaktivováno.

### <a name="remarks"></a>Poznámky

Výchozí implementace odebere nebo přidá prvky uživatelského rozhraní na úrovni rámce podle potřeby. Tuto funkci můžete přepsat, pokud chcete provést další akce, když se dokument obsahující vaši položku aktivuje nebo deaktivuje.

Další informace najdete v článku [Aktivace](../../mfc/activation-cpp.md)..

##  <a name="onexecolecmd"></a>COleServerDoc::OnExecOleCmd

Rozhraní volá tuto funkci k provedení zadaného příkazu nebo zobrazení nápovědu pro příkaz.

```
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,
    DWORD nCmdID,
    DWORD nCmdExecOpt,
    VARIANTARG* pvarargIn,
    VARIANTARG* pvarargOut);
```

### <a name="parameters"></a>Parametry

*pguidCmdGroup*<br/>
Ukazatel na identifikátor GUID, který identifikuje sadu příkazů. Může mít hodnotu NULL, aby označovala výchozí skupinu příkazů.

*nCmdID*<br/>
Příkaz, který má být spuštěn. Musí být ve skupině určené pomocí *pguidCmdGroup*.

*nCmdExecOut*<br/>
Způsob, jakým má objekt spustit příkaz, jednu nebo více z následujících hodnot z výčtu OLECMDEXECOPT:

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pvarargIn*<br/>
Ukazatel na VARIANTARG obsahující vstupní argumenty pro příkaz. Může mít hodnotu NULL.

*pvarargOut*<br/>
Ukazatel na VARIANTARG pro příjem výstupních vrácených hodnot z příkazu. Může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK, pokud bylo úspěšné. v opačném případě jeden z následujících kódů chyb:

|Value|Popis|
|-----------|-----------------|
|E_UNEXPECTED|Stala se neočekávaná chyba.|
|E_FAIL|Došlo k chybě|
|E_NOTIMPL|Indikuje, že by se sama knihovna MFC měla pokusit přeložit a odeslat příkaz.|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* je nenulová, ale neurčuje rozpoznanou skupinu příkazů.|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* se v *pguidCmdGroup* skupiny nedá rozpoznat jako platný příkaz.|
|OLECMDERR_DISABLED|Příkaz identifikovaný *nCmdID* je zakázaný a nedá se spustit.|
|OLECMDERR_NOHELP|Volající se požádal o nápovědu k příkazu identifikovanému funkcí *nCmdID* , ale není k dispozici žádná nápovědu.|
|OLECMDERR_CANCELED|Uživatel zrušil provádění.|

### <a name="remarks"></a>Poznámky

`COleCmdUI`dá se použít k povolení, aktualizaci a nastavení dalších vlastností příkazů uživatelského rozhraní DocObject. Po inicializaci příkazů je můžete spustit pomocí `OnExecOleCmd`příkazu.

Rozhraní volá funkci před pokusem o převod a odeslání příkazu dokumentu OLE. Tuto funkci není nutné potlačit, pokud chcete zpracovat standardní příkazy v dokumentu OLE, ale pokud chcete zpracovávat vlastní příkazy nebo zpracovávat příkazy, které přijímají parametry nebo vrací výsledky, musíte zadat přepsání této funkce.

Většina příkazů nepřijímá argumenty nebo návratové hodnoty. Pro většinu příkazů může volající předat hodnoty NULL pro *pvarargIn* a *pvarargOut*. Pro příkazy, které očekávají vstupní hodnoty, volající může deklarovat a inicializovat proměnnou VARIANTARG a předat ukazatel na proměnnou v *pvarargIn*. Pro příkazy, které vyžadují jednu hodnotu, lze argument uložit přímo v VARIANTARG a předat do funkce. Více argumentů musí být zabaleno v rámci VARIANTARG pomocí jednoho z podporovaných typů (například `IDispatch` a SAFEARRAY).

Podobně platí, že pokud příkaz vrátí argumenty, volající očekává deklarovat VARIANTARG, inicializovat ho pro VT_EMPTY a předat jeho adresu v *pvarargOut*. Pokud příkaz vrátí jednu hodnotu, objekt může tuto hodnotu uložit přímo do *pvarargOut*. Více výstupních hodnot musí být zabaleno nějakým způsobem vhodným pro VARIANTARG.

Implementace základní třídy této funkce provede OLE_COMMAND_MAP struktury přidružené k cíli příkazu a pokusí se odeslat příkaz příslušné obslužné rutině. Implementace základní třídy funguje pouze s příkazy, které nepřijímají argumenty nebo návratové hodnoty. Pokud potřebujete zpracovat příkazy, které akceptují argumenty nebo návratové hodnoty, musíte tuto funkci přepsat a pracovat s parametry *pvarargIn* a *pvarargOut* sami.

##  <a name="onframewindowactivate"></a>COleServerDoc::OnFrameWindowActivate

Rozhraní volá tuto funkci, když se aktivuje nebo deaktivuje okno rámce aplikace kontejneru.

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
Určuje, zda má být okno rámce aktivováno nebo dezaktivováno.

### <a name="remarks"></a>Poznámky

Výchozí implementace zruší všechny režimy, ve kterých se může okno rámce nacházet. Tuto funkci potlačíte, pokud chcete provádět zvláštní zpracování při aktivaci nebo deaktivaci okna rámce.

Další informace najdete v článku [Aktivace](../../mfc/activation-cpp.md)..

##  <a name="ongetembeddeditem"></a>COleServerDoc:: funkci OnGetEmbeddedItem

Volá se rozhraním, když aplikace typu kontejner volá serverovou aplikaci, aby vytvořila nebo upravila vloženou položku.

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na položku představující celý dokument; Hodnota NULL, pokud se operace nezdařila.

### <a name="remarks"></a>Poznámky

Neexistuje žádná výchozí implementace. Tuto funkci musíte přepsat, chcete-li vrátit položku, která představuje celý dokument. Tato návratová hodnota by měla být objektem `COleServerItem`odvozené třídy.

##  <a name="onreactivateandundo"></a>COleServerDoc::OnReactivateAndUndo

Rozhraní volá tuto funkci, když se uživatel rozhodne vrátit zpět změny provedené u položky, která byla aktivována, změněna a následně dezaktivována.

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace nedělá nic s výjimkou vrácení FALSE pro indikaci selhání.

Tuto funkci přepište, pokud vaše aplikace podporuje vrácení zpět. Obvykle byste provedli operaci vrácení zpět a potom aktivovali položku voláním `ActivateInPlace`. Pokud je aplikace kontejneru zapsána s knihovna Microsoft Foundation Class, volání `COleClientItem::ReactivateAndUndo` způsobí, že tato funkce bude volána.

##  <a name="onresizeborder"></a>COleServerDoc::OnResizeBorder

Rozhraní volá tuto funkci, když se změní velikost oken v rámečku aplikace kontejneru.

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>Parametry

*lpRectBorder*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt, který určuje souřadnice ohraničení.

*lpUIWindow*<br/>
Ukazatel na objekt třídy `IOleInPlaceUIWindow` , který vlastní aktuální místní relaci úprav.

*bFrame*<br/>
TRUE, pokud *lpUIWindow* odkazuje na okno rámce nejvyšší úrovně aplikace kontejneru, nebo false, pokud *lpUIWindow* odkazuje na okno rámce na úrovni dokumentu aplikace kontejneru.

### <a name="remarks"></a>Poznámky

Tato funkce změní velikost a upraví panely nástrojů a další prvky uživatelského rozhraní podle nové velikosti okna.

Další informace najdete v tématu [IOleInPlaceUIWindow](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow) v Windows SDK.

Toto je pokročilá přepsatelné.

##  <a name="onsethostnames"></a>  COleServerDoc::OnSetHostNames

Volá se rozhraním, když kontejner nastavuje nebo mění názvy hostitelů pro tento dokument.

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>Parametry

*lpszHost*<br/>
Ukazatel na řetězec, který určuje název aplikace typu kontejner.

*lpszHostObj*<br/>
Ukazatel na řetězec, který určuje název kontejneru pro dokument.

### <a name="remarks"></a>Poznámky

Výchozí implementace změní název dokumentu u všech zobrazení odkazujících na tento dokument.

Tuto funkci přepište, pokud vaše aplikace nastaví názvy pomocí jiného mechanismu.

##  <a name="onsetitemrects"></a>COleServerDoc::OnSetItemRects

Rozhraní volá tuto funkci, aby umístila místní editační okno rámce v rámci okna rámce aplikace kontejneru.

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt, který určuje umístění místního okna rámce vzhledem k klientské oblasti aplikace kontejneru.

*lpClipRect*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt, který určuje obdélník ořezového okna v místě vzhledem k klientské oblasti aplikace kontejneru.

### <a name="remarks"></a>Poznámky

Potlačením této funkce aktualizujete faktor přiblížení zobrazení v případě potřeby.

Tato funkce je obvykle volána jako odpověď na `RequestPositionChange` volání, přestože může být kdykoli volána kontejnerem pro vyžádání změny pozice pro místní položku.

##  <a name="onshowcontrolbars"></a>COleServerDoc::OnShowControlBars

Rozhraní volá tuto funkci, aby zobrazila nebo skryla ovládací prvky serverové aplikace přidružené k oknu rámce identifikovaném na *pFrameWnd*.

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

*pFrameWnd*<br/>
Ukazatel na okno rámce, jehož ovládací panely by měly být skryté nebo zobrazené.

*bShow*<br/>
Určuje, zda jsou ovládací panely zobrazeny nebo skryty.

### <a name="remarks"></a>Poznámky

Výchozí implementace vytvoří výčet všech ovládacích prvků vlastněných oknem tohoto rámce a jeho skrytí nebo zobrazení.

##  <a name="onshowdocument"></a>COleServerDoc::OnShowDocument

Rozhraní volá funkci, `OnShowDocument` když dokument serveru musí být skrytý nebo zobrazený.

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
Určuje, zda se má zobrazit nebo skrýt uživatelské rozhraní dokumentu.

### <a name="remarks"></a>Poznámky

Pokud má *bShow* hodnotu true, výchozí implementace aktivuje serverovou aplikaci, je-li to nutné, a způsobí, že aplikace kontejneru posune své okno tak, aby byla položka viditelná. Pokud má *bShow* hodnotu false, výchozí implementace deaktivuje položku prostřednictvím volání `OnDeactivate`a potom zničí nebo skryje všechna okna oken, která byla vytvořena pro dokument s výjimkou prvního z nich. Pokud žádné viditelné dokumenty nezůstanou, výchozí implementace skryje serverovou aplikaci.

##  <a name="onupdatedocument"></a>COleServerDoc::OnUpdateDocument

Volá se rozhraním při ukládání dokumentu, který je vloženou položkou ve složeném dokumentu.

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se dokument úspěšně aktualizoval; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá členské funkce [COleServerDoc:: NotifySaved](#notifysaved) a [COleServerDoc:: SaveEmbedding](#saveembedding) a označí dokument jako čistý. Tuto funkci můžete přepsat, pokud chcete při aktualizaci vložené položky provést zvláštní zpracování.

##  <a name="requestpositionchange"></a>COleServerDoc::RequestPositionChange

Tuto členskou funkci zavolejte, pokud chcete, aby aplikace kontejneru změnila pozici položky.

```
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt obsahující novou pozici položky.

### <a name="remarks"></a>Poznámky

Tato funkce se obvykle nazývá (ve spojení s `UpdateAllItems`), když se změní data na místní aktivní položce. Po tomto volání kontejner může nebo nemusí provést změnu voláním `OnSetItemRects`. Výsledná pozice se může lišit od toho, co se požaduje.

##  <a name="saveembedding"></a>COleServerDoc::SaveEmbedding

Voláním této funkce sdělíte aplikaci kontejneru, aby uložila vložený objekt.

```
void SaveEmbedding();
```

### <a name="remarks"></a>Poznámky

Tato funkce se nazývá automaticky z `OnUpdateDocument`. Všimněte si, že tato funkce způsobí, že se položka aktualizuje na disku, takže je obvykle volána pouze v důsledku konkrétní akce uživatele.

##  <a name="scrollcontainerby"></a>COleServerDoc::ScrollContainerBy

Zavolejte členskou funkci pro posunutí dokumentu kontejneru o hodnotu v pixelech, kterou `sizeScroll`označuje. `ScrollContainerBy`

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>Parametry

*sizeScroll*<br/>
Určuje, jak daleko má být dokument kontejneru posunut.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Kladné hodnoty označují posun dolů a doprava; záporné hodnoty označují posun nahoru a doleva.

##  <a name="updateallitems"></a>COleServerDoc::UpdateAllItems

Voláním této funkce oznamujete všem propojeným položkám připojeným k dokumentu, že se dokument změnil.

```
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Ukazatel na položku, která změnila dokument, nebo hodnotu NULL, pokud mají být aktualizovány všechny položky.

*lHint*<br/>
Obsahuje informace o změně.

*pHint*<br/>
Ukazatel na objekt, který ukládá informace o změně.

*nDrawAspect*<br/>
Určuje, jak má být položka vykreslena. Toto je hodnota z výčtu DVASPECT. Tento parametr může mít jednu z následujících hodnot:

- Položka DVASPECT_CONTENT je reprezentovaná takovým způsobem, že se dá zobrazit jako vložený objekt uvnitř kontejneru.

- Položka DVASPECT_THUMBNAIL se vykresluje v "miniatuře" reprezentace, aby se mohla zobrazit v nástroji pro procházení.

- Položka DVASPECT_ICON je reprezentována ikonou.

- Položka DVASPECT_DOCPRINT je reprezentována, jako kdyby byla vytištěna pomocí příkazu Print v nabídce soubor.

### <a name="remarks"></a>Poznámky

Tato funkce se obvykle volá poté, co uživatel změní dokument serveru. Pokud je položka OLE propojena s dokumentem pomocí automatického propojení, bude položka aktualizována, aby odrážela změny. V kontejnerových aplikacích napsaných pomocí knihovna Microsoft Foundation Class [](../../mfc/reference/coleclientitem-class.md#onchange) `COleClientItem` je volána členská funkce Change.

`OnUpdate` Tato funkce volá členskou funkci pro každou položku dokumentu s výjimkou odesílající položky, předávání *pHint*, *lHint*a *nDrawAspect*. Pomocí těchto parametrů můžete předat informace k položkám o změnách provedených v dokumentu. Můžete kódovat informace pomocí *lHint* nebo můžete definovat `CObject`třídu odvozenou pro ukládání informací o úpravách a předání objektu této třídy pomocí *pHint*. Přepište `COleServerItem`členskou funkci v odvozené třídě k optimalizaci aktualizace každé položky v závislosti na tom, zda se její prezentace změnila. `OnUpdate`

## <a name="see-also"></a>Viz také:

[HIERSVR Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[COleLinkingDoc – třída](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDocument – třída](../../mfc/reference/coledocument-class.md)<br/>
[COleLinkingDoc – třída](../../mfc/reference/colelinkingdoc-class.md)<br/>
[COleTemplateServer – třída](../../mfc/reference/coletemplateserver-class.md)
