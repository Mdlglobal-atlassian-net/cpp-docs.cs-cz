---
title: Třída COleServerDoc
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
ms.openlocfilehash: 8e75ec5c00c614a225a059a2b3cf97a7a307c61c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753786"
---
# <a name="coleserverdoc-class"></a>Třída COleServerDoc

Základní třída pro dokumenty serveru OLE.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleServerDoc::COleServerDoc](#coleserverdoc)|Vytvoří `COleServerDoc` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleServerDoc::ActivateDocObject](#activatedocobject)|Aktivuje přidružený dokument DocObject.|
|[COleServerdoc::Aktivovatinplace](#activateinplace)|Aktivuje dokument pro úpravy na místě.|
|[COleServerDoc::DeaktivovatAOddělat](#deactivateandundo)|Deaktivuje uživatelské rozhraní serveru.|
|[COleServerDoc::DiscardUndoState](#discardundostate)|Zahodí informace o stavu vrátit.|
|[COleServerDoc::GetClientSite](#getclientsite)|Načte ukazatel na `IOleClientSite` základní rozhraní.|
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|Vrátí ukazatel na položku představující celý dokument.|
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|Vrátí aktuální ořezový obdélník pro úpravy na místě.|
|[COleServerDoc::GetItemPosition](#getitemposition)|Vrátí obdélník aktuální pozice vzhledem k klientské oblasti aplikace kontejneru pro úpravy na místě.|
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|Vrátí faktor zvětšení v obrazových bodech.|
|[COleServerdoc::isdocobjekt](#isdocobject)|Určuje, zda je dokument DocObject.|
|[COleServerDoc::IsEmbedded](#isembedded)|Označuje, zda je dokument vložen do dokumentu kontejneru nebo zda je spuštěn samostatně.|
|[COleServerdoc::IsInplaceActive](#isinplaceactive)|Vrátí hodnotu PRAVDA, pokud je položka aktuálně aktivována na místě.|
|[COleServerDoc::NotifyChanged](#notifychanged)|Upozorní kontejnery, že uživatel změnil dokument.|
|[COleServerDoc::NotifyClosed](#notifyclosed)|Upozorní kontejnery, že uživatel zavřel dokument.|
|[COleServerDoc::Přejmenovat notifyrename](#notifyrename)|Upozorní kontejnery, které uživatel přejmenoval dokument.|
|[COleServerDoc::NotifySaved](#notifysaved)|Upozorní kontejnery, které uživatel uložil dokument.|
|[COleServerDoc::OnDeaktivovat](#ondeactivate)|Volat rámci při uživatel deaktivuje položku, která byla aktivována na místě.|
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|Volat rámci zničit ovládací prvky a další prvky uživatelského rozhraní vytvořené pro aktivaci na místě.|
|[COleServerdoc::OnDocWindowActivate](#ondocwindowactivate)|Volat rámci při kontejneru okno rámce dokumentu je aktivován nebo deaktivován.|
|[COleServerDoc::OnResizeBorder](#onresizeborder)|Volat rámci při velikosti okna rámce aplikace kontejneru nebo dokumentu.|
|[COleServerdoc::OnShowControlBars](#onshowcontrolbars)|Volat rámci zobrazit nebo skrýt ovládací panely pro úpravy na místě.|
|[COleServerdoc::OnUpdateDocument](#onupdatedocument)|Volat rámci při uložení dokumentu serveru, který je vložené položky, aktualizace kontejneru kopii položky.|
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|Změní polohu rámečku pro úpravy na místě.|
|[COleServerDoc::Uložit vkládání](#saveembedding)|Informuje aplikaci kontejneru o uložení dokumentu.|
|[COleServerdoc::ScrollContainerby](#scrollcontainerby)|Posune dokument kontejneru.|
|[COleServerDoc::Aktualizovatvšechny položky](#updateallitems)|Upozorní kontejnery, že uživatel změnil dokument.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[COleServerdoc::CreateInplaceFrame](#createinplaceframe)|Volat rámci vytvořit okno rámce pro úpravy na místě.|
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|Volat rámci zničit okno rámce pro úpravy na místě.|
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|Přepsáním této funkce `CDocObjectServer` vytvořte nový objekt a označte, že tento dokument je kontejner DocObject.|
|[COleServerDoc::OnClose](#onclose)|Volat rámci při kontejneru požadavky na zavření dokumentu.|
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|Provede zadaný příkaz nebo zobrazí nápovědu pro příkaz.|
|[COleServerdoc::OnFrameWindowActivate](#onframewindowactivate)|Volat rámci při okno rámce kontejneru je aktivován nebo deaktivován.|
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|Volána `COleServerItem` získat, který představuje celý dokument; slouží k získání vložené položky. Implementace je nutná.|
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|Volat rámci vrátit zpět změny provedené během úprav na místě.|
|[COleserverdoc::OnSetHostNames](#onsethostnames)|Volat rámci při kontejneru nastaví název okna pro vložený objekt.|
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|Volat rámci umístit na místě okno rámce pro úpravy v okně aplikace kontejneru.|
|[COleServerdoc::Dokument OnShow](#onshowdocument)|Volat rámci zobrazit nebo skrýt dokument.|

## <a name="remarks"></a>Poznámky

Dokument serveru může obsahovat objekty [COleServerItem,](../../mfc/reference/coleserveritem-class.md) které představují rozhraní serveru pro vložené nebo propojené položky. Když je serverová aplikace spuštěna kontejnerem pro úpravu vložené položky, položka je načtena jako vlastní serverový dokument. objekt `COleServerDoc` obsahuje pouze `COleServerItem` jeden objekt, který se skládá z celého dokumentu. Když je serverová aplikace spuštěna kontejnerem pro úpravu propojené položky, je existující dokument načten z disku. část obsahu dokumentu je zvýrazněna, aby se označila propojená položka.

`COleServerDoc`objekty mohou také obsahovat položky [cOleClientItem](../../mfc/reference/coleclientitem-class.md) třídy. To umožňuje vytvářet aplikace kontejner-server. Rozhraní framework poskytuje funkce `COleClientItem` pro správné uložení `COleServerItem` položek při údržbě objektů.

Pokud serverová aplikace nepodporuje odkazy, bude serverový dokument vždy obsahovat pouze jednu položku serveru, která představuje celý vložený objekt jako dokument. Pokud serverová aplikace podporuje odkazy, musí vytvořit položku serveru při každém zkopírování výběru do schránky.

Chcete-li použít `COleServerDoc`, odvodit třídu z něj a implementovat [OnGetEmbeddedItem](#ongetembeddeditem) členské funkce, která umožňuje serveru pro podporu vložené položky. Odvodit `COleServerItem` třídu z implementovat položky v dokumentech a vrátit objekty této třídy z `OnGetEmbeddedItem`.

Chcete-li podporovat `COleServerDoc` propojené položky, poskytuje [OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) člennou funkci. Můžete použít výchozí implementaci nebo přepsat, pokud máte vlastní způsob správy položek dokumentu.

Potřebujete jednu `COleServerDoc`odvozenou třídu pro každý typ dokumentu serveru, který vaše aplikace podporuje. Pokud například serverová aplikace podporuje listy a `COleServerDoc`grafy, potřebujete dvě odvozené třídy.

Další informace o serverech naleznete v článku [Servery: Implementace serveru](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[CDokument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="coleserverdocactivatedocobject"></a><a name="activatedocobject"></a>COleServerDoc::ActivateDocObject

Aktivuje přidružený dokument DocObject.

```cpp
void ActivateDocObject();
```

### <a name="remarks"></a>Poznámky

Ve výchozím `COleServerDoc` nastavení nepodporuje aktivní dokumenty (označované také jako DocObjects). Chcete-li tuto podporu povolit, přečtěte si téma [GetDocObjectServer](#getdocobjectserver) a třída [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).

## <a name="coleserverdocactivateinplace"></a><a name="activateinplace"></a>COleServerdoc::Aktivovatinplace

Aktivuje položku pro úpravy na místě.

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0, což znamená, že položka je plně otevřena.

### <a name="remarks"></a>Poznámky

Tato funkce provádí všechny operace nezbytné pro aktivaci na místě. Vytvoří okno rámečku na místě, aktivuje ho a zvětší na položku, nastaví sdílené nabídky a další ovládací prvky, posune položku do zobrazení a nastaví fokus na okno rámečku na místě.

Tato funkce je volána výchozí implementací [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow). Tuto funkci zavolejte, pokud vaše aplikace podporuje jiné sloveso pro aktivaci na místě (například Play).

## <a name="coleserverdoccoleserverdoc"></a><a name="coleserverdoc"></a>COleServerDoc::COleServerDoc

Vytvoří `COleServerDoc` objekt bez připojení k knihovnám DLL systému OLE.

```
COleServerDoc();
```

### <a name="remarks"></a>Poznámky

Chcete-li otevřít komunikaci s ole, musíte volat [COleLinkingDoc::Register.](../../mfc/reference/colelinkingdoc-class.md#register) Pokud používáte [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) ve `COleLinkingDoc::Register` vaší aplikaci, `COleLinkingDoc`je volána pro vás implementací společnosti `OnNewDocument`, `OnOpenDocument`a `OnSaveDocument`.

## <a name="coleserverdoccreateinplaceframe"></a><a name="createinplaceframe"></a>COleServerdoc::CreateInplaceFrame

Rozhraní Framework volá tuto funkci k vytvoření okna rámce pro úpravy na místě.

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na nadřazené okno aplikace kontejneru.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno rámce na místě nebo NULL, pokud není úspěšný.

### <a name="remarks"></a>Poznámky

Výchozí implementace používá k vytvoření rámce informace zadané v šabloně dokumentu. Použité zobrazení je prvním zobrazením vytvořeným pro dokument. Toto zobrazení je dočasně odpojeno od původního rámečku a připojeno k nově vytvořenému rámečku.

Tohle je pokročilé překažné.

## <a name="coleserverdocdeactivateandundo"></a><a name="deactivateandundo"></a>COleServerDoc::DeaktivovatAOddělat

Tuto funkci zavolejte, pokud aplikace podporuje vrácení a uživatel po aktivaci položky, ale před její úpravou zvolí vrácení.

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová na úspěch; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud je aplikace kontejneru zapsána pomocí knihovny tříd Microsoft Foundation, volání této funkce způsobí, [že cOleClientItem::OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) bude volána, což deaktivuje uživatelské rozhraní serveru.

## <a name="coleserverdocdestroyinplaceframe"></a><a name="destroyinplaceframe"></a>COleServerDoc::DestroyInPlaceFrame

Rozhraní Framework volá tuto funkci zničit okno rámce na místě a vrátit okno dokumentu serverové aplikace do jeho stavu před aktivací na místě.

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parametry

*pFrameWnd*<br/>
Ukazatel na okno rámce na místě, které má být zničeno.

### <a name="remarks"></a>Poznámky

Tohle je pokročilé překažné.

## <a name="coleserverdocdiscardundostate"></a><a name="discardundostate"></a>COleServerDoc::DiscardUndoState

Pokud uživatel provede operaci úprav, kterou nelze vrátit zpět, volání této funkce vynutí aplikaci kontejneru zahodit informace o stavu zpět.

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová na úspěch; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je k dispozici tak, aby servery, které podporují Undo můžete uvolnit prostředky, které by jinak byly spotřebovány informace o stavu vrátit, které nelze použít.

## <a name="coleserverdocgetclientsite"></a><a name="getclientsite"></a>COleServerDoc::GetClientSite

Načte ukazatel na `IOleClientSite` základní rozhraní.

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>Návratová hodnota

Načte ukazatel na základní rozhraní [IOleClientSite.](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite)

## <a name="coleserverdocgetdocobjectserver"></a><a name="getdocobjectserver"></a>COleServerDoc::GetDocObjectServer

Přepište tuto funkci a `CDocObjectServer` vytvořte novou položku a vraťte jí ukazatel.

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>Parametry

*pDocSite*<br/>
Ukazatel na `IOleDocumentSite` rozhraní, které připojí tento dokument k serveru.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CDocObjectServer`; Null, pokud se operace nezdařila.

### <a name="remarks"></a>Poznámky

Při aktivaci serveru DocObject, návrat non-NULL ukazatel ukazuje, že klient může podporovat DocObjects. Výchozí implementace vrátí hodnotu NULL.

Typické implementace pro dokument, který podporuje DocObjects `CDocObjectServer` jednoduše přidělit nový objekt a vrátit jej volajícímu. Příklad:

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

## <a name="coleserverdocgetembeddeditem"></a><a name="getembeddeditem"></a>COleServerDoc::GetEmbeddedItem

Volání této funkce získat ukazatel na položku představující celý dokument.

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na položku představující celý dokument; Null, pokud se operace nezdařila.

### <a name="remarks"></a>Poznámky

Volá [COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem), virtuální funkce bez výchozí implementace.

## <a name="coleserverdocgetitemcliprect"></a><a name="getitemcliprect"></a>COleServerDoc::GetItemClipRect

Volání `GetItemClipRect` členské funkce získat ořezové obdélník ové souřadnice položky, která je upravována na místě.

```cpp
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>Parametry

*lpClipRect*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt pro příjem souřadnic ořezového obdélníku položky.

### <a name="remarks"></a>Poznámky

Souřadnice jsou v obrazových bodech vzhledem k klientské oblasti okna aplikace kontejneru.

Kreslení by se nemělo vyskytovat mimo ořezový obdélník. Kreslení je obvykle automaticky omezeno. Pomocí této funkce můžete určit, zda se uživatel posouval mimo viditelnou část dokumentu. Pokud ano, posuňte dokument kontejneru podle potřeby pomocí volání [ScrollContainerBy](#scrollcontainerby).

## <a name="coleserverdocgetitemposition"></a><a name="getitemposition"></a>COleServerDoc::GetItemPosition

Volání `GetItemPosition` členské funkce získat souřadnice položky upravovány na místě.

```cpp
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt pro příjem souřadnic položky.

### <a name="remarks"></a>Poznámky

Souřadnice jsou v obrazových bodech vzhledem k klientské oblasti okna aplikace kontejneru.

Pozici položky lze porovnat s aktuálním ořezovým obdélníkem a určit rozsah, ve kterém je položka viditelná (nebo není viditelná) na obrazovce.

## <a name="coleserverdocgetzoomfactor"></a><a name="getzoomfactor"></a>COleServerDoc::GetZoomFactor

Členská `GetZoomFactor` funkce určuje "faktor zvětšení" položky, která byla aktivována pro úpravy na místě.

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpSizeNum*<br/>
Ukazatel na objekt `CSize` třídy, který bude obsahovat čítač faktoru zvětšení. Může být NULL.

*lpSizeDenom*<br/>
Ukazatel na objekt `CSize` třídy, který bude obsahovat jmenovatele faktoru zvětšení. Může být NULL.

*lpPosRect*<br/>
Ukazatel na objekt `CRect` třídy, který popisuje novou pozici položky. Pokud je tento argument NULL, funkce používá aktuální pozici položky.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je položka aktivována pro úpravy na místě a její faktor zvětšení je jiný než 100% (1:1); jinak 0.

### <a name="remarks"></a>Poznámky

Faktor zvětšení v obrazových bodech je poměr velikosti položky k jejímu aktuálnímu rozsahu. Pokud aplikace kontejneru nenastavila rozsah položky, použije se její přirozený rozsah (určený [cOleServerItem::OnGetExtent).](../../mfc/reference/coleserveritem-class.md#ongetextent)

Funkce nastaví své první dva argumenty na čitatel a jmenovatel položky "faktor zvětšení." Pokud položka není upravována na místě, funkce nastaví tyto argumenty na výchozí hodnotu 100 % (nebo 1:1) a vrátí nulu. Další informace naleznete v technických poznámkách 40, [mfc/OLE změna velikosti a přiblížení](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="coleserverdocisdocobject"></a><a name="isdocobject"></a>COleServerdoc::isdocobjekt

Určuje, zda je dokument DocObject.

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je dokument DocObject; jinak FALSE.

## <a name="coleserverdocisembedded"></a><a name="isembedded"></a>COleServerDoc::IsEmbedded

Volání `IsEmbedded` členské funkce k určení, zda dokument představuje objekt vložený do kontejneru.

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, `COleServerDoc` pokud je objekt dokument, který představuje objekt vložený do kontejneru; jinak 0.

### <a name="remarks"></a>Poznámky

Dokument načtený ze souboru není vložen, i když s ním může pracovat aplikace kontejneru jako odkaz. Dokument, který je vložen ý do dokumentu kontejneru, se považuje za vložený.

## <a name="coleserverdocisinplaceactive"></a><a name="isinplaceactive"></a>COleServerdoc::IsInplaceActive

Volání `IsInPlaceActive` členské funkce k určení, zda je položka aktuálně v aktivním stavu na místě.

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, `COleServerDoc` pokud je objekt aktivní na místě; jinak 0.

## <a name="coleserverdocnotifychanged"></a><a name="notifychanged"></a>COleServerDoc::NotifyChanged

Voláním této funkce oznámíte všem připojeným položkám připojeným k dokumentu, že dokument byl změněn.

```cpp
void NotifyChanged();
```

### <a name="remarks"></a>Poznámky

Obvykle voláte tuto funkci poté, co uživatel změní některé globální atribut, jako jsou rozměry dokumentu serveru. Pokud je položka OLE propojena s dokumentem s automatickým propojením, bude aktualizována tak, aby odrážela změny. V kontejnerových aplikacích napsaných pomocí knihovny `COleClientItem` tříd Microsoft Foundation je volána členská funkce [OnChange.](../../mfc/reference/coleclientitem-class.md#onchange)

> [!NOTE]
> Tato funkce je součástí kompatibility s OLE 1. Nové aplikace by měly používat [UpdateAllItems](#updateallitems).

## <a name="coleserverdocnotifyclosed"></a><a name="notifyclosed"></a>COleServerDoc::NotifyClosed

Volání této funkce upozornit kontejner (y), že dokument byl uzavřen.

```cpp
void NotifyClosed();
```

### <a name="remarks"></a>Poznámky

Když uživatel vybere příkaz Zavřít z nabídky `NotifyClosed` Soubor, `COleServerDoc`je volána implementací členské funkce [OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument) . V kontejnerových aplikacích napsaných pomocí knihovny `COleClientItem` tříd Microsoft Foundation je volána členská funkce [OnChange.](../../mfc/reference/coleclientitem-class.md#onchange)

## <a name="coleserverdocnotifyrename"></a><a name="notifyrename"></a>COleServerDoc::Přejmenovat notifyrename

Tuto funkci zavolejte po přejmenování dokumentu serveru uživatelem.

```cpp
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parametry

*lpszNewName*<br/>
Ukazatel na řetězec určující nový název dokumentu serveru; obvykle se jedná o plně kvalifikovanou cestu.

### <a name="remarks"></a>Poznámky

Když uživatel zvolí příkaz Uložit jako z `NotifyRename` nabídky Soubor, je volána implementací `COleServerDoc`členské funkce [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument) . Tato funkce upozorní knihovny DLL systému OLE, které zase upozorňují kontejnery. V kontejnerových aplikacích napsaných pomocí knihovny `COleClientItem` tříd Microsoft Foundation je volána členská funkce [OnChange.](../../mfc/reference/coleclientitem-class.md#onchange)

## <a name="coleserverdocnotifysaved"></a><a name="notifysaved"></a>COleServerDoc::NotifySaved

Tuto funkci zavolejte po uložení dokumentu serveru uživatelem.

```cpp
void NotifySaved();
```

### <a name="remarks"></a>Poznámky

Když uživatel zvolí příkaz Uložit z nabídky `NotifySaved` Soubor, je `COleServerDoc`volána implementací [aplikace OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument). Tato funkce upozorní knihovny DLL systému OLE, které zase upozorňují kontejnery. V kontejnerových aplikacích napsaných pomocí knihovny `COleClientItem` tříd Microsoft Foundation je volána členská funkce [OnChange.](../../mfc/reference/coleclientitem-class.md#onchange)

## <a name="coleserverdoconclose"></a><a name="onclose"></a>COleServerDoc::OnClose

Volat rámci při kontejneru požaduje, aby byl uzavřen dokument serveru.

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>Parametry

*dwCloseOption*<br/>
Hodnota z výčtu OLECLOSE. Tento parametr může mít jednu z následujících hodnot:

- OLECLOSE_SAVEIFDIRTY Soubor je uložen, pokud byl změněn.

- OLECLOSE_NOSAVE Soubor je uzavřen bez uložení.

- OLECLOSE_PROMPTSAVE Pokud byl soubor změněn, je uživatel vyzván k jeho uložení.

### <a name="remarks"></a>Poznámky

Výchozí volání `CDocument::OnCloseDocument`implementace .

Další informace a další hodnoty naleznete v [tématu OLECLOSE](/windows/win32/api/oleidl/ne-oleidl-oleclose) v sadě Windows SDK.

## <a name="coleserverdocondeactivate"></a><a name="ondeactivate"></a>COleServerDoc::OnDeaktivovat

Volat rámci při uživatel deaktivuje vložené nebo propojené položky, která je aktuálně na místě aktivní.

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>Poznámky

Tato funkce obnoví uživatelské rozhraní aplikace kontejneru do původního stavu a zničí všechny nabídky a další ovládací prvky, které byly vytvořeny pro aktivaci na místě.

Informace o stavu vrátit vrátit by měla být bezpodmínečně uvolněna v tomto okamžiku.

Další informace naleznete v článku [Aktivace](../../mfc/activation-cpp.md)..

## <a name="coleserverdocondeactivateui"></a><a name="ondeactivateui"></a>COleServerDoc::OnDeactivateUI

Volána, když uživatel deaktivuje položku, která byla aktivována na místě.

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>Parametry

*bNeodáhnutelný*<br/>
Určuje, zda lze změny úprav vrátit zpět.

### <a name="remarks"></a>Poznámky

Tato funkce obnoví uživatelské rozhraní aplikace kontejneru do původního stavu a skryje všechny nabídky a další ovládací prvky, které byly vytvořeny pro aktivaci na místě.

Rozhraní framework vždy nastaví *bUndoable* na FALSE. Pokud server podporuje zpět a je operace, která může být vrátit zpět, volání základní třídy implementace s *bUndoable* nastavena na hodnotu TRUE.

## <a name="coleserverdocondocwindowactivate"></a><a name="ondocwindowactivate"></a>COleServerdoc::OnDocWindowActivate

Framework volá tuto funkci k aktivaci nebo deaktivaci okna dokumentu pro úpravy na místě.

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bAktivovat*<br/>
Určuje, zda má být okno dokumentu aktivováno nebo deaktivováno.

### <a name="remarks"></a>Poznámky

Výchozí implementace odebere nebo přidá prvky uživatelského rozhraní na úrovni rámce podle potřeby. Tuto funkci přepište, pokud chcete provést další akce, když je dokument obsahující položku aktivován nebo deaktivován.

Další informace naleznete v článku [Aktivace](../../mfc/activation-cpp.md)..

## <a name="coleserverdoconexecolecmd"></a><a name="onexecolecmd"></a>COleServerDoc::OnExecOleCmd

Rozhraní Framework volá tuto funkci ke spuštění zadaného příkazu nebo zobrazení nápovědy pro příkaz.

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
Ukazatel na identifikátor GUID, který identifikuje sadu příkazů. Může být NULL k označení výchozí skupiny příkazů.

*nCmdID*<br/>
Příkaz k provedení. Musí být ve skupině označené *pguidCmdGroup*.

*nCmdExecOut*<br/>
Způsob, jakým by měl objekt provést příkaz, jednu nebo více z následujících hodnot z výčtu OLECMDEXECOPT:

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pvarargIn*<br/>
Ukazatel na VARIANTARG obsahující vstupní argumenty pro příkaz. Může být NULL.

*pvarargOut*<br/>
Ukazatel na VARIANTARG pro příjem výstupních vrácené hodnoty z příkazu. Může být NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK v případě úspěchu. v opačném případě jeden z následujících kódů chyb:

|Hodnota|Popis|
|-----------|-----------------|
|E_UNEXPECTED|Došlo k neočekávané chybě.|
|E_fail|Došlo k chybě|
|E_NOTIMPL|Označuje, že samotný knihovna MFC by se měl pokusit přeložit a odeslat příkaz.|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* není null, ale neurčuje rozpoznanou skupinu příkazů|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* není rozpoznán jako platný příkaz ve skupině *pguidCmdGroup*|
|OLECMDERR_DISABLED|Příkaz identifikovaný *nCmdID* je zakázán a nelze jej provést.|
|OLECMDERR_NOHELP|Volající požádal o pomoc na příkaz identifikován *nCmdID,* ale žádná pomoc je k dispozici|
|OLECMDERR_CANCELED|Uživatel zrušil spuštění|

### <a name="remarks"></a>Poznámky

`COleCmdUI`lze povolit, aktualizovat a nastavit další vlastnosti příkazů uživatelského rozhraní DocObject. Po inicializování příkazů je můžete `OnExecOleCmd`spustit pomocí .

Rozhraní Framework volá funkci před pokusem o překlad a odeslání příkazu dokumentu OLE. Tuto funkci není nutné přepsat pro zpracování standardních příkazů dokumentu OLE, ale pokud chcete zpracovat vlastní příkazy nebo příkazy, které přijímají parametry nebo vracejí výsledky, je nutné zadat přepsání této funkce.

Většina příkazů neberou argumenty nebo vrátí hodnoty. Pro většinu příkazů může volající předat null pro *pvarargIn* a *pvarargOut*. Pro příkazy, které očekávají vstupní hodnoty, volající může deklarovat a inicializovat proměnnou VARIANTARG a předat ukazatel proměnné v *pvarargIn*. Pro příkazy, které vyžadují jednu hodnotu, argument může být uložen přímo v VARIANTARG a předán funkci. Více argumentů musí být zabaleny v rámci VARIANTARG pomocí `IDispatch` jednoho z podporovaných typů (například safearray).

Podobně pokud příkaz vrátí argumenty volajícího se očekává deklarovat VARIANTARG, inicializovat VT_EMPTY a předat jeho adresu v *pvarargOut*. Pokud příkaz vrátí jednu hodnotu, objekt můžete uložit tuto hodnotu přímo v *pvarargOut*. Více výstupních hodnot musí být nějakým způsobem zabaleno vhodné pro VARIANTARG.

Implementace této funkce základní třídy bude procházet OLE_COMMAND_MAP struktury přidružené k cíli příkazu a pokusí se odeslat příkaz příslušné obslužné rutině. Implementace základní třídy funguje pouze s příkazy, které nepřijímají argumenty nebo vrátí hodnoty. Pokud potřebujete zpracovat příkazy, které přijímají argumenty nebo vrátí hodnoty, musíte přepsat tuto funkci a pracovat s parametry *pvarargIn* a *pvarargOut* sami.

## <a name="coleserverdoconframewindowactivate"></a><a name="onframewindowactivate"></a>COleServerdoc::OnFrameWindowActivate

Framework volá tuto funkci při aktivaci nebo deaktivaci okna rámce aplikace kontejneru.

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bAktivovat*<br/>
Určuje, zda má být okno rámce aktivováno nebo deaktivováno.

### <a name="remarks"></a>Poznámky

Výchozí implementace zruší všechny režimy nápovědy, ve kterých se může okno rámce napíjet. Přepsat tuto funkci, pokud chcete provést speciální zpracování při aktivaci nebo deaktivaci okna rámce.

Další informace naleznete v článku [Aktivace](../../mfc/activation-cpp.md)..

## <a name="coleserverdocongetembeddeditem"></a><a name="ongetembeddeditem"></a>COleServerDoc::OnGetEmbeddedItem

Volat rámci při kontejneru aplikace volá serverovou aplikaci k vytvoření nebo úpravě vložené položky.

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na položku představující celý dokument; Null, pokud se operace nezdařila.

### <a name="remarks"></a>Poznámky

Neexistuje žádná výchozí implementace. Chcete-li vrátit položku, která představuje celý dokument, je nutné přepsat tuto funkci. Tato vrácená hodnota by `COleServerItem`měla být objektem odvozené třídy.

## <a name="coleserverdoconreactivateandundo"></a><a name="onreactivateandundo"></a>COleServerDoc::OnReactivateAndUndo

Rozhraní Framework volá tuto funkci, když se uživatel rozhodne vrátit zpět změny provedené v položce, která byla aktivována na místě, změněna a následně deaktivována.

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovede žádné další informace o vrácení CHYBY NEPRAVDA, což znamená selhání.

Přepsat tuto funkci, pokud vaše aplikace podporuje vrátit. Obvykle byste provést operaci zpět, pak aktivovat `ActivateInPlace`položku voláním . Pokud je aplikace kontejneru zapsána pomocí `COleClientItem::ReactivateAndUndo` knihovny tříd Microsoft Foundation, volání způsobí, že tato funkce bude volána.

## <a name="coleserverdoconresizeborder"></a><a name="onresizeborder"></a>COleServerDoc::OnResizeBorder

Rozhraní Framework volá tuto funkci při změně velikosti okna rámce aplikace kontejneru.

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>Parametry

*lpRectBorder*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt, který určuje souřadnice ohraničení.

*lpUIOkno*<br/>
Ukazatel na objekt `IOleInPlaceUIWindow` třídy, který vlastní aktuální relaci úprav na místě.

*bRám*<br/>
TRUE Pokud *lpUIWindow* odkazuje na okno rámce nejvyšší úrovně aplikace kontejneru nebo FALSE, pokud *lpUIWindow* odkazuje na okno rámce na úrovni dokumentu aplikace kontejneru.

### <a name="remarks"></a>Poznámky

Tato funkce změní velikost a upraví panely nástrojů a další prvky uživatelského rozhraní v souladu s novou velikostí okna.

Další informace naleznete v tématu [IOleInPlaceUIWindow](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow) v sadě Windows SDK.

Tohle je pokročilé překažné.

## <a name="coleserverdoconsethostnames"></a><a name="onsethostnames"></a>COleserverdoc::OnSetHostNames

Volat rámci při kontejneru nastaví nebo změní názvy hostitelů pro tento dokument.

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>Parametry

*lpszHost*<br/>
Ukazatel na řetězec, který určuje název aplikace kontejneru.

*lpszHostObj*<br/>
Ukazatel na řetězec, který určuje název kontejneru pro dokument.

### <a name="remarks"></a>Poznámky

Výchozí implementace změní název dokumentu pro všechna zobrazení odkazující na tento dokument.

Přepsat tuto funkci, pokud vaše aplikace nastaví tituly prostřednictvím jiného mechanismu.

## <a name="coleserverdoconsetitemrects"></a><a name="onsetitemrects"></a>COleServerDoc::OnSetItemRects

Rozhraní Framework volá tuto funkci k umístění okna rámce pro úpravy na místě v okně rámce aplikace kontejneru.

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt, který určuje umístění okna rámce na místě vzhledem k klientské oblasti aplikace kontejneru.

*lpClipRect*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt, který určuje ořezový obdélník okna rámečku na místě vzhledem k klientské oblasti aplikace kontejneru.

### <a name="remarks"></a>Poznámky

Přepsáním této funkce v případě potřeby aktualizujte faktor zvětšení zobrazení.

Tato funkce je obvykle volána jako odpověď na `RequestPositionChange` volání, i když může být volána kdykoli kontejnerem požádat o změnu pozice pro položku na místě.

## <a name="coleserverdoconshowcontrolbars"></a><a name="onshowcontrolbars"></a>COleServerdoc::OnShowControlBars

Framework volá tuto funkci k zobrazení nebo skrytí ovládacích panelů serverové aplikace přidružených k oknu rámce identifikovanému *pFrameWnd*.

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

*pFrameWnd*<br/>
Ukazatel na okno rámce, jehož ovládací panely by měly být skryté nebo zobrazeny.

*bZobrazit*<br/>
Určuje, zda jsou ovládací panely zobrazeny nebo skryty.

### <a name="remarks"></a>Poznámky

Výchozí implementace vyjmenovává všechny řídicí panely vlastněné tímto oknem rámce a skryje nebo zobrazí.

## <a name="coleserverdoconshowdocument"></a><a name="onshowdocument"></a>COleServerdoc::Dokument OnShow

Rozhraní Framework `OnShowDocument` volá funkci, když musí být dokument serveru skrytý nebo zobrazen.

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bZobrazit*<br/>
Určuje, zda má být uživatelské rozhraní dokumentu zobrazeno nebo skryto.

### <a name="remarks"></a>Poznámky

Pokud *bShow* je PRAVDA, výchozí implementace aktivuje serverovou aplikaci, v případě potřeby a způsobí, že aplikace kontejneru posunout jeho okna tak, aby položka je viditelná. Pokud *je bShow* FALSE, výchozí implementace deaktivuje položku prostřednictvím volání do `OnDeactivate`aplikace , pak zničí nebo skryje všechna okna rámce, která byla vytvořena pro dokument, s výjimkou prvního. Pokud nezůstanou žádné viditelné dokumenty, výchozí implementace skryje serverovou aplikaci.

## <a name="coleserverdoconupdatedocument"></a><a name="onupdatedocument"></a>COleServerdoc::OnUpdateDocument

Volat rámci při ukládání dokumentu, který je vložené položky ve složeném dokumentu.

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl dokument úspěšně aktualizován; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá [cOleServerDoc::NotifySaved](#notifysaved) a [COleServerDoc::SaveEmbedding](#saveembedding) členské funkce a pak označí dokument jako čistý. Přepsat tuto funkci, pokud chcete provést speciální zpracování při aktualizaci vložené položky.

## <a name="coleserverdocrequestpositionchange"></a><a name="requestpositionchange"></a>COleServerDoc::RequestPositionChange

Volání této členské funkce, aby aplikace kontejneru změnit pozici položky.

```cpp
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt obsahující novou pozici položky.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána (ve spojení s) `UpdateAllItems`při změně dat v aktivní položce na místě. Po tomto volání kontejneru může nebo nemusí `OnSetItemRects`provést změnu voláním . Výsledná pozice se může lišit od požadované pozice.

## <a name="coleserverdocsaveembedding"></a><a name="saveembedding"></a>COleServerDoc::Uložit vkládání

Volání této funkce sdělte aplikaci kontejneru uložení vloženého objektu.

```cpp
void SaveEmbedding();
```

### <a name="remarks"></a>Poznámky

Tato funkce je `OnUpdateDocument`volána automaticky z aplikace . Všimněte si, že tato funkce způsobí, že položka má být aktualizován na disku, takže je obvykle volána pouze v důsledku akce konkrétní uživatele.

## <a name="coleserverdocscrollcontainerby"></a><a name="scrollcontainerby"></a>COleServerdoc::ScrollContainerby

Volání `ScrollContainerBy` členské funkce pro posun dokumentu kontejneru o množství v `sizeScroll`pixelech označené .

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>Parametry

*sizeScroll*<br/>
Označuje, jak daleko je dokument kontejneru posunout.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Kladné hodnoty označují posouvání dolů a doprava; záporné hodnoty označují posouvání nahoru a doleva.

## <a name="coleserverdocupdateallitems"></a><a name="updateallitems"></a>COleServerDoc::Aktualizovatvšechny položky

Voláním této funkce oznámíte všem připojeným položkám připojeným k dokumentu, že dokument byl změněn.

```cpp
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parametry

*pOdesílatelí*<br/>
Ukazatel na položku, která dokument upravila, nebo hodnotu NULL, pokud mají být aktualizovány všechny položky.

*lTip*<br/>
Obsahuje informace o úpravě.

*pHint*<br/>
Ukazatel na objekt ukládající informace o změně.

*nDrawAspect*<br/>
Určuje způsob, jakým má být položka nakreslena. Toto je hodnota z výčtu DVASPECT. Tento parametr může mít jednu z následujících hodnot:

- DVASPECT_CONTENT Item je reprezentován a to takovým způsobem, že může být zobrazen jako vložený objekt uvnitř kontejneru.

- DVASPECT_THUMBNAIL Položka je vykreslena v "miniatuře", aby ji bylo možné zobrazit v nástroji pro procházení.

- DVASPECT_ICON položka je reprezentována ikonou.

- DVASPECT_DOCPRINT Položka je reprezentována, jako by byla vytištěna pomocí příkazu Tisk z nabídky Soubor.

### <a name="remarks"></a>Poznámky

Obvykle voláte tuto funkci poté, co uživatel změní dokument serveru. Pokud je položka OLE propojena s dokumentem s automatickým propojením, bude aktualizována tak, aby odrážela změny. V kontejnerových aplikacích napsaných pomocí knihovny `COleClientItem` tříd Microsoft Foundation je volána členská funkce [OnChange.](../../mfc/reference/coleclientitem-class.md#onchange)

Tato funkce `OnUpdate` volá členskou funkci pro každou položku dokumentu s výjimkou odesílající položky, předávání *pHint*, *lHint*a *nDrawAspect*. Tyto parametry slouží k předání informací položkám o změnách provedených v dokumentu. Můžete zakódovat informace pomocí *lHint* `CObject`nebo můžete definovat -derived třídy pro ukládání informací o změny a předat objekt této třídy pomocí *pHint*. Přepište `OnUpdate` členská funkce `COleServerItem`ve vaší odvozené třídě a optimalizujte aktualizaci každé položky v závislosti na tom, zda se změnila její prezentace.

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Třída COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída COleDocument](../../mfc/reference/coledocument-class.md)<br/>
[Třída COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Třída COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
