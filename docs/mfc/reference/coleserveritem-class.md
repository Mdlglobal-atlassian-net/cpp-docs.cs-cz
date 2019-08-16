---
title: Odvozenou třídu COleServerItem – třída
ms.date: 11/04/2016
f1_keywords:
- COleServerItem
- AFXOLE/COleServerItem
- AFXOLE/COleServerItem::COleServerItem
- AFXOLE/COleServerItem::AddOtherClipboardData
- AFXOLE/COleServerItem::CopyToClipboard
- AFXOLE/COleServerItem::DoDragDrop
- AFXOLE/COleServerItem::GetClipboardData
- AFXOLE/COleServerItem::GetDocument
- AFXOLE/COleServerItem::GetEmbedSourceData
- AFXOLE/COleServerItem::GetItemName
- AFXOLE/COleServerItem::GetLinkSourceData
- AFXOLE/COleServerItem::GetObjectDescriptorData
- AFXOLE/COleServerItem::IsConnected
- AFXOLE/COleServerItem::IsLinkedItem
- AFXOLE/COleServerItem::NotifyChanged
- AFXOLE/COleServerItem::OnDoVerb
- AFXOLE/COleServerItem::OnDraw
- AFXOLE/COleServerItem::OnDrawEx
- AFXOLE/COleServerItem::OnGetClipboardData
- AFXOLE/COleServerItem::OnGetExtent
- AFXOLE/COleServerItem::OnInitFromData
- AFXOLE/COleServerItem::OnQueryUpdateItems
- AFXOLE/COleServerItem::OnRenderData
- AFXOLE/COleServerItem::OnRenderFileData
- AFXOLE/COleServerItem::OnRenderGlobalData
- AFXOLE/COleServerItem::OnSetColorScheme
- AFXOLE/COleServerItem::OnSetData
- AFXOLE/COleServerItem::OnSetExtent
- AFXOLE/COleServerItem::OnUpdate
- AFXOLE/COleServerItem::OnUpdateItems
- AFXOLE/COleServerItem::SetItemName
- AFXOLE/COleServerItem::GetDataSource
- AFXOLE/COleServerItem::OnHide
- AFXOLE/COleServerItem::OnOpen
- AFXOLE/COleServerItem::OnShow
- AFXOLE/COleServerItem::m_sizeExtent
helpviewer_keywords:
- COleServerItem [MFC], COleServerItem
- COleServerItem [MFC], AddOtherClipboardData
- COleServerItem [MFC], CopyToClipboard
- COleServerItem [MFC], DoDragDrop
- COleServerItem [MFC], GetClipboardData
- COleServerItem [MFC], GetDocument
- COleServerItem [MFC], GetEmbedSourceData
- COleServerItem [MFC], GetItemName
- COleServerItem [MFC], GetLinkSourceData
- COleServerItem [MFC], GetObjectDescriptorData
- COleServerItem [MFC], IsConnected
- COleServerItem [MFC], IsLinkedItem
- COleServerItem [MFC], NotifyChanged
- COleServerItem [MFC], OnDoVerb
- COleServerItem [MFC], OnDraw
- COleServerItem [MFC], OnDrawEx
- COleServerItem [MFC], OnGetClipboardData
- COleServerItem [MFC], OnGetExtent
- COleServerItem [MFC], OnInitFromData
- COleServerItem [MFC], OnQueryUpdateItems
- COleServerItem [MFC], OnRenderData
- COleServerItem [MFC], OnRenderFileData
- COleServerItem [MFC], OnRenderGlobalData
- COleServerItem [MFC], OnSetColorScheme
- COleServerItem [MFC], OnSetData
- COleServerItem [MFC], OnSetExtent
- COleServerItem [MFC], OnUpdate
- COleServerItem [MFC], OnUpdateItems
- COleServerItem [MFC], SetItemName
- COleServerItem [MFC], GetDataSource
- COleServerItem [MFC], OnHide
- COleServerItem [MFC], OnOpen
- COleServerItem [MFC], OnShow
- COleServerItem [MFC], m_sizeExtent
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
ms.openlocfilehash: e369cfcbf94a1e5abc59d6f66aa71599efb11765
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503758"
---
# <a name="coleserveritem-class"></a>Odvozenou třídu COleServerItem – třída

Poskytuje serverové rozhraní pro položky OLE.

## <a name="syntax"></a>Syntaxe

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleServerItem::COleServerItem](#coleserveritem)|`COleServerItem` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|Umístí prezentační a převodní formáty do `COleDataSource` objektu.|
|[COleServerItem::CopyToClipboard](#copytoclipboard)|Zkopíruje položku do schránky.|
|[COleServerItem::DoDragDrop](#dodragdrop)|Provede operaci přetažení.|
|[COleServerItem::GetClipboardData](#getclipboarddata)|Získá zdroj dat pro použití při přenosu dat (přetahování nebo schránku).|
|[COleServerItem::GetDocument](#getdocument)|Vrátí dokument serveru, který obsahuje položku.|
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|Načte data CF_EMBEDSOURCE pro položku OLE.|
|[COleServerItem::GetItemName](#getitemname)|Vrátí název položky. Používá se pouze pro propojené položky.|
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|Načte data CF_LINKSOURCE pro položku OLE.|
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|Načte data CF_OBJECTDESCRIPTOR pro položku OLE.|
|[COleServerItem::IsConnected](#isconnected)|Označuje, zda je položka aktuálně připojena k aktivnímu kontejneru.|
|[COleServerItem::IsLinkedItem](#islinkeditem)|Označuje, zda položka představuje propojenou položku OLE.|
|[COleServerItem::NotifyChanged](#notifychanged)|Aktualizuje všechny kontejnery pomocí automatické aktualizace propojení.|
|[COleServerItem::OnDoVerb](#ondoverb)|Volá se, aby se spustil příkaz.|
|[Odvozenou třídu COleServerItem:: Draw](#ondraw)|Volá se, když kontejner vyžádá vykreslení položky; vyžaduje se implementace.|
|[Odvozenou třídu COleServerItem:: OnDrawEx](#ondrawex)|Volá se pro vykreslení specializované položky.|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|Volá se rozhraním, aby se získala data, která se zkopírují do schránky.|
|[COleServerItem::OnGetExtent](#ongetextent)|Volá se rozhraním, aby se načetla velikost položky OLE.|
|[COleServerItem::OnInitFromData](#oninitfromdata)|Volá se rozhraním, aby se inicializoval položka OLE pomocí obsahu zadaného objektu pro přenos dat.|
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|Volá se, aby se zjistilo, jestli nějaké propojené položky vyžadují aktualizaci.|
|[COleServerItem::OnRenderData](#onrenderdata)|Načte data jako součást zpožděného vykreslování.|
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|Načte data do `CFile` objektu jako součást zpožděného vykreslování.|
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|Načte data do HGLOBAL jako součást zpožděného vykreslování.|
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|Volá se, aby se nastavilo barevné schéma položky.|
|[COleServerItem::OnSetData](#onsetdata)|Volá se, aby se nastavila data položky.|
|[COleServerItem::OnSetExtent](#onsetextent)|Volá se rozhraním, aby se nastavila velikost položky OLE.|
|[COleServerItem::OnUpdate](#onupdate)|Volá se, když se změní část dokumentu, ve které položka patří.|
|[COleServerItem::OnUpdateItems](#onupdateitems)|Volá se, aby se aktualizovala mezipaměť prezentace všech položek v dokumentu na serveru.|
|[COleServerItem::SetItemName](#setitemname)|Nastaví název položky. Používá se pouze pro propojené položky.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[COleServerItem::GetDataSource](#getdatasource)|Získá objekt použitý k uložení formátů převodu.|
|[COleServerItem::OnHide](#onhide)|Volá se rozhraním, aby se skryla položka OLE.|
|[COleServerItem::OnOpen](#onopen)|Volá se rozhraním, aby se zobrazila položka OLE ve svém vlastním okně nejvyšší úrovně.|
|[COleServerItem::OnShow](#onshow)|Volá se, když kontejner požaduje zobrazení položky.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleServerItem::m_sizeExtent](#m_sizeextent)|Informuje server o tom, kolik položek OLE je viditelné.|

## <a name="remarks"></a>Poznámky

Propojená položka může představovat některé nebo všechny serverové dokumenty. Vložená položka vždy představuje celý dokument serveru.

`COleServerItem` Třída definuje několik přepisovatelných členských funkcí, které jsou volány pomocí knihovny DLL (Dynamic Link Library) systému OLE, obvykle v reakci na požadavky z aplikace typu kontejner. Tyto členské funkce umožňují aplikaci kontejneru manipulovat s položkou nepřímo různými způsoby, jako je zobrazení, provádění jejích operací nebo načítání dat v různých formátech.

Chcete- `COleServerItem`li použít, odvodit z něj třídu a implementovat členské funkce nakreslit a [serializovat](../../mfc/reference/cobject-class.md#serialize) . [](#ondraw) `OnDraw` Funkce poskytuje metasouborové reprezentace položky, která umožňuje zobrazení, když aplikace typu kontejner otevírá složený dokument. `Serialize` Funkceposkytujenativníreprezentacepoložky,cožumožňujepřenášetvloženoupoložkumeziaplikacemi`CObject` serveru a kontejnerů. [OnGetExtent](#ongetextent) poskytuje přirozené velikosti položky kontejneru a povoluje kontejneru velikost položky.

Další informace o serverech a souvisejících tématech najdete v článku [servery: Implementace serveru](../../mfc/servers-implementing-a-server.md) a "Vytvoření aplikace typu kontejner/server" v kontejnerech článků [: Pokročilé funkce](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXOLE. h

##  <a name="addotherclipboarddata"></a>Odvozenou třídu COleServerItem:: AddOtherClipboardData

Voláním této funkce umístíte formáty prezentace a převodu pro položku OLE v zadaném `COleDataSource` objektu.

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>Parametry

*pDataSource*<br/>
Ukazatel na `COleDataSource` objekt, ve kterém mají být umístěna data.

### <a name="remarks"></a>Poznámky

Aby bylo možné zadat prezentační [](#ondraw) formát (obrázek metasouboru) pro položku, je nutné, abyste nasadili členskou funkci nakreslit. Chcete-li podporovat jiné formáty převodu, zaregistrujte je pomocí objektu [COleDataSource –](../../mfc/reference/coledatasource-class.md) vráceného funkcí GetDataSource a přepište členskou funkci [OnRenderData](#onrenderdata) , aby poskytovala data ve formátech, které chcete podporovat. [](#getdatasource)

##  <a name="coleserveritem"></a>Odvozenou třídu COleServerItem:: odvozenou třídu COleServerItem

`COleServerItem` Vytvoří objekt a přidá jej do kolekce položek dokumentu na serveru.

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*pServerDoc*<br/>
Ukazatel na dokument, který bude obsahovat novou položku.

*bAutoDelete*<br/>
Příznak označující, zda lze objekt odstranit, je-li uvolněn odkaz na něj Nastavte na hodnotu false, pokud `COleServerItem` se jedná o nedílnou součást dat dokumentu, kterou je nutné odstranit. Nastavte na hodnotu TRUE, pokud je objekt sekundární strukturou použitou k identifikaci rozsahu v datech v dokumentu, který může rozhraní odstranit.

##  <a name="copytoclipboard"></a>Odvozenou třídu COleServerItem:: CopyToClipboard

Voláním této funkce zkopírujte položku OLE do schránky.

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>Parametry

*bIncludeLink*<br/>
Nastavte tuto hodnotu na TRUE, pokud se mají data odkazu zkopírovat do schránky. Nastavte na hodnotu FALSE, pokud serverová aplikace nepodporuje odkazy.

### <a name="remarks"></a>Poznámky

Funkce používá členskou funkci [OnGetClipboardData](#ongetclipboarddata) k vytvoření objektu [COleDataSource –](../../mfc/reference/coledatasource-class.md) obsahujícího data položky OLE ve formátech, které jsou podporovány. Funkce pak umístí `COleDataSource` objekt do schránky pomocí funkce [COleDataSource –:: SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) . `COleDataSource` Objekt obsahuje nativní data položky a její reprezentace ve formátu CF_METAFILEPICT a také data v libovolných formátech převodu, které se rozhodnete podporovat. Aby fungovala tato [](../../mfc/reference/cobject-class.md#serialize) členská funkce, je nutné implementovat serializaci a funkci [Draw](#ondraw) .

##  <a name="dodragdrop"></a>Odvozenou třídu COleServerItem::D oDragDrop

Chcete-li provést operaci přetažení, zavolejte členskoufunkci.`DoDragDrop`

```
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,
    CPoint ptOffset,
    BOOL bIncludeLink = FALSE,
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,
    LPCRECT lpRectStartDrag = NULL);
```

### <a name="parameters"></a>Parametry

*lpRectItem*<br/>
Obdélník položky na obrazovce v pixelech vzhledem k oblasti klienta.

*ptOffset*<br/>
Posun od *lpItemRect* , kde byla pozice myši v době tažení.

*bIncludeLink*<br/>
Nastavte tuto hodnotu na TRUE, pokud se mají data odkazu zkopírovat do schránky. Nastavte na hodnotu FALSE, pokud vaše aplikace nepodporuje odkazy.

*dwEffects*<br/>
Určuje efekty, které bude zdroj přetažení umožňovat v operaci přetažení (kombinace kopírování, přesunutí a propojení).

*lpRectStartDrag*<br/>
Ukazatel na obdélník, který definuje, kde se má skutečně začít přetahování. Další informace naleznete v následující části poznámky.

### <a name="return-value"></a>Návratová hodnota

Hodnota z výčtu DROPEFFECT. Pokud je DROPEFFECT_MOVE, měla by se odebrat původní data.

### <a name="remarks"></a>Poznámky

Operace přetažení se nespustí okamžitě. Počká, dokud ukazatel myši neopustí obdélník určený parametrem *lpRectStartDrag* , nebo dokud neuplyne zadaný počet milisekund. Pokud má *lpRectStartDrag* hodnotu null, použije se výchozí obdélník, aby se při přesunutí ukazatele myši na jeden pixel spustilo přetažení.

Doba zpoždění je určena nastavením klíče registru. Dobu zpoždění můžete změnit voláním [CWinApp:: WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) nebo [CWinApp:: WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Pokud nezadáte dobu zpoždění, použije se výchozí hodnota 200 milisekund. Čas zpoždění při přetahování je uložený takto:

- Čas zpoždění při přetahování Windows NT je uložený v HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- Čas zpoždění při přetahování Windows 3. x je uložený v souboru WIN. Soubor INI, v části [Windows}.

- Čas zpoždění při přetahování Windows 95/98 je uložený ve verzi WIN uložené v mezipaměti. Užívaný.

Další informace o tom, jak jsou informace o zpoždění při přetahování uloženy v registru nebo v. Soubor INI, viz [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) v Windows SDK.

##  <a name="getclipboarddata"></a>Odvozenou třídu COleServerItem:: GetClipboardData

Voláním této funkce vyplníte zadaný objekt [COleDataSource –](../../mfc/reference/coledatasource-class.md) všemi daty, která budou zkopírována do schránky, pokud jste volali [CopyToClipboard](#copytoclipboard) (stejná data budou přenesena i v případě, že jste volali [DoDragDrop](#dodragdrop)).

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>Parametry

*pDataSource*<br/>
Ukazatel na `COleDataSource` objekt, který dostane data položky OLE ve všech podporovaných formátech.

*bIncludeLink*<br/>
TRUE, pokud mají být data odkazů zkopírována do schránky. FALSE, pokud serverová aplikace nepodporuje odkazy.

*lpOffset*<br/>
Posun ukazatele myši v pixelech od počátku objektu.

*lpSize*<br/>
Velikost objektu v pixelech

### <a name="remarks"></a>Poznámky

Tato funkce volá členskou funkci [GetEmbedSourceData](#getembedsourcedata) pro získání nativních dat pro položku OLE a volá členskou funkci [AddOtherClipboardData](#addotherclipboarddata) pro získání formátu prezentace a všech podporovaných formátů převodu. Pokud má *bIncludeLink* hodnotu true, funkce také volá [GetLinkSourceData](#getlinksourcedata) , aby získala data propojení pro položku.

Tuto funkci přepište, pokud chcete vložit formáty do `COleDataSource` objektu před nebo po těchto formátech, které `CopyToClipboard`poskytuje.

##  <a name="getdatasource"></a>Odvozenou třídu COleServerItem:: GetDataSource

Voláním této funkce získáte objekt [COleDataSource –](../../mfc/reference/coledatasource-class.md) , který slouží k uložení formátů převodu, které podporuje serverová aplikace.

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `COleDataSource` objekt použitý k uložení formátů převodu.

### <a name="remarks"></a>Poznámky

Pokud chcete, aby vaše serverová aplikace nabízela během operací přenosu dat data v nejrůznějších formátech, zaregistrujte tyto `COleDataSource` formáty pomocí objektu vráceného touto funkcí. Například pokud chcete zadat reprezentaci CF_TEXT položky OLE pro operace schránky nebo přetažení, měli byste tento formát zaregistrovat pomocí `COleDataSource` objektu, který vrátí tato funkce, a potom `OnRenderXxxData` přepsat členskou funkci na Zadejte data.

##  <a name="getdocument"></a>Odvozenou třídu COleServerItem:: GetDocument

Voláním této funkce získáte ukazatel na dokument, který obsahuje položku.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dokument, který obsahuje položku; Hodnota NULL, pokud položka není součástí dokumentu.

### <a name="remarks"></a>Poznámky

To umožňuje přístup k dokumentu serveru, který jste předali jako argument `COleServerItem` konstruktoru.

##  <a name="getembedsourcedata"></a>  COleServerItem::GetEmbedSourceData

Voláním této funkce získáte data CF_EMBEDSOURCE pro položku OLE.

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpStgMedium*<br/>
Ukazatel na strukturu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) , která bude přijímat data CF_EMBEDSOURCE pro položku OLE.

### <a name="remarks"></a>Poznámky

Tento formát zahrnuje nativní data položky. Aby tato funkce fungovala `Serialize` správně, je nutné, abyste implementovali členskou funkci.

Výsledek lze přidat ke zdroji dat pomocí [COleDataSource –:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Tato funkce je volána automaticky pomocí [odvozenou třídu COleServerItem:: OnGetClipboardData](#ongetclipboarddata).

Další informace najdete v tématu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) v Windows SDK.

##  <a name="getitemname"></a>Odvozenou třídu COleServerItem:: GetItem

Voláním této funkce získáte název položky.

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název položky

### <a name="remarks"></a>Poznámky

Tato funkce se obvykle volá jenom pro propojené položky.

##  <a name="getlinksourcedata"></a>Odvozenou třídu COleServerItem:: GetLinkSourceData

Voláním této funkce získáte data CF_LINKSOURCE pro položku OLE.

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpStgMedium*<br/>
Ukazatel na strukturu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) , která bude přijímat data CF_LINKSOURCE pro položku OLE.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tento formát obsahuje identifikátor CLSID popisující typ položky OLE a informace potřebné k vyhledání dokumentu obsahujícího položku OLE.

Výsledek lze přidat do zdroje dat pomocí [COleDataSource –:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Tato funkce je volána automaticky [OnGetClipboardData](#ongetclipboarddata).

Další informace najdete v tématu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) v Windows SDK.

##  <a name="getobjectdescriptordata"></a>Odvozenou třídu COleServerItem:: GetObjectDescriptorData

Voláním této funkce získáte data CF_OBJECTDESCRIPTOR pro položku OLE.

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpOffset*<br/>
Posun kliknutí myší v levém horním rohu položky OLE Může mít hodnotu NULL.

*lpSize*<br/>
Velikost položky OLE Může mít hodnotu NULL.

*lpStgMedium*<br/>
Ukazatel na strukturu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) , která bude přijímat data CF_OBJECTDESCRIPTOR pro položku OLE.

### <a name="remarks"></a>Poznámky

Informace se zkopírují do struktury `STGMEDIUM` , na kterou odkazuje *lpStgMedium*. Tento formát obsahuje informace potřebné pro dialog Vložit speciální.

Další informace najdete v tématu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) v Windows SDK.

##  <a name="isconnected"></a>Odvozenou třídu COleServerItem::-Connected

Voláním této funkce zjistíte, zda je položka OLE připojena.

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je položka připojena; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Položka OLE je považována za připojenou, pokud jeden nebo více kontejnerů obsahuje odkazy na položku. Položka je připojena, pokud je počet odkazů větší než 0 nebo pokud se jedná o vloženou položku.

##  <a name="islinkeditem"></a>Odvozenou třídu COleServerItem:: IsLinkedItem

Voláním této funkce zjistíte, zda je položka OLE propojenou položkou.

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je položka propojená položka; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Položka je propojena v případě, že položka je platná a není vrácena v seznamu vložené položky v dokumentu. Propojená položka může nebo nemusí být připojena ke kontejneru.

Je běžné použít stejnou třídu pro propojené i vložené položky. `IsLinkedItem`umožňuje, aby se propojené položky chovaly jinak než vložené položky, i když je kód často společný.

##  <a name="m_sizeextent"></a>Odvozenou třídu COleServerItem:: m_sizeExtent

Tento člen oznamuje serveru, jak velká část objektu je viditelná v dokumentu kontejneru.

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>Poznámky

Výchozí implementace [OnSetExtent](#onsetextent) nastaví tento člen.

##  <a name="notifychanged"></a>Odvozenou třídu COleServerItem:: NotifyChanged

Po změně propojené položky volejte tuto funkci.

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Hodnota z výčtu DVASPECT, která určuje, který aspekt položky OLE se změnil. Tento parametr může mít některou z následujících hodnot:

- Položka DVASPECT_CONTENT je reprezentovaná takovým způsobem, že se dá zobrazit jako vložený objekt uvnitř kontejneru.

- Položka DVASPECT_THUMBNAIL se vykresluje v "miniatuře" reprezentace, aby se mohla zobrazit v nástroji pro procházení.

- Položka DVASPECT_ICON je reprezentována ikonou.

- Položka DVASPECT_DOCPRINT je reprezentována, jako kdyby byla vytištěna pomocí příkazu Print v nabídce soubor.

### <a name="remarks"></a>Poznámky

Pokud je položka kontejneru propojena s dokumentem pomocí automatického propojení, bude položka aktualizována, aby odrážela změny. V kontejnerových aplikacích napsaných pomocí knihovna Microsoft Foundation Class se v odpovědi volá [COleClientItem::-Change](../../mfc/reference/coleclientitem-class.md#onchange) .

##  <a name="ondoverb"></a>  COleServerItem::OnDoVerb

Volá se rozhraním, aby se dala provést Zadaná operace.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Určuje operaci, která má být provedena. Může to být jedna z následujících možností:

|Value|Význam|Písmeno|
|-----------|-------------|------------|
|0|primární požadavek|OLEIVERB_PRIMARY|
|1|Sekundární příkaz|NTato|
|- 1|Zobrazit položku pro úpravy|OLEIVERB_SHOW|
|- 2|Upravit položku v samostatném okně|OLEIVERB_OPEN|
|- 3|Skrýt položku|OLEIVERB_HIDE|

Hodnota-1 je obvykle alias pro jinou operaci. Pokud není podporováno otevírání úprav, má-2 stejný účinek jako-1. Další hodnoty naleznete v tématu [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) v Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud byla aplikace typu kontejner vytvořena pomocí knihovna Microsoft Foundation Class, je tato funkce volána, když je volána členská funkce [COleClientItem:: Activate](../../mfc/reference/coleclientitem-class.md#activate) odpovídajícího `COleClientItem` objektu. Výchozí implementace volá členskou funkci [inshow](#onshow) , pokud je zadána primární operace nebo OLEIVERB_SHOW, [Open](#onopen) , pokud je ZADÁN sekundární příkaz nebo OLEIVERB_OPEN, a když je zadán [](#onhide) parametr OLEIVERB_HIDE. Výchozí implementace volá `OnShow` , pokud *iVerb* není jednou z výše uvedených příkazů.

Tuto funkci přepište, pokud vaše primární příkaz tuto položku nezobrazuje. Například pokud je položka záznam zvuku a jeho primárním příkazem je přehráno, nemusíte zobrazit serverovou aplikaci, aby ji bylo možné přehrát.

Další informace najdete v tématu [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) v Windows SDK.

##  <a name="ondraw"></a>Odvozenou třídu COleServerItem:: Draw

Volá se rozhraním, aby se vygenerovala položka OLE do metasouboru.

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel na objekt [CDC](../../mfc/reference/cdc-class.md) , pro který chcete položku nakreslit. Kontext zobrazení je automaticky připojen k kontextu zobrazení atributu, takže můžete volat funkce atributů, i když by to mělo být závislé na zařízení.

*rSize*<br/>
Velikost (v jednotkách HIMETRIC), ve které se má metasoubor nakreslit.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla položka úspěšně vykreslena; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Reprezentace metasouboru položky OLE se používá k zobrazení položky v aplikaci typu kontejner. Pokud aplikace kontejneru byla napsána s knihovna Microsoft Foundation Class, metasoubor je používán funkcí [Draw](../../mfc/reference/coleclientitem-class.md#draw) member objektu odpovídajícího objektu [COleClientItem](../../mfc/reference/coleclientitem-class.md) . Neexistuje žádná výchozí implementace. Aby bylo možné položku nakreslit do zadaného kontextu zařízení, je nutné tuto funkci přepsat.

##  <a name="ondrawex"></a>Odvozenou třídu COleServerItem:: OnDrawEx

Volá se rozhraním pro všechny vykreslování.

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel na objekt [CDC](../../mfc/reference/cdc-class.md) , pro který chcete položku nakreslit. Řadič domény se automaticky připojí k atributu řadiče domény, takže můžete volat funkce atributů, i když by to mělo být specifické pro zařízení Metafile.

*nDrawAspect*<br/>
Hodnota z výčtu DVASPECT. Tento parametr může mít některou z následujících hodnot:

- Položka DVASPECT_CONTENT je reprezentovaná takovým způsobem, že se dá zobrazit jako vložený objekt uvnitř kontejneru.

- Položka DVASPECT_THUMBNAIL se vykresluje v "miniatuře" reprezentace, aby se mohla zobrazit v nástroji pro procházení.

- Položka DVASPECT_ICON je reprezentována ikonou.

- Položka DVASPECT_DOCPRINT je reprezentována, jako kdyby byla vytištěna pomocí příkazu Print v nabídce soubor.

*rSize*<br/>
Velikost položky v jednotkách HIMETRIC

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla položka úspěšně vykreslena; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace volání `OnDraw` , když je DVASPECT rovna DVASPECT_CONTENT; v opačném případě selže.

Přepište tuto funkci, pokud chcete poskytnout prezentační data pro jiné aspekty než DVASPECT_CONTENT, jako je například DVASPECT_ICON nebo DVASPECT_THUMBNAIL.

##  <a name="ongetclipboarddata"></a>Odvozenou třídu COleServerItem:: OnGetClipboardData

Volá se rozhraním, aby se `COleDataSource` získal objekt obsahující všechna data, která by se umístila do schránky prostřednictvím volání členské funkce [CopyToClipboard](#copytoclipboard) .

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>Parametry

*bIncludeLink*<br/>
Nastavte tuto hodnotu na TRUE, pokud se mají data odkazu zkopírovat do schránky. Nastavte na hodnotu FALSE, pokud serverová aplikace nepodporuje odkazy.

*lpOffset*<br/>
Posun kurzoru myši od počátku objektu v pixelech

*lpSize*<br/>
Velikost objektu v pixelech

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [COleDataSource –](../../mfc/reference/coledatasource-class.md) obsahující data ze schránky.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce volá [GetClipboardData](#getclipboarddata).

##  <a name="ongetextent"></a>Odvozenou třídu COleServerItem:: OnGetExtent

Volá se rozhraním, aby se načetla velikost položky OLE v HIMETRIC jednotkách.

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Určuje aspekt položky OLE, jejíž hranice mají být načteny. Tento parametr může mít některou z následujících hodnot:

- Položka DVASPECT_CONTENT je reprezentovaná takovým způsobem, že se dá zobrazit jako vložený objekt uvnitř kontejneru.

- Položka DVASPECT_THUMBNAIL se vykresluje v "miniatuře" reprezentace, aby se mohla zobrazit v nástroji pro procházení.

- Položka DVASPECT_ICON je reprezentována ikonou.

- Položka DVASPECT_DOCPRINT je reprezentována, jako kdyby byla vytištěna pomocí příkazu Print v nabídce soubor.

*rSize*<br/>
Odkaz na `CSize` objekt, který získá velikost položky OLE.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud byla aplikace typu kontejner napsána s knihovna Microsoft Foundation Class, je tato funkce volána, [](../../mfc/reference/coleclientitem-class.md#getextent) když je volána funkce getvelikost členské `COleClientItem` funkce odpovídajícího objektu. Výchozí implementace neprovádí žádnou akci. Musíte ji implementovat sami. Tuto funkci potlačíte, pokud chcete provádět zvláštní zpracování při zpracování požadavku na velikost položky OLE.

##  <a name="onhide"></a>Odvozenou třídu COleServerItem:: Hide

Volá se rozhraním, aby se skryla položka OLE.

```
virtual void OnHide();
```

### <a name="remarks"></a>Poznámky

Výchozí volání `COleServerDoc::OnShowDocument( FALSE )`. Funkce také oznámí kontejneru, že položka OLE je skrytá. Tuto funkci přepište, pokud chcete provést speciální zpracování při skrývání položky OLE.

##  <a name="oninitfromdata"></a>Odvozenou třídu COleServerItem:: OnInitFromData

Volá se rozhraním, aby se inicializoval položka OLE s použitím obsahu *pDataObject*.

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Ukazatel na datový objekt OLE obsahující data v různých formátech pro inicializaci položky OLE.

*bCreation*<br/>
TRUE, pokud je volána funkce pro inicializaci položky OLE, která je nově vytvořena aplikací typu kontejner. FALSE, pokud je funkce volána k nahrazení obsahu již existující položky OLE.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud má *bCreation* hodnotu true, tato funkce se zavolá, pokud kontejner implementuje vložení nového objektu na základě aktuálního výběru. Vybraná data se použijí při vytváření nové položky OLE. Například při výběru rozsahu buněk v programu tabulky a poté pomocí objektu INSERT New vytvořte graf založený na hodnotách ve vybraném rozsahu. Výchozí implementace neprovádí žádnou akci. Pomocí této funkce můžete zvolit přijatelný formát z těch, které nabízí *pDataObject* , a inicializovat položku OLE na základě poskytnutých dat. Toto je pokročilá přepsatelné.

Další informace naleznete v tématu [IOleObject:: InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) v Windows SDK.

##  <a name="onopen"></a>Odvozenou třídu COleServerItem:: Open

Volá se rozhraním, aby se zobrazila položka OLE v samostatné instanci serverové aplikace, a ne na místo.

```
virtual void OnOpen();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace aktivuje první okno rámce, ve kterém se zobrazuje dokument obsahující položku OLE; Pokud je aplikace minim serverem, výchozí implementace zobrazí hlavní okno. Funkce také oznámí kontejneru, že se otevřela položka OLE.

Tuto funkci přepište, pokud chcete při otevírání položky OLE provést speciální zpracování. To je obzvláště běžné u propojených položek, u kterých chcete nastavit výběr na odkaz při jeho otevření.

Další informace naleznete v tématu [IOleClientSite:: OnShowWindow](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) v Windows SDK.

##  <a name="onqueryupdateitems"></a>  COleServerItem::OnQueryUpdateItems

Volá se rozhraním, aby se zjistilo, jestli jsou nějaké propojené položky v aktuálním dokumentu na serveru zastaralé.

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dokument obsahuje položky, které vyžadují aktualizace. 0, pokud jsou všechny položky aktuální.

### <a name="remarks"></a>Poznámky

Položka je zastaralá, pokud došlo ke změně zdrojového dokumentu, ale propojená položka nebyla aktualizována, aby odrážela změny v dokumentu.

##  <a name="onrenderdata"></a>Odvozenou třídu COleServerItem:: OnRenderData

Volá se rozhraním, aby se načetla data v zadaném formátu.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) s určením formátu, ve kterém jsou požadovány informace.

*lpStgMedium*<br/>
Odkazuje na strukturu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) , ve které se mají vrátit data.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je ten dřív umístěný do `COleDataSource` objektu pomocí členské funkce [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) nebo [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) pro zpožděné vykreslování. Výchozí implementace této funkce volá [OnRenderFileData](#onrenderfiledata) nebo [OnRenderGlobalData](#onrenderglobaldata), v případě, že zadané paměťové médium je buď soubor, nebo paměť. Pokud ani jeden z těchto formátů není zadán, výchozí implementace vrátí 0 a neprovede žádnou akci.

Pokud je *lpStgMedium*-> *TYMED* TYMED_NULL, STGMEDIUM by měl být přidělen a vyplněn podle zadání *lpFormatEtc-> TYMED*. Pokud není TYMED_NULL, STGMEDIUM by se měl vyplnit daty.

Toto je pokročilá přepsatelné. Tuto funkci potlačíte tak, aby poskytovala data v požadovaném formátu a na středních médiích. V závislosti na vašich datech možná budete chtít místo toho přepsat jednu z dalších verzí této funkce. Pokud jsou vaše data malá a pevná velikost, přepište `OnRenderGlobalData`. Pokud jsou vaše data v souboru nebo mají proměnlivou velikost, popište `OnRenderFileData`.

Další informace naleznete v tématu [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)a [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) v Windows SDK.

##  <a name="onrenderfiledata"></a>  COleServerItem::OnRenderFileData

Volá se rozhraním, aby se načetla data v zadaném formátu, když je paměťové médium soubor.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) s určením formátu, ve kterém jsou požadovány informace.

*pFile*<br/>
Odkazuje na `CFile` objekt, ve kterém mají být vykreslena data.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je ten dřív umístěný do `COleDataSource` objektu pomocí členské funkce [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrátí hodnotu FALSE.

Toto je pokročilá přepsatelné. Tuto funkci potlačíte tak, aby poskytovala data v požadovaném formátu a na středních médiích. V závislosti na vašich datech možná budete chtít místo toho přepsat jednu z dalších verzí této funkce. Pokud chcete zpracovat více úložných médií, přepište [OnRenderData](#onrenderdata). Pokud jsou vaše data v souboru nebo mají proměnlivou velikost, přepište [OnRenderFileData](#onrenderfiledata).

Další informace naleznete v tématu [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) a [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v Windows SDK.

##  <a name="onrenderglobaldata"></a>  COleServerItem::OnRenderGlobalData

Volá se rozhraním, aby se načetla data v zadaném formátu, pokud je zadané paměťové médium globální paměti.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) s určením formátu, ve kterém jsou požadovány informace.

*phGlobal*<br/>
Odkazuje na popisovač globální paměti, ve které mají být vrácena data. Pokud není přidělena žádná paměť, tento parametr může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je ten dřív umístěný do `COleDataSource` objektu pomocí členské funkce [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrátí hodnotu FALSE.

Pokud má *phGlobal* hodnotu null, měl by se přidělit a vrátit nový HGLOBAL v *phGlobal*. V opačném případě by měl být HGLOBAL zadaný pomocí *phGlobal* vyplněn daty. Množství dat umístěných v HGLOBAL nesmí překročit aktuální velikost bloku paměti. Blok nelze také přidělit větší velikosti.

Toto je pokročilá přepsatelné. Tuto funkci potlačíte tak, aby poskytovala data v požadovaném formátu a na středních médiích. V závislosti na vašich datech možná budete chtít místo toho přepsat jednu z dalších verzí této funkce. Pokud chcete zpracovat více úložných médií, přepište [OnRenderData](#onrenderdata). Pokud jsou vaše data v souboru nebo mají proměnlivou velikost, přepište [OnRenderFileData](#onrenderfiledata).

Další informace naleznete v tématu [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) a [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v Windows SDK.

##  <a name="onsetcolorscheme"></a>Odvozenou třídu COleServerItem:: OnSetColorScheme

Volá se rozhraním, aby se určila barevná paleta, která se má použít při úpravách položky OLE.

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>Parametry

*lpLogPalette*<br/>
Ukazatel na strukturu [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) systému Windows.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je použita paleta barev; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud byla aplikace kontejneru vytvořena pomocí knihovna Microsoft Foundation Class, je tato funkce volána při volání funkce [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) odpovídajícího `COleClientItem` objektu. Výchozí implementace vrátí hodnotu FALSE. Tuto funkci můžete přepsat, pokud chcete použít doporučenou paletu. Serverová aplikace není nutná k použití navrhované palety.

Další informace naleznete v tématu [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) v Windows SDK.

##  <a name="onsetdata"></a>Odvozenou třídu COleServerItem::-SetData

Volá se rozhraním, aby se data položky OLE nahradila zadanými daty.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Ukazatel na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , která určuje formát dat.

*lpStgMedium*<br/>
Ukazatel na strukturu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) , ve které jsou uložena data.

*bRelease*<br/>
Označuje, kdo má po dokončení volání funkce vlastnictví úložného média. Volající určí, kdo zodpovídá za uvolnění prostředků přidělených za médium úložiště. Volající to provede nastavením *bRelease*. Pokud je *bRelease* nenulového, serverová položka převezme vlastnictví a uvolní médium, když ho jeho používání dokončí. Když je *bRelease* 0, volající zachová vlastnictví a položka serveru může používat médium úložiště pouze po dobu trvání volání.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Položka serveru převezme vlastnictví dat, dokud je neúspěšně nezískala. To znamená, že nepřevezme vlastnictví, pokud vrátí hodnotu 0. Pokud zdroj dat převezme vlastnictví, uvolní médium úložiště voláním funkce [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) .

Výchozí implementace neprovádí žádnou akci. Přepište tuto funkci, aby se data položky OLE nahradila zadanými daty. Toto je pokročilá přepsatelné.

Další informace naleznete v tématu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)a [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) v Windows SDK.

##  <a name="onsetextent"></a>Odvozenou třídu COleServerItem:: OnSetExtent

Volá se rozhraním, aby bylo možné sdělit objektu OLE, kolik místa je k dispozici v kontejneru dokumentu.

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Určuje aspekt položky OLE, jejíž hranice jsou určeny. Tento parametr může mít některou z následujících hodnot:

- Položka DVASPECT_CONTENT je reprezentovaná takovým způsobem, že se dá zobrazit jako vložený objekt uvnitř kontejneru.

- Položka DVASPECT_THUMBNAIL se vykresluje v "miniatuře" reprezentace, aby se mohla zobrazit v nástroji pro procházení.

- Položka DVASPECT_ICON je reprezentována ikonou.

- Položka DVASPECT_DOCPRINT je reprezentována, jako kdyby byla vytištěna pomocí příkazu Print v nabídce soubor.

*hodnota*<br/>
Struktura [CSize](../../atl-mfc-shared/reference/csize-class.md) určující novou velikost položky OLE.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud byla aplikace kontejneru vytvořena pomocí knihovna Microsoft Foundation Class, je tato funkce volána při volání členské funkce [SetExtent](../../mfc/reference/coleclientitem-class.md#setextent) odpovídajícího `COleClientItem` objektu. Výchozí implementace nastaví člena [m_sizeExtent](#m_sizeextent) na určenou velikost, pokud je *nDrawAspect* DVASPECT_CONTENT; v opačném případě vrátí 0. Tuto funkci můžete přepsat, chcete-li provést speciální zpracování při změně velikosti položky.

##  <a name="onshow"></a>Odvozenou třídu COleServerItem:: inshow

Volá se rozhraním, aby se serverová aplikace dala zobrazit, aby se zobrazila položka OLE.

```
virtual void OnShow();
```

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána, když uživatel aplikace typu kontejner vytvoří položku nebo provede operaci, například Edit, která vyžaduje zobrazení položky. Výchozí implementace pokusů o místní aktivaci. Pokud se to nepovede, funkce volá `OnOpen` členskou funkci, aby zobrazila položku OLE v samostatném okně.

Tuto funkci potlačíte, pokud chcete provádět zvláštní zpracování při zobrazení položky OLE.

##  <a name="onupdate"></a>Odvozenou třídu COleServerItem:: inupdate

Volá se rozhraním, když se změnila položka.

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Ukazatel na položku, která změnila dokument. Může mít hodnotu NULL.

*lHint*<br/>
Obsahuje informace o změně.

*pHint*<br/>
Ukazatel na objekt, který ukládá informace o změně.

*nDrawAspect*<br/>
Hodnota z výčtu DVASPECT. Tento parametr může mít jednu z následujících hodnot:

- Položka DVASPECT_CONTENT je reprezentovaná takovým způsobem, že se dá zobrazit jako vložený objekt uvnitř kontejneru.

- Položka DVASPECT_THUMBNAIL se vykresluje v "miniatuře" reprezentace, aby se mohla zobrazit v nástroji pro procházení.

- Položka DVASPECT_ICON je reprezentována ikonou.

- Položka DVASPECT_DOCPRINT je reprezentována, jako kdyby byla vytištěna pomocí příkazu Print v nabídce soubor.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá [NotifyChanged](#notifychanged), bez ohledu na pomocný parametr nebo odesílatele.

##  <a name="onupdateitems"></a>Odvozenou třídu COleServerItem:: OnUpdateItems

Volá se rozhraním, aby se aktualizovaly všechny položky v dokumentu serveru.

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace volá [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) pro všechny `COleClientItem` objekty v dokumentu.

##  <a name="setitemname"></a>Odvozenou třídu COleServerItem:: SetItemName

Tuto funkci volejte, když vytvoříte propojenou položku, která nastaví její název.

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
Ukazatel na nový název položky.

### <a name="remarks"></a>Poznámky

Název musí být v rámci dokumentu jedinečný. Když je volána serverová aplikace pro úpravu propojené položky, aplikace používá tento název k vyhledání položky. Tuto funkci není nutné volat pro vložené položky.

## <a name="see-also"></a>Viz také:

[HIERSVR Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CDocItem – třída](../../mfc/reference/cdocitem-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc – třída](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer – třída](../../mfc/reference/coletemplateserver-class.md)
