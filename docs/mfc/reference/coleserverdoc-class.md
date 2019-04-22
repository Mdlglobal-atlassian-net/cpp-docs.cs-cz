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
ms.openlocfilehash: 4cada70723c7fadc9c91c40380b8a7e9fc46a07a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58777256"
---
# <a name="coleserverdoc-class"></a>COleServerDoc Class

Základní třída pro dokumenty OLE na serveru.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleServerDoc::COleServerDoc](#coleserverdoc)|Vytvoří `COleServerDoc` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleServerDoc::ActivateDocObject](#activatedocobject)|Aktivuje přidružený dokument DocObject.|
|[COleServerDoc::ActivateInPlace](#activateinplace)|Aktivuje dokument pro místní úpravy.|
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|Deaktivuje uživatelské rozhraní serveru.|
|[COleServerDoc::DiscardUndoState](#discardundostate)|Zahodí informace o stavu vrácení zpět.|
|[COleServerDoc::GetClientSite](#getclientsite)|Načte ukazatel na základní `IOleClientSite` rozhraní.|
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|Vrací ukazatel na položku představující celý dokument.|
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|Vrátí aktuální obdélník oříznutí pro místní úpravy.|
|[COleServerDoc::GetItemPosition](#getitemposition)|Vrátí aktuální pozici obdélníku vzhledem ke klientské oblasti aplikace typu kontejner, pro místní úpravy.|
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|Vrátí na faktor zvětšování v pixelech.|
|[COleServerDoc::IsDocObject](#isdocobject)|Určuje, jestli dokument DocObject.|
|[COleServerDoc::IsEmbedded](#isembedded)|Označuje, zda je dokument vložený v dokumentu kontejneru nebo spuštění samostatné.|
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|Vrátí hodnotu PRAVDA, pokud položka je aktuálně aktivovaná na místě.|
|[COleServerDoc::NotifyChanged](#notifychanged)|Upozorní kontejnery, že uživatel změnil dokumentu.|
|[COleServerDoc::NotifyClosed](#notifyclosed)|Upozorní kontejnery, že uživatel má zavření dokumentu.|
|[COleServerDoc::NotifyRename](#notifyrename)|Upozorní kontejnery, že uživatel má přejmenovat dokumentu.|
|[COleServerDoc::NotifySaved](#notifysaved)|Upozorní kontejnery, že uživatel má dokument uložen.|
|[COleServerDoc::OnDeactivate](#ondeactivate)|Volá se rozhraním, když uživatel deaktivuje položku, která se aktivovala na místě.|
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|Volá se rozhraním ke zničení ovládacích prvků a další prvky uživatelského rozhraní pro aktivace na místě vytvořit.|
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|Volá se rozhraním, když se aktivuje nebo deaktivuje okno rámce kontejner dokumentů.|
|[COleServerDoc::OnResizeBorder](#onresizeborder)|Volá se rozhraním při změně velikosti okna dokumentu nebo okno rámce aplikace kontejneru.|
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|Volá se rozhraním, které chcete zobrazit nebo skrýt ovládací pruhy pro místní úpravy.|
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|Volá se rozhraním při uložení dokumentu serveru, který je vložená položka aktualizaci kontejneru kopie položky.|
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|Změní pozici úpravy rámečkem na místě.|
|[COleServerDoc::SaveEmbedding](#saveembedding)|Říká aplikace typu kontejner pro uložení dokumentu.|
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|Posune dokument kontejneru.|
|[COleServerDoc::UpdateAllItems](#updateallitems)|Upozorní kontejnery, že uživatel změnil dokumentu.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|Volá se rozhraním, chcete-li vytvořit okno rámce pro místní úpravy.|
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|Volá se rozhraním zničit okno rámce pro místní úpravy.|
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|Přepsání této funkce můžete vytvořit nový `CDocObjectServer` objektu a označení, že tento dokument je kontejner DocObject.|
|[COleServerDoc::OnClose](#onclose)|Volá se rozhraním, když kontejner požaduje zavření dokumentu.|
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|Provede zadaný příkaz nebo zobrazí nápovědu pro příkaz.|
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|Volá se rozhraním, když se aktivuje nebo deaktivuje okno rámce kontejneru.|
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|Volá za účelem získání `COleServerItem` , který představuje celý dokument; použít k získání vloženou položku. Implementace vyžaduje.|
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|Volá se rozhraním, které chcete vrátit zpět změny provedené při místní úpravy.|
|[COleServerDoc::OnSetHostNames](#onsethostnames)|Volá se rozhraním, když kontejner nastavuje název okna pro vložený objekt.|
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|Volá se rozhraním, které chcete umístit okno místní úpravy rámce okna aplikace typu kontejner.|
|[COleServerDoc::OnShowDocument](#onshowdocument)|Volá se rozhraním, zobrazení nebo skrytí dokumentu.|

## <a name="remarks"></a>Poznámky

Dokument na serveru může obsahovat [odvozenou třídu COleServerItem](../../mfc/reference/coleserveritem-class.md) objekty, které představují rozhraní serveru vložené nebo propojené položky. Při spuštění serverové aplikace v kontejneru do upravila vložená položka. položka je načtena jako svůj vlastní server dokumentu. `COleServerDoc` objekt obsahuje pouze jeden `COleServerItem` objekt, který se skládá z celý dokument. Při spuštění serverové aplikace v kontejneru můžete upravit propojené položky existující dokument je načten z disku k označení propojená položka je zvýrazněn část obsahu dokumentu.

`COleServerDoc` objekty mohou také obsahovat položky [COleClientItem](../../mfc/reference/coleclientitem-class.md) třídy. To umožňuje vytvořit kontejner serverových aplikací. Rozhraní poskytuje funkce pro ukládání správně `COleClientItem` položky během obsluhy `COleServerItem` objekty.

Pokud vaše serverová aplikace nepodporuje odkazy, bude dokument na serveru vždy obsahovat pouze jednu položku server, který představuje celou vloženého objektu jako dokument. Pokud vaše serverová aplikace nepodporuje odkazy, musí vytvořit položku serveru při každém výběru je zkopírován do schránky.

Použití `COleServerDoc`odvodit třídu z něj a implementovat [OnGetEmbeddedItem](#ongetembeddeditem) členskou funkci, která umožňuje serveru pro podporu vložené položky. Odvodit třídu z `COleServerItem` implementace položek v dokumentech a vrací objekty z této třídy `OnGetEmbeddedItem`.

Pro podporu propojené položky `COleServerDoc` poskytuje [OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) členskou funkci. Můžete použít výchozí implementace nebo ho přepsat, pokud budete mít vlastní způsob, jak Správa položek dokumentu.

Budete potřebovat `COleServerDoc`-odvozené třídy pro každý typ serveru dokumentů vaše aplikace podporuje. Například pokud vaše serverová aplikace podporuje listů a grafy, potřebujete dva `COleServerDoc`-odvozené třídy.

Další informace o serverech, najdete v článku [serverů: Implementace serveru](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

##  <a name="activatedocobject"></a>  COleServerDoc::ActivateDocObject

Aktivuje přidružený dokument DocObject.

```
void ActivateDocObject();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `COleServerDoc` nepodporuje aktivní dokumenty (také označované jako DocObjects). Pokud chcete povolit tuto podporu, najdete v článku [GetDocObjectServer](#getdocobjectserver) a třída [cdocobjectserver –](../../mfc/reference/cdocobjectserver-class.md).

##  <a name="activateinplace"></a>  COleServerDoc::ActivateInPlace

Aktivuje položku pro místní úpravy.

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. v opačném případě 0, což znamená, že položka je zcela otevřená.

### <a name="remarks"></a>Poznámky

Tato funkce provede všechny operace, které jsou nezbytné pro aktivace na místě. Ho vytvoří okno rámečkem na místě, aktivuje se ji s položkou o velikosti, nastaví sdílených nabídek a další ovládací prvky, položky se posune do zobrazení a nastaví fokus do okna s rámečkem na místě.

Tato funkce se volá výchozí implementace [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow). Voláním této funkce, pokud vaše aplikace podporuje další příkaz k aktivaci na místě (například Play).

##  <a name="coleserverdoc"></a>  COleServerDoc::COleServerDoc

Vytvoří `COleServerDoc` objektu bez připojení s OLE systémové knihovny DLL.

```
COleServerDoc();
```

### <a name="remarks"></a>Poznámky

Je nutné volat [COleLinkingDoc::Register](../../mfc/reference/colelinkingdoc-class.md#register) otevřete komunikace s OLE. Pokud používáte [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) ve vaší aplikaci `COleLinkingDoc::Register` nazývá aplikací `COleLinkingDoc`vaší implementace `OnNewDocument`, `OnOpenDocument`, a `OnSaveDocument`.

##  <a name="createinplaceframe"></a>  COleServerDoc::CreateInPlaceFrame

Rozhraní volá tuto funkci, která vytvoří okno rámce pro místní úpravy.

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel do nadřazeného okna aplikace typu kontejner.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okna s rámečkem na místě, nebo hodnota NULL, pokud je neúspěšná.

### <a name="remarks"></a>Poznámky

Výchozí implementace používá informace zadané v šabloně dokumentu. Chcete-li vytvořit snímek. Zobrazení použité je první zobrazení vytvořené pro dokument. Toto zobrazení je dočasně odpojeno od původního rámce a připojit k nově vytvořený rámce.

To je moderní overridable.

##  <a name="deactivateandundo"></a>  COleServerDoc::DeactivateAndUndo

Voláním této funkce, pokud vaše aplikace podporuje zpět a uživatel vybere možnost vrácení zpět po aktivaci položky, ale začnete upravovat.

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu; nenulovou hodnotu. jinak 0.

### <a name="remarks"></a>Poznámky

Pokud aplikace typu kontejner je zapsáno s použitím knihovny Microsoft Foundation Class, volání této funkce způsobí, že [COleClientItem::OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) k volání, které uživatelské rozhraní serveru deaktivuje.

##  <a name="destroyinplaceframe"></a>  COleServerDoc::DestroyInPlaceFrame

Rozhraní volá tuto funkci zničení oken rámečkem na místě a vrátíte se na serveru okno dokumentu aplikace do stavu před aktivace na místě.

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parametry

*pFrameWnd*<br/>
Ukazatel do okna rámečkem na místě, který se má zničit.

### <a name="remarks"></a>Poznámky

To je moderní overridable.

##  <a name="discardundostate"></a>  COleServerDoc::DiscardUndoState

Pokud uživatel provede operaci úprav, která není možné vrátit zpět, volejte tuto funkci a vynuťte aplikace typu kontejner se zahodit informací o stavu zpět.

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu; nenulovou hodnotu. jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je poskytována tak, aby servery, které podporují zpět můžete uvolnit prostředky, které by jinak stav vracení zpět informace, které nelze použít.

##  <a name="getclientsite"></a>  COleServerDoc::GetClientSite

Načte ukazatel na základní `IOleClientSite` rozhraní.

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>Návratová hodnota

Načte ukazatel na základní [IOleClientSite](/windows/desktop/api/oleidl/nn-oleidl-ioleclientsite) rozhraní.

##  <a name="getdocobjectserver"></a>  COleServerDoc::GetDocObjectServer

Přepsání této funkce můžete vytvořit nový `CDocObjectServer` položky a vrácen ukazatel na ni.

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>Parametry

*pDocSite*<br/>
Ukazatel `IOleDocumentSite` rozhraní, které tento dokument se připojí k serveru.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CDocObjectServer`; Hodnota NULL, pokud se operace nezdařila.

### <a name="remarks"></a>Poznámky

Po aktivaci zcela DocObject server vrátit NENULOVÝ ukazatel ukazuje, že klient může podporovat DocObjects. Výchozí implementace vrací hodnotu NULL.

Obvyklá implementace pro dokument, který podporuje DocObjects jednoduše přidělit nový `CDocObjectServer` objekt a vracet volajícímu. Příklad:

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

##  <a name="getembeddeditem"></a>  COleServerDoc::GetEmbeddedItem

Voláním této funkce získání ukazatele na položku představující celý dokument.

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na položku představující celého dokumentu. Hodnota NULL, pokud se operace nezdařila.

### <a name="remarks"></a>Poznámky

Volá [COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem), virtuální funkce s žádná výchozí implementaci.

##  <a name="getitemcliprect"></a>  COleServerDoc::GetItemClipRect

Volání `GetItemClipRect` členskou funkci zobrazíte obdélník oříznutí souřadnice položky, který je zpracováván na místě.

```
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>Parametry

*lpClipRect*<br/>
Ukazatel na `RECT` struktury nebo `CRect` objektu pro příjem obdélník oříznutí souřadnice položky.

### <a name="remarks"></a>Poznámky

Souřadnice jsou uváděny v pixelech vzhledem ke klientské oblasti okna aplikace kontejneru.

Kreslení by nemělo dojít mimo obdélník oříznutí. Kreslení je obvykle automaticky s omezeným přístupem. Tato funkce slouží k určení, zda má uživatel přešli mimo viditelnou část dokumentu. Pokud ano, posuňte dokumentu kontejneru podle potřeby prostřednictvím volání [ScrollContainerBy](#scrollcontainerby).

##  <a name="getitemposition"></a>  COleServerDoc::GetItemPosition

Volání `GetItemPosition` členskou funkci, aby se získaly souřadnice položky, který právě upravujete na místě.

```
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Ukazatel na `RECT` struktury nebo `CRect` objektu získat souřadnice položky.

### <a name="remarks"></a>Poznámky

Souřadnice jsou uváděny v pixelech vzhledem ke klientské oblasti okna aplikace kontejneru.

Umístění položky lze porovnat s aktuální obdélník oříznutí k určení rozsahu, ke kterému je položka viditelná (nebo ho nevidí.) na obrazovce.

##  <a name="getzoomfactor"></a>  COleServerDoc::GetZoomFactor

`GetZoomFactor` Členská funkce určuje "faktor zvětšování" položky, která se aktivovala pro místní úpravy.

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpSizeNum*<br/>
Ukazatel na objekt třídy `CSize` , který bude obsahovat čitatel na faktor zvětšování. Může mít hodnotu NULL.

*lpSizeDenom*<br/>
Ukazatel na objekt třídy `CSize` , který bude obsahovat jmenovatel na faktor zvětšování. Může mít hodnotu NULL.

*lpPosRect*<br/>
Ukazatel na objekt třídy `CRect` , který popisuje novou pozici položky. Pokud tento argument je NULL, funkce používá aktuální pozici položky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud položka aktivuje pro místní úpravy a jeho faktor zvětšování je jiného než 100 % (1:1); jinak 0.

### <a name="remarks"></a>Poznámky

Faktor zvětšení v pixelech, je poměr velikost položky na aktuální velikost. Pokud aplikace typu kontejner nenastavil položky v rozsahu, jeho fyzické rozsah (počítáno od [COleServerItem::OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)) se používá.

Funkce nastaví jeho prvních dvou argumentů čitatelem a jmenovatelem položky "faktor zvětšování." Pokud položka není upravovaný na místě, funkce nastaví na výchozí hodnotu 100 % (nebo 1:1) tyto argumenty a vrátí hodnotu 0. Další informace najdete v tématu Technická poznámka 40 [MFC/OLE – místní změny velikosti a Zooming](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

##  <a name="isdocobject"></a>  COleServerDoc::IsDocObject

Určuje, jestli dokument DocObject.

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je dokument DocObject; v opačném případě FALSE.

##  <a name="isembedded"></a>  COleServerDoc::IsEmbedded

Volání `IsEmbedded` členskou funkci k určení, jestli dokument představuje objekt vložen do kontejneru.

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud `COleServerDoc` objektu je dokument, který představuje objekt vložený v kontejneru; jinak 0.

### <a name="remarks"></a>Poznámky

I když může být používán aplikace typu kontejner jako odkaz není vložený dokument načtený ze souboru. Dokument, který je vložený v dokumentu kontejneru se považuje za vložit.

##  <a name="isinplaceactive"></a>  COleServerDoc::IsInPlaceActive

Volání `IsInPlaceActive` členská funkce určuje, jestli položka je aktuálně v aktivním stavu na místě.

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud `COleServerDoc` objekt je aktivní v místě, jinak 0.

##  <a name="notifychanged"></a>  COleServerDoc::NotifyChanged

Voláním této funkce upozornění na všechny propojené položky, které jsou připojené k dokumentu, který dokument se změnil.

```
void NotifyChanged();
```

### <a name="remarks"></a>Poznámky

Poté, co uživatel změní některé globální atribut jako je například dimenze dokumentu na serveru se obvykle voláním této funkce. Pokud položka OLE je propojený s dokumentu s odkazem pro automatické, je položka aktualizována tak, aby odrážely změny. V kontejneru aplikací napsaných pomocí knihovny Microsoft Foundation Class [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) členskou funkci `COleClientItem` je volána.

> [!NOTE]
>  Tato funkce je zahrnuto pro kompatibilitu s OLE 1. Nová aplikace by měly používat [UpdateAllItems](#updateallitems).

##  <a name="notifyclosed"></a>  COleServerDoc::NotifyClosed

Voláním této funkce upozornění kontejnery, že dokument byla uzavřena.

```
void NotifyClosed();
```

### <a name="remarks"></a>Poznámky

Když uživatel vybere příkaz Zavřít z nabídky Soubor `NotifyClosed` je volán `COleServerDoc`provádění [OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument) členskou funkci. V kontejneru aplikací napsaných pomocí knihovny Microsoft Foundation Class [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) členskou funkci `COleClientItem` je volána.

##  <a name="notifyrename"></a>  COleServerDoc::NotifyRename

Voláním této funkce poté, co uživatel přejmenuje dokumentu na serveru.

```
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parametry

*lpszNewName*<br/>
Ukazatel na řetězec zadáte nový název serveru dokumentu. Obvykle se jedná o plně kvalifikovanou cestu.

### <a name="remarks"></a>Poznámky

Když se uživatel rozhodne příkazu Uložit jako, v nabídce Soubor `NotifyRename` je volán `COleServerDoc`vaší implementace [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument) členskou funkci. Tato funkce upozorní systém OLE knihovny DLL, které zase oznámí kontejnery. V kontejneru aplikací napsaných pomocí knihovny Microsoft Foundation Class [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) členskou funkci `COleClientItem` je volána.

##  <a name="notifysaved"></a>  COleServerDoc::NotifySaved

Voláním této funkce poté, co uživatel uloží dokumentu na serveru.

```
void NotifySaved();
```

### <a name="remarks"></a>Poznámky

Když uživatel vybere příkaz Uložit v nabídce Soubor `NotifySaved` nazývá aplikací `COleServerDoc`vaší implementace [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument). Tato funkce upozorní systém OLE knihovny DLL, které zase oznámí kontejnery. V kontejneru aplikací napsaných pomocí knihovny Microsoft Foundation Class [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) členskou funkci `COleClientItem` je volána.

##  <a name="onclose"></a>  COleServerDoc::OnClose

Volá se rozhraním, když kontejner požaduje zavřít serverem dokumentu.

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>Parametry

*dwCloseOption*<br/>
Hodnota z výčtu OLECLOSE. Tento parametr může mít jednu z následujících hodnot:

- OLECLOSE_SAVEIFDIRTY soubor je uložen, pokud byl změněn.

- OLECLOSE_NOSAVE soubor bude uzavřeno bez uložení.

- OLECLOSE_PROMPTSAVE Pokud soubor byl změněn, bude uživatel vyzván o uložení.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá `CDocument::OnCloseDocument`.

Další informace a další hodnoty, najdete v článku [OLECLOSE](/windows/desktop/api/oleidl/ne-oleidl-tagoleclose) v sadě Windows SDK.

##  <a name="ondeactivate"></a>  COleServerDoc::OnDeactivate

Volá se rozhraním, když uživatel deaktivuje položku vložený nebo připojený, který je aktuálně v místě aktivní.

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>Poznámky

Tato funkce obnoví uživatelské rozhraní aplikace typu kontejner do původního stavu a odstraní všechny nabídky a další ovládací prvky, které byly vytvořeny pro aktivace na místě.

Informace o stavu vrácení zpět by měly být vydány bezpodmínečně v tomto okamžiku.

Další informace najdete v článku [aktivace](../../mfc/activation-cpp.md)...

##  <a name="ondeactivateui"></a>  COleServerDoc::OnDeactivateUI

Volá se, když uživatel deaktivuje položku, která se aktivovala na místě.

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>Parametry

*bUndoable*<br/>
Určuje, zda je možné vrátit zpět změny.

### <a name="remarks"></a>Poznámky

Tato funkce obnoví uživatelské rozhraní aplikace typu kontejner do původního stavu, skrytí všechny nabídky a další ovládací prvky, které byly vytvořeny pro aktivace na místě.

Rozhraní framework vždy nastavuje *bUndoable* na hodnotu FALSE. Pokud server podporuje vrácení zpět a operace, která lze vrátit zpět, volat implementaci základní třídy s *bUndoable* nastavena na hodnotu TRUE.

##  <a name="ondocwindowactivate"></a>  COleServerDoc::OnDocWindowActivate

Rozhraní volá tuto funkci aktivovat nebo deaktivovat okno dokumentu pro místní úpravy.

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
Určuje, zda okno dokumentu se aktivuje nebo deaktivuje.

### <a name="remarks"></a>Poznámky

Výchozí implementace odstraní nebo přidá prvky úrovni snímků uživatelského rozhraní podle potřeby. Tato funkce přepište, pokud chcete provádět další akce, když se aktivuje nebo deaktivuje dokument obsahující vaši položku.

Další informace najdete v článku [aktivace](../../mfc/activation-cpp.md)...

##  <a name="onexecolecmd"></a>  COleServerDoc::OnExecOleCmd

Rozhraní volá tuto funkci a spustit zadaný příkaz zobrazit nápovědu pro příkaz.

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
Ukazatel na identifikátor GUID, který identifikuje sadu příkazů. Může mít hodnotu NULL označuje výchozí příkaz skupiny.

*nCmdID*<br/>
Příkaz ke spuštění. Musí být ve skupině identifikovaný *pguidCmdGroup*.

*nCmdExecOut*<br/>
Způsob, jakým objekt by měl spustit příkaz, jednu nebo více z následujících hodnot z výčtu OLECMDEXECOPT:

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pvarargIn*<br/>
Ukazatel na VARIANTARG obsahující vstupní argumenty pro příkaz. Může mít hodnotu NULL.

*pvarargOut*<br/>
Ukazatel na VARIANTARG získat výstup návratové hodnoty z příkazu. Může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK v případě úspěchu; jinak, jeden z následující kódy chyb:

|Hodnota|Popis|
|-----------|-----------------|
|E_UNEXPECTED, JE-|Došlo k neočekávané chybě.|
|E_FAIL|Došlo k chybě.|
|E_NOTIMPL|Označuje MFC sama má pokusit o přeložení a odeslání příkazu|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* je jiná než NULL, ale neurčuje skupinu rozpoznaný příkaz|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* nebyl rozpoznán jako platný příkaz ve skupině *pguidCmdGroup*|
|OLECMDERR_DISABLED|Příkaz určený *nCmdID* zakázána a nemůže být proveden,|
|OLECMDERR_NOHELP|Volající požádali o pomoc na příkaz určený *nCmdID* , ale není k dispozici žádná Nápověda|
|OLECMDERR_CANCELED|Uživatel zrušil provádění|

### <a name="remarks"></a>Poznámky

`COleCmdUI` slouží k povolení, aktualizovat a nastavit další vlastnosti DocObject uživatelských rozhraní příkazů. Příkazy jsou inicializovány, můžete spouštět pomocí `OnExecOleCmd`.

Rozhraní volá funkci před pokusem o přeložení a odeslání příkazu k dokumentu OLE. Není nutné přepsat tuto funkci pro zpracování standardní příkazy dokumentu OLE, ale pokud chcete zpracovat vlastních příkazů nebo zpracovat příkazy, které přijímají parametry nebo vrací výsledky, je nutné zadat přepsání pro tuto funkci.

Většina příkazů přijímají argumenty ani návratové hodnoty. Pro většinu příkazů volající můžete předat hodnoty Null *pvarargIn* a *pvarargOut*. Příkazy, které očekávají vstupní hodnoty, můžete deklarovat a inicializovat proměnnou VARIANTARG a předat ukazatel k proměnné v volající *pvarargIn*. Příkazy, které vyžadují jednu hodnotu můžete ukládána přímo VARIANTARG argument a předané funkci. Více argumentů musí být zabaleny v rámci VARIANTARG pomocí jedné z podporovaných typů (například `IDispatch` a SAFEARRAY).

Podobně, pokud příkaz vrátí argumenty volající by měl deklarovat VARIANTARG, inicializace VT_EMPTY a předat adresu v *pvarargOut*. Pokud příkaz vrátí jednu hodnotu, objektu lze uložit hodnotu přímo v *pvarargOut*. Více výstupní hodnoty musí být zabaleny nějakým způsobem vhodné pro VARIANTARG.

Implementace základní třídy tuto funkci se provedou struktury OLE_COMMAND_MAP přidružený k daném cíli příkazu a zkuste odeslat příkaz, který má odpovídajícího popisovače. Implementace základní třídy funguje pouze s příkazy, které přijímají argumenty nebo návratové hodnoty. Pokud potřebujete zpracovávat příkazy, které přijímají argumenty nebo návratové hodnoty, musí přepsat tuto funkci a pracovat *pvarargIn* a *pvarargOut* parametry sami.

##  <a name="onframewindowactivate"></a>  COleServerDoc::OnFrameWindowActivate

Rozhraní volá tuto funkci, když se aktivuje nebo deaktivuje okno rámce aplikace kontejneru.

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
Určuje, zda je okno rámce aktivuje nebo deaktivuje.

### <a name="remarks"></a>Poznámky

Výchozí implementace zruší všechny režimy nápovědy oknem rámce je možné. Tato funkce přepište, pokud chcete provést zvláštní zpracování, když se aktivuje nebo deaktivuje okno rámce.

Další informace najdete v článku [aktivace](../../mfc/activation-cpp.md)...

##  <a name="ongetembeddeditem"></a>  COleServerDoc::OnGetEmbeddedItem

Volá se rozhraním, když aplikace typu kontejner volá se serverová aplikace mohla vytvořit nebo upravila vložená položka.

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na položku představující celého dokumentu. Hodnota NULL, pokud se operace nezdařila.

### <a name="remarks"></a>Poznámky

Neexistuje žádný výchozí implementaci. Je nutné přepsat této funkci vrátíte položku, která představuje celý dokument. Tato návratová hodnota by měla být objekt `COleServerItem`-odvozené třídy.

##  <a name="onreactivateandundo"></a>  COleServerDoc::OnReactivateAndUndo

Rozhraní volá tuto funkci, když se uživatel rozhodne vrátit zpět změny položky, která se aktivuje na místě, změnit a následně deaktivovat.

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovede žádnou akci s tím rozdílem, vrátí hodnotu FALSE k označení selhání.

Tato funkce přepište, pokud vaše aplikace podporuje vrácení zpět. Obvykle provést operaci vrácení zpět a potom aktivovat položky voláním `ActivateInPlace`. Pokud aplikace typu kontejner pomocí knihovny Microsoft Foundation Class, volání `COleClientItem::ReactivateAndUndo` způsobí, že tuto funkci, která se má volat.

##  <a name="onresizeborder"></a>  COleServerDoc::OnResizeBorder

Rozhraní volá tuto funkci při změně velikosti oken s rámečkem v kontejneru aplikace.

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>Parametry

*lpRectBorder*<br/>
Ukazatel `RECT` struktury nebo `CRect` objekt, který určuje souřadnice ohraničení.

*lpUIWindow*<br/>
Ukazatel na objekt třídy `IOleInPlaceUIWindow` , který vlastní aktuální místní relaci.

*bFrame*<br/>
Hodnota TRUE v případě *lpUIWindow* odkazuje na okno rámce nejvyšší úrovně aplikace typu kontejner nebo FALSE v případě *lpUIWindow* odkazuje na okno rámce na úrovni dokumentu aplikace typu kontejner.

### <a name="remarks"></a>Poznámky

Tato funkce změní velikost a upraví panely nástrojů a další prvky uživatelského rozhraní v souladu s novou velikost okna.

Další informace najdete v tématu [IOleInPlaceUIWindow](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceuiwindow) v sadě Windows SDK.

To je moderní overridable.

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

Výchozí implementace změní název dokumentu pro všechna zobrazení odkazující na tento dokument.

Potlačí tuto funkci v případě, že aplikace nastaví názvy prostřednictvím jiným způsobem.

##  <a name="onsetitemrects"></a>  COleServerDoc::OnSetItemRects

Rozhraní volá tuto funkci na pozici v rámci okna rámce aplikace kontejneru. úpravy okno rámce na místě.

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Ukazatel `RECT` struktury nebo `CRect` objekt, který určuje pozici okna rámečkem na místě vzhledem ke klientské oblasti aplikace typu kontejner.

*lpClipRect*<br/>
Ukazatel `RECT` struktury nebo `CRect` objekt, který určuje měřítko obdélníku oříznutí okno rámce místní vzhledem ke klientské oblasti aplikace typu kontejner.

### <a name="remarks"></a>Poznámky

Potlačí tuto funkci k aktualizaci zobrazení na faktor zvětšování, v případě potřeby.

Tato funkce je obvykle volána v reakci `RequestPositionChange` zavolat, i když je možné vyvolat v každém okamžiku v kontejneru požadavek na změnu umístění pro místní položku.

##  <a name="onshowcontrolbars"></a>  COleServerDoc::OnShowControlBars

Rozhraní volá tuto funkci můžete zobrazit nebo skrýt ovládací pruhy serverová aplikace spojená s oknem rámce, který je identifikován *pFrameWnd*.

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

*pFrameWnd*<br/>
Ukazatel na okno rámce, jehož ovládací pruhy by měl být skrytí nebo zobrazení.

*bShow*<br/>
Určuje, zda ovládací pruhy zobrazený nebo skrytý.

### <a name="remarks"></a>Poznámky

Výchozí implementace vytvoří výčet všech ovládací pruhy vlastníkem tohoto okna rámce a skryje nebo zobrazí je.

##  <a name="onshowdocument"></a>  COleServerDoc::OnShowDocument

Rámec volá `OnShowDocument` fungovat v případě, že dokument serveru musí být skrytí nebo zobrazení.

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
Určuje, zda uživatelské rozhraní pro dokument je zobrazen nebo skryt.

### <a name="remarks"></a>Poznámky

Pokud *bShow* hodnotu TRUE, je výchozí implementace serverové aplikace, aktivuje v případě potřeby a způsobí, že aplikace typu kontejner posouvat její okno tak, že je položka viditelná. Pokud *bShow* má hodnotu FALSE, výchozí implementace deaktivuje položku přímo pomocí volání `OnDeactivate`, odstraní nebo skryje všechny oken s rámečkem vytvořené pro dokument, s výjimkou první z nich. Pokud žádné viditelné dokumenty zůstanou, výchozí implementace skryje serverová aplikace.

##  <a name="onupdatedocument"></a>  COleServerDoc::OnUpdateDocument

Volá se rozhraním při ukládání dokumentu, který je vložená položka ve složeném dokumentu.

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dokument byl úspěšně aktualizován; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá [COleServerDoc::NotifySaved](#notifysaved) a [COleServerDoc::SaveEmbedding](#saveembedding) členské funkce a pak označí jako vyčistit dokument. Tato funkce přepište, pokud chcete provést zvláštní zpracování při aktualizaci vloženou položku.

##  <a name="requestpositionchange"></a>  COleServerDoc::RequestPositionChange

Voláním této členské funkce, aby aplikace typu kontejner změní pozici položky.

```
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Ukazatel `RECT` struktury nebo `CRect` objekt, který obsahuje novou pozici položky.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána (ve spojení s `UpdateAllItems`) změny dat v aktivní položky v místě. Po tomto volání kontejneru může nebo nemusí provést změnu voláním `OnSetItemRects`. Výsledné umístění se může lišit od požadované.

##  <a name="saveembedding"></a>  COleServerDoc::SaveEmbedding

Voláním této funkce předat aplikace typu kontejner pro uložení vloženého objektu.

```
void SaveEmbedding();
```

### <a name="remarks"></a>Poznámky

Tato funkce je volána automaticky `OnUpdateDocument`. Všimněte si, že tato funkce způsobí, že položka aktualizovat na disku, takže je obvykle volána pouze v důsledku akcí konkrétního uživatele.

##  <a name="scrollcontainerby"></a>  COleServerDoc::ScrollContainerBy

Volání `ScrollContainerBy` členskou funkci posouvat dokumentu kontejneru vzdálenost v pixelech, indikován `sizeScroll`.

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>Parametry

*sizeScroll*<br/>
Určuje, jak daleko je dokumentu kontejneru posouvat.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Kladné hodnoty udávají posun dolů a doprava; záporné hodnoty označují posouvání nahoru a doleva.

##  <a name="updateallitems"></a>  COleServerDoc::UpdateAllItems

Voláním této funkce upozornění na všechny propojené položky, které jsou připojené k dokumentu, který dokument se změnil.

```
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Ukazatel na položku, která upravit dokument, nebo hodnota NULL, pokud jsou všechny položky aktualizovat.

*lHint*<br/>
Obsahuje informace o změnu.

*pHint*<br/>
Ukazatel na objekt ukládání informací o změnu.

*nDrawAspect*<br/>
Určuje, jak má být vykreslen položky. Jedná se o hodnotu z výčtu DVASPECT. Tento parametr může mít jednu z následujících hodnot:

- Položky DVASPECT_CONTENT je reprezentována způsobem, že může být zobrazen jako vložený objekt uvnitř svého kontejneru.

- DVASPECT_THUMBNAIL položky se vykreslí v reprezentaci "miniaturu" tak, aby ji bylo možné zobrazit v nástroji pro procházení.

- Položka DVASPECT_ICON je reprezentován ikonou.

- Položka DVASPECT_DOCPRINT je reprezentována jako kdyby byly zobrazeny, pomocí příkazu tisknout z nabídky soubor.

### <a name="remarks"></a>Poznámky

Obvykle tuto funkci zavolat poté, co uživatel změní dokumentu na serveru. Pokud položka OLE je propojený s dokumentu s odkazem pro automatické, je položka aktualizována tak, aby odrážely změny. V kontejneru aplikací napsaných pomocí knihovny Microsoft Foundation Class [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) členskou funkci `COleClientItem` je volána.

Tato funkce volá `OnUpdate` členskou funkci pro všechny položky dokumentu s výjimkou odesílání položky, předají *pHint*, *lHint*, a *nDrawAspect*. Použijte tyto parametry k předání informací na informace o tom, změny provedené v dokumentu. Můžete kódovat informací pomocí *lHint* nebo můžete definovat `CObject`-odvozené třídy k ukládání informací o změny a předejte objekt této třídy pomocí *pHint*. Přepsat `OnUpdate` členské funkce ve vaší `COleServerItem`-odvozené třídy optimalizovat, aktualizuje se každou položku v závislosti na tom, zda došlo ke změně jeho prezentaci.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleLinkingDoc – třída](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDocument – třída](../../mfc/reference/coledocument-class.md)<br/>
[COleLinkingDoc – třída](../../mfc/reference/colelinkingdoc-class.md)<br/>
[COleTemplateServer – třída](../../mfc/reference/coletemplateserver-class.md)
