---
title: COleServerItem Class
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
ms.openlocfilehash: c4c026975e9884ac2a0e6aaef31e799c2b5b09bf
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777373"
---
# <a name="coleserveritem-class"></a>COleServerItem Class

Poskytuje rozhraní serveru pro položky OLE.

## <a name="syntax"></a>Syntaxe

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleServerItem::COleServerItem](#coleserveritem)|Vytvoří `COleServerItem` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|Umístí v prezentaci a převod formátů `COleDataSource` objektu.|
|[COleServerItem::CopyToClipboard](#copytoclipboard)|Kopíruje položku do schránky.|
|[COleServerItem::DoDragDrop](#dodragdrop)|Provádí operaci přetažení myší.|
|[COleServerItem::GetClipboardData](#getclipboarddata)|Získá zdroj dat pro použití v přenosu dat (přetahování nebo schránky).|
|[COleServerItem::GetDocument](#getdocument)|Vrátí dokumentu na serveru, který obsahuje položku.|
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|Získá CF_EMBEDSOURCE data pro položky OLE.|
|[COleServerItem::GetItemName](#getitemname)|Vrátí název položky. Používá se pouze propojené položky.|
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|Získá CF_LINKSOURCE data pro položky OLE.|
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|Získá CF_OBJECTDESCRIPTOR data pro položky OLE.|
|[COleServerItem::IsConnected](#isconnected)|Určuje, zda položka je v současnosti připojená k aktivní kontejner.|
|[COleServerItem::IsLinkedItem](#islinkeditem)|Určuje, zda položka představuje propojená položka OLE.|
|[COleServerItem::NotifyChanged](#notifychanged)|Aktualizuje všechny kontejnery s aktualizací update automatické propojení.|
|[COleServerItem::OnDoVerb](#ondoverb)|Volá se, aby provést operaci.|
|[COleServerItem::OnDraw](#ondraw)|Volá se, když kontejner požaduje k vykreslení položky; implementace vyžaduje.|
|[COleServerItem::OnDrawEx](#ondrawex)|Volá se pro kreslení specializované položky.|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|Volá se rozhraním, které se mají získat data, která má být zkopírováno do schránky.|
|[COleServerItem::OnGetExtent](#ongetextent)|Volá se rozhraním, aby se načetla velikost položky OLE.|
|[COleServerItem::OnInitFromData](#oninitfromdata)|Volá se rozhraním, aby se iniciovala položka OLE. obsah zadaného objektu přenos dat pomocí.|
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|Voláno k určení, jestli nějaké propojené položky vyžadovat aktualizaci.|
|[COleServerItem::OnRenderData](#onrenderdata)|Načte data jako součást zpožděné vykreslování.|
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|Načte data do `CFile` objekt jako součást zpožděné vykreslování.|
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|Načte data do HGLOBAL jako součást zpožděné vykreslování.|
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|Volá se, aby nastavení položky barevném schématu.|
|[COleServerItem::OnSetData](#onsetdata)|Volá se, aby nastavením položky.|
|[COleServerItem::OnSetExtent](#onsetextent)|Volá se rozhraním, chcete-li nastavit velikost položky OLE.|
|[COleServerItem::OnUpdate](#onupdate)|Volá se, když některá část dokumentu položka patří se změní.|
|[COleServerItem::OnUpdateItems](#onupdateitems)|Volá se, aby aktualizovat mezipaměť prezentace všechny položky v serverovém dokumentu.|
|[COleServerItem::SetItemName](#setitemname)|Nastaví název položky. Používá se pouze propojené položky.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[COleServerItem::GetDataSource](#getdatasource)|Získá objekt použitý k uložení převod formátů.|
|[COleServerItem::OnHide](#onhide)|Volá se rozhraním, chcete-li skrýt položky OLE.|
|[COleServerItem::OnOpen](#onopen)|Volá se rozhraním, aby se zobrazila položka OLE v samostatném okně nejvyšší úrovně.|
|[COleServerItem::OnShow](#onshow)|Volá se, když kontejner požaduje zobrazíte položky.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleServerItem::m_sizeExtent](#m_sizeextent)|Informuje o tom, jak velká část položky OLE je viditelné server.|

## <a name="remarks"></a>Poznámky

Propojená položka může představovat některé nebo všechny dokumentu na serveru. Vložená položka vždy představuje dokument celý server.

`COleServerItem` Třída definuje několik přepisovatelné členské funkce, které jsou volány OLE systému dynamické knihovny (DLL), obvykle v reakci na žádosti z aplikace typu kontejner. Tyto členské funkce povolit aplikace typu kontejner pro manipulaci s položkou nepřímo různými způsoby, například zobrazením, provádí její akce nebo načítá data v různých formátech.

Použití `COleServerItem`odvodit třídu z něj a implementovat [OnDraw](#ondraw) a [serializace](../../mfc/reference/cobject-class.md#serialize) členské funkce. `OnDraw` Poskytuje funkce znázornění metasouboru položky, díky kterému jej zobrazí, když se otevře aplikace typu kontejner do složeného dokumentu. `Serialize` Funkce `CObject` poskytuje nativní reprezentace některou položku, což vložená položka. přenos mezi aplikacemi serveru a kontejneru. [OnGetExtent](#ongetextent) poskytuje fyzická velikost položky do kontejneru, povolení kontejner pro nastavení velikosti položky.

Další informace o serverech a související témata, najdete v článku [serverů: Implementace serveru](../../mfc/servers-implementing-a-server.md) a "Vytváření Server/kontejner aplikace" v článku [kontejnerů: Pokročilé funkce](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

##  <a name="addotherclipboarddata"></a>  COleServerItem::AddOtherClipboardData

Voláním této funkce umístit prezentace a převod formátů pro položky OLE v zadaném `COleDataSource` objektu.

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>Parametry

*pDataSource*<br/>
Ukazatel `COleDataSource` objektu, ve kterém by měl umístit data.

### <a name="remarks"></a>Poznámky

Jste implementovali [OnDraw](#ondraw) členskou funkci k určení formátu prezentace (obrázek metafile) pro položku. Pro podporu dalších převod formátů, zaregistrujte je pomocí [coledatasource –](../../mfc/reference/coledatasource-class.md) vrácený [GetDataSource](#getdatasource) a přepsat [OnRenderData](#onrenderdata) členské funkce Zadejte data ve formátech, které chcete podporovat.

##  <a name="coleserveritem"></a>  COleServerItem::COleServerItem

Vytvoří `COleServerItem` objektu a přidá jej do dokumentu na serveru kolekci položek dokumentu.

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*pServerDoc*<br/>
Ukazatel na dokument, který bude obsahovat nová položka.

*bAutoDelete*<br/>
Příznak označující, jestli objekt může odstranit při odkazu na vydání. Nastavte na FALSE v případě `COleServerItem` objektu je nedílnou součástí dat dokumentu, které je potřeba odstranit. Nastavte na hodnotu TRUE, pokud objekt je sekundární struktura používaná k identifikaci oblast v dokumentu, a data, která je možné odstranit v rámci rozhraní.

##  <a name="copytoclipboard"></a>  COleServerItem::CopyToClipboard

Voláním této funkce do schránky Kopírovat položky OLE.

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>Parametry

*bIncludeLink*<br/>
Nastavte na hodnotu TRUE, pokud mají být odkaz data zkopírována do schránky. Nastavte na hodnotu FALSE, pokud váš server aplikace nepodporuje odkazy.

### <a name="remarks"></a>Poznámky

Funkce používá [OnGetClipboardData](#ongetclipboarddata) členské funkci, která vytvoří [coledatasource –](../../mfc/reference/coledatasource-class.md) objekt, který obsahuje položky OLE. data v formáty podporované. Funkce pak umístí `COleDataSource` objektu do schránky pomocí [COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) funkce. `COleDataSource` Objekt zahrnuje nativní datové položky a její znázornění ve formátu CF_METAFILEPICT, jakož i data v libovolné převod formátů výběr podporované. Jste implementovali [serializace](../../mfc/reference/cobject-class.md#serialize) a [OnDraw](#ondraw) pro tato členská funkce pro práci.

##  <a name="dodragdrop"></a>  COleServerItem::DoDragDrop

Volání `DoDragDrop` členská funkce k provedení operace přetažení myší.

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
Obdélník položky na obrazovce v pixelech vzhledem ke klientské oblasti.

*ptOffset*<br/>
Posun od *lpItemRect* kde byl pozice myši při přetažení.

*bIncludeLink*<br/>
Nastavte na hodnotu TRUE, pokud mají být odkaz data zkopírována do schránky. Nastavte ho na hodnotu FALSE, pokud aplikace nepodporuje odkazy.

*dwEffects*<br/>
Určuje efekty, které vám umožní zdroji přetažení v operaci přetažení (kombinace kopírovat, přesunout a odkaz).

*lpRectStartDrag*<br/>
Ukazatel na obdélník, který definuje, ve kterém ve skutečnosti spustí přetahování. Další informace naleznete v následující části poznámky.

### <a name="return-value"></a>Návratová hodnota

Hodnota z výčtu DROPEFFECT. Pokud je DROPEFFECT_MOVE, byste měli odebrat původní data.

### <a name="remarks"></a>Poznámky

Operace přetažení myší nespustí ihned. To počká, dokud kurzor myši opustí obdélník určené *lpRectStartDrag* nebo dokud se zadaný počet milisekund prošly. Pokud *lpRectStartDrag* má hodnotu NULL, výchozí obdélník se používá tak, aby přetažení se spustí při přesunu kurzoru myši jeden pixel.

Doba zpoždění je určené nastavení klíče registru. Doba zpoždění lze změnit pomocí volání [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) nebo [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Pokud nezadáte čas zpoždění, je použita výchozí hodnota 200 MS. Přetáhněte zpoždění je uložen následujícím způsobem:

- Doba zpoždění přetáhněte Windows NT se ukládají do HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- Doba zpoždění přetáhněte 3.x Windows se ukládají do VÍTĚZSTVÍ. Soubor INI [Windows} oddílu.

- Přetáhněte Windows 95/98 zpoždění je uložen v mezipaměti verzi Windows. INI.

Pro další informace o tom, přetáhněte zpoždění informace jsou uloženy v registru buď nebo. Soubor INI, naleznete v tématu [WriteProfileString](/windows/desktop/api/winbase/nf-winbase-writeprofilestringa) v sadě Windows SDK.

##  <a name="getclipboarddata"></a>  COleServerItem::GetClipboardData

Voláním této funkce tak, aby vyplnil zadaný [coledatasource –](../../mfc/reference/coledatasource-class.md) objekt se všechna data, která má být zkopírováno do schránky. Pokud jste volali [CopyToClipboard](#copytoclipboard) (stejná data by přenáší taky, pokud jste volá se, [metody DoDragDrop](#dodragdrop)).

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>Parametry

*pDataSource*<br/>
Ukazatel `COleDataSource` objekt, který bude přijímat položky OLE. data ve všech podporovaných formátů.

*bIncludeLink*<br/>
TRUE, pokud mají být odkaz data zkopírována do schránky. FALSE, pokud vaše serverová aplikace nepodporuje odkazy.

*lpOffset*<br/>
Odsazení v pixelech kurzoru myši ze zdroje objektu.

*lpSize*<br/>
Velikost objektu v pixelech.

### <a name="remarks"></a>Poznámky

Tato funkce volá [GetEmbedSourceData](#getembedsourcedata) členskou funkci získat data nativní pro položky OLE a volání [AddOtherClipboardData](#addotherclipboarddata) získat formát prezentace a všechny členské funkce Podporované formáty převodu. Pokud *bIncludeLink* je hodnota TRUE, funkce také volání [GetLinkSourceData](#getlinksourcedata) k získání dat odkaz pro položku.

Přepsat tuto funkci, pokud chcete umístit do formátů `COleDataSource` objektu před nebo za tyto formáty poskytnutých `CopyToClipboard`.

##  <a name="getdatasource"></a>  COleServerItem::GetDataSource

Voláním této funkce získáte [coledatasource –](../../mfc/reference/coledatasource-class.md) objektu se používá k ukládání převod formátů, které podporuje serverové aplikace.

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `COleDataSource` objekt použitý k uložení převod formátů.

### <a name="remarks"></a>Poznámky

Pokud chcete, vaše serverová aplikace nabízí v různých formátech dat při přenosu dat operace, tyto formáty se zaregistrovat `COleDataSource` objekt vrácený touto funkcí. Například pokud chcete zadat CF_TEXT reprezentace položky OLE schránky nebo operace přetažení myší, které by zaregistrovat formátu s `COleDataSource` tato funkce vrací objekt a potom přepsání `OnRenderXxxData` členské funkce Zadejte data.

##  <a name="getdocument"></a>  COleServerItem::GetDocument

Volání této funkce získáte ukazatel na dokument, který obsahuje položky.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dokument, který obsahuje položky; Hodnota NULL, pokud položka není součástí dokumentu.

### <a name="remarks"></a>Poznámky

To umožňuje přístup k dokumentu na serveru, který je předán jako argument `COleServerItem` konstruktoru.

##  <a name="getembedsourcedata"></a>  COleServerItem::GetEmbedSourceData

Voláním této funkce získání dat CF_EMBEDSOURCE pro položky OLE.

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpStgMedium*<br/>
Ukazatel [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktura, která bude přijímat data CF_EMBEDSOURCE pro položky OLE.

### <a name="remarks"></a>Poznámky

Tento formát obsahuje nativní datové položky. Jste implementovali `Serialize` členské funkce pro tuto funkci fungovala správně.

Výsledkem je potom možné přidat ke zdroji dat s využitím [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Tato funkce je volána automaticky [COleServerItem::OnGetClipboardData](#ongetclipboarddata).

Další informace najdete v tématu [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) v sadě Windows SDK.

##  <a name="getitemname"></a>  COleServerItem::GetItemName

Voláním této funkce a získat tak název položky.

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název položky.

### <a name="remarks"></a>Poznámky

Voláním této funkce se obvykle pouze pro propojené položky.

##  <a name="getlinksourcedata"></a>  COleServerItem::GetLinkSourceData

Voláním této funkce získání dat CF_LINKSOURCE pro položky OLE.

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpStgMedium*<br/>
Ukazatel [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktura, která bude přijímat data CF_LINKSOURCE pro položky OLE.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tento formát obsahuje identifikátor CLSID popisující typ položky OLE a informace potřebné k vyhledání dokument obsahující položky OLE.

Výsledkem je potom možné přidat k datovému zdroji prostřednictvím [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Tato funkce je volána automaticky [OnGetClipboardData](#ongetclipboarddata).

Další informace najdete v tématu [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) v sadě Windows SDK.

##  <a name="getobjectdescriptordata"></a>  COleServerItem::GetObjectDescriptorData

Voláním této funkce získání dat CF_OBJECTDESCRIPTOR pro položky OLE.

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpOffset*<br/>
Posun kliknutí myší od levého horního rohu položky OLE. Může mít hodnotu NULL.

*lpSize*<br/>
Velikost položky OLE. Může mít hodnotu NULL.

*lpStgMedium*<br/>
Ukazatel [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktura, která bude přijímat data CF_OBJECTDESCRIPTOR pro položky OLE.

### <a name="remarks"></a>Poznámky

Informace se zkopíruje do `STGMEDIUM` struktura odkazované *lpStgMedium*. Tento formát obsahuje informace potřebné pro dialogové okno zvláštní vložení.

Další informace najdete v tématu [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) v sadě Windows SDK.

##  <a name="isconnected"></a>  COleServerItem::IsConnected

Voláním této funkce, pokud je připojený položky OLE.

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je připojené položky; jinak 0.

### <a name="remarks"></a>Poznámky

Položky OLE se považuje za připojená, pokud jeden nebo více kontejnerů mají odkazy na položky. Položka je připojený, pokud jeho počet odkazů je větší než 0 nebo pokud je vložená položka.

##  <a name="islinkeditem"></a>  COleServerItem::IsLinkedItem

Voláním této funkce zjistěte, zda je položka OLE propojená položka.

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je položka propojená položka; jinak 0.

### <a name="remarks"></a>Poznámky

Položka je spojený, pokud položka je platný a nevrátí dokumentu seznam vložených položek. Propojená položka může nebo nemusí být připojen ke kontejneru.

Je běžné použití stejné třídy pro propojené a vložené položky. `IsLinkedItem` umožňuje zajistit propojené položky chovat jinak než vložené položky, i když v mnoha případech kód je běžné.

##  <a name="m_sizeextent"></a>  COleServerItem::m_sizeExtent

Tento člen říká serveru, jak velká část objektu je viditelný v dokumentu kontejneru.

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>Poznámky

Výchozí implementace [OnSetExtent](#onsetextent) nastaví tento člen.

##  <a name="notifychanged"></a>  COleServerItem::NotifyChanged

Voláním této funkce po změně propojená položka.

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Hodnota z výčtu DVASPECT, která určuje, se kterými aspekty položky OLE se změnil. Tento parametr může mít některý z následujících hodnot:

- Položky DVASPECT_CONTENT je reprezentována způsobem, že může být zobrazen jako vložený objekt uvnitř svého kontejneru.

- DVASPECT_THUMBNAIL položky se vykreslí v reprezentaci "miniaturu" tak, aby ji bylo možné zobrazit v nástroji pro procházení.

- Položka DVASPECT_ICON je reprezentován ikonou.

- Položka DVASPECT_DOCPRINT je reprezentována jako kdyby byly zobrazeny, pomocí příkazu tisknout z nabídky soubor.

### <a name="remarks"></a>Poznámky

Pokud položka kontejneru je propojený s dokumentu s odkazem pro automatické, je položka aktualizována tak, aby odrážely změny. V kontejneru aplikace vytvořené pomocí knihovny Microsoft Foundation Class [COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange) volána jako odpověď.

##  <a name="ondoverb"></a>  COleServerItem::OnDoVerb

Volá se rozhraním, aby provedla Zadaná operace.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Určuje příkaz pro spuštění. Může být některý z následujících akcí:

|Hodnota|Význam|Symbol|
|-----------|-------------|------------|
|0|primární požadavek|OLEIVERB_PRIMARY|
|1|Sekundární příkaz|(Žádné)|
|- 1|Položka zobrazení pro úpravy|OLEIVERB_SHOW|
|- 2|Upravit položky v samostatném okně.|OLEIVERB_OPEN|
|- 3|Skrytí položky|OLEIVERB_HIDE|

Hodnota-1 je obvykle alias pro jinou operací. Pokud otevřete úpravy se nepodporují, -2 má stejný účinek jako hodnotu -1. Další hodnoty, najdete v části [Funkce IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Kontejner aplikace vytvořené pomocí knihovny Microsoft Foundation Class, tato funkce je volána, když [COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate) členskou funkci k odpovídající položce `COleClientItem` objektu je volána. Výchozí implementace volá [viditelnost](#onshow) členskou funkci, pokud je zadán primárního operaci nebo OLEIVERB_SHOW, [při otevření](#onopen) Pokud sekundární operaci nebo OLEIVERB_OPEN není zadána, a [skrytí. ](#onhide) případného OLEIVERB_HIDE. Výchozí implementace volá `OnShow` Pokud *iVerb* není jedním z výše uvedených příkazů.

Tato funkce přepište, pokud položka není uveden primární požadavek. Například pokud položka je záznam zvuku a jeho primární požadavek je přehrávání, můžete nemusí zobrazit se serverová aplikace mohla přehrát.

Další informace najdete v tématu [Funkce IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) v sadě Windows SDK.

##  <a name="ondraw"></a>  COleServerItem::OnDraw

Volá se rozhraním, aby vykreslení položky OLE do metasouboru.

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel [CDC](../../mfc/reference/cdc-class.md) objekt, kterému chcete-li nakreslit položky. Kontext zobrazení je automaticky připojeni ke kontextu zobrazení atribut tak bude možné volat funkce atribut, i když to uděláte tak s žádným metasoubor konkrétní zařízení.

*parametru rSize*<br/>
Velikost v jednotkách HIMETRIC, ve kterém chcete-li nakreslit metasoubor.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud položka byla úspěšně vystavena; jinak 0.

### <a name="remarks"></a>Poznámky

Znázornění metasouboru položky OLE se používá k zobrazení položek v kontejneru aplikace. Kontejner aplikace vytvořené pomocí knihovny Microsoft Foundation Class, je tento metasoubor používané [nakreslit](../../mfc/reference/coleclientitem-class.md#draw) členskou funkci k odpovídající položce [COleClientItem](../../mfc/reference/coleclientitem-class.md) objektu. Neexistuje žádný výchozí implementaci. Je nutné přepsat tuto funkci k vykreslení položky do určeného kontextu zařízení.

##  <a name="ondrawex"></a>  COleServerItem::OnDrawEx

Volá se rozhraním pro všechny kreslení.

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel [CDC](../../mfc/reference/cdc-class.md) objekt, kterému chcete-li nakreslit položky. Řadič domény je automaticky připojen k atribut řadiče domény tak bude možné volat funkce atribut, i když to uděláte tak s žádným metasoubor specifická pro zařízení.

*nDrawAspect*<br/>
Hodnota z výčtu DVASPECT. Tento parametr může mít některý z následujících hodnot:

- Položky DVASPECT_CONTENT je reprezentována způsobem, že může být zobrazen jako vložený objekt uvnitř svého kontejneru.

- DVASPECT_THUMBNAIL položky se vykreslí v reprezentaci "miniaturu" tak, aby ji bylo možné zobrazit v nástroji pro procházení.

- Položka DVASPECT_ICON je reprezentován ikonou.

- Položka DVASPECT_DOCPRINT je reprezentována jako kdyby byly zobrazeny, pomocí příkazu tisknout z nabídky soubor.

*parametru rSize*<br/>
Velikost položky v jednotkách HIMETRIC.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud položka byla úspěšně vystavena; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá `OnDraw` při DVASPECT rovná DVASPECT_CONTENT; jinak dojde k chybě.

Tato funkce poskytující data prezentaci aspekty než DVASPECT_CONTENT, jako je například DVASPECT_ICON nebo DVASPECT_THUMBNAIL přepište.

##  <a name="ongetclipboarddata"></a>  COleServerItem::OnGetClipboardData

Volá se rozhraním, chcete-li získat `COleDataSource` objekt, který obsahuje všechna data, které by měly umístit do schránky voláním [CopyToClipboard](#copytoclipboard) členskou funkci.

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>Parametry

*bIncludeLink*<br/>
Nastavte na hodnotu TRUE, pokud mají být odkaz data zkopírována do schránky. Nastavte na hodnotu FALSE, pokud váš server aplikace nepodporuje odkazy.

*lpOffset*<br/>
Posun kurzoru myši ze zdroje objektu v pixelech.

*lpSize*<br/>
Velikost objektu v pixelech.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [coledatasource –](../../mfc/reference/coledatasource-class.md) objekt, který obsahuje data ve schránce.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce se volá [GetClipboardData](#getclipboarddata).

##  <a name="ongetextent"></a>  COleServerItem::OnGetExtent

Volá se rozhraním, aby se načetla velikost v jednotkách HIMETRIC položky OLE.

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Určuje aspekt položky OLE, jejichž rozsah se mají načíst. Tento parametr může mít některý z následujících hodnot:

- Položky DVASPECT_CONTENT je reprezentována způsobem, že může být zobrazen jako vložený objekt uvnitř svého kontejneru.

- DVASPECT_THUMBNAIL položky se vykreslí v reprezentaci "miniaturu" tak, aby ji bylo možné zobrazit v nástroji pro procházení.

- Položka DVASPECT_ICON je reprezentován ikonou.

- Položka DVASPECT_DOCPRINT je reprezentována jako kdyby byly zobrazeny, pomocí příkazu tisknout z nabídky soubor.

*parametru rSize*<br/>
Odkaz `CSize` objekt, který bude příjemcem velikost položky OLE.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Kontejner aplikace vytvořené pomocí knihovny Microsoft Foundation Class, tato funkce je volána, když [GetExtent](../../mfc/reference/coleclientitem-class.md#getextent) členskou funkci k odpovídající položce `COleClientItem` objektu je volána. Výchozí implementace nemá žádný účinek. Je nutné implementovat ho sami. Tato funkce přepište, pokud chcete provést zvláštní zpracování při zpracovávání konkrétní žádosti pro velikost položky OLE.

##  <a name="onhide"></a>  COleServerItem::OnHide

Volá se rozhraním, chcete-li skrýt položky OLE.

```
virtual void OnHide();
```

### <a name="remarks"></a>Poznámky

Volá výchozí `COleServerDoc::OnShowDocument( FALSE )`. Funkce také oznámí kontejneru skryté položky OLE. Tato funkce přepište, pokud chcete provést zvláštní zpracování při skrytí položky OLE.

##  <a name="oninitfromdata"></a>  COleServerItem::OnInitFromData

Volá se rozhraním, aby se iniciovala položka OLE. pomocí obsahu *pDataObject*.

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Ukazatel na datový objekt OLE obsahující data v různých formátech pro inicializaci položky OLE.

*bCreation*<br/>
TRUE, pokud je tato funkce volána k inicializaci položky OLE se nově vytvořené aplikace kontejneru. FALSE, pokud je tato funkce volána pro nahrazení obsahu již existující položky OLE.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *bCreation* má hodnotu TRUE, tato funkce je volána, pokud kontejner implementuje vložit nový objekt na základě aktuálního výběru. Vybraná data se používá při vytváření nové položky OLE. Například když vyberete oblast buněk v tabulce programu a následným použitím Vložit nový objekt k vytvoření grafu na základě hodnot ve vybraném rozsahu. Výchozí implementace nemá žádný účinek. Tuto funkci můžete vybírat z těch, které nabízí přijatelný formát přepsat *pDataObject* a inicializovat na základě dat poskytuje položky OLE. To je moderní overridable.

Další informace najdete v tématu [IOleObject::InitFromData](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-initfromdata) v sadě Windows SDK.

##  <a name="onopen"></a>  COleServerItem::OnOpen

Volá se rozhraním, aby se zobrazila položka OLE v samostatné instanci serverové aplikace, nikoli na místě.

```
virtual void OnOpen();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace aktivuje první okno rámce zobrazení dokumentu, který obsahuje položky OLE.; Pokud je aplikace mini serveru, zobrazí výchozí implementace hlavního okna. Funkce také oznámí kontejneru otevřené položky OLE.

Tato funkce přepište, pokud chcete provést zvláštní zpracování při otevření položky OLE. Toto je častý zejména s propojené položky, ve kterém chcete nastavit výběr na odkazu při otevření.

Další informace najdete v tématu [IOleClientSite::OnShowWindow](/windows/desktop/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) v sadě Windows SDK.

##  <a name="onqueryupdateitems"></a>  COleServerItem::OnQueryUpdateItems

Volá se rozhraním, chcete-li zjistit, jestli nějaké propojené položky v aktuálním dokumentu serveru jsou zastaralé.

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dokument obsahuje položky, které vyžadují aktualizace. 0, pokud všechny položky jsou aktuální.

### <a name="remarks"></a>Poznámky

Položka není aktuální, pokud jeho zdrojový dokument se změnil, ale propojená položka nebyla aktualizována tak, aby odrážely změny v dokumentu.

##  <a name="onrenderdata"></a>  COleServerItem::OnRenderData

Volá se rozhraním, k načtení dat v zadaném formátu.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura určující formát, ve které je požadované informace.

*lpStgMedium*<br/>
Odkazuje [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktury, ve kterém má být vrácena data.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je jedna dříve umístili ve `COleDataSource` pomocí [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) nebo [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) členskou funkci pro zpožděné vykreslování. Výchozí implementace této funkce se volá [OnRenderFileData](#onrenderfiledata) nebo [OnRenderGlobalData](#onrenderglobaldata), pokud je zadaný paměťovému médiu souboru nebo paměti. Pokud není zadána ani jedna z těchto formátů, výchozí implementace vrací hodnotu 0 a nemá žádný účinek.

Pokud *lpStgMedium*-> *objekt tymed* TYMED_NULL, je STGMEDIUM měli přidělená a vyplněné podle specifikace *lpFormatEtc -> objekt tymed*. Pokud není TYMED_NULL, STGMEDIUM by mělo být vyplněno místo s daty.

To je moderní overridable. Tato funkce se vaše data v požadovaný formát a střední přepište. V závislosti na vašich dat můžete chtít přepsat místo toho některou z dalších verzí této funkce. Pokud vaše data je malý a pevnou velikost, má přednost před `OnRenderGlobalData`. Pokud vaše data se v souboru nebo se s proměnnou velikostí, má přednost před `OnRenderFileData`.

Další informace najdete v tématu [IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium), [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc), a [objekt TYMED](/windows/desktop/api/objidl/ne-objidl-tagtymed) v sadě Windows SDK.

##  <a name="onrenderfiledata"></a>  COleServerItem::OnRenderFileData

Volá se rozhraním, k načtení dat v zadaném formátu souboru po paměťovému médiu.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura určující formát, ve které je požadované informace.

*pFile*<br/>
Odkazuje `CFile` objektu, ve kterém se data mají být vykresleny.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je jedna dříve umístili ve `COleDataSource` pomocí [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) členskou funkci pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrací hodnotu FALSE.

To je moderní overridable. Tato funkce se vaše data v požadovaný formát a střední přepište. V závislosti na vašich dat můžete chtít přepsat místo toho některou z dalších verzí této funkce. Pokud chcete zpracovávat více úložných, má přednost před [OnRenderData](#onrenderdata). Pokud vaše data se v souboru nebo se s proměnnou velikostí, má přednost před [OnRenderFileData](#onrenderfiledata).

Další informace najdete v tématu [IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) a [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) v sadě Windows SDK.

##  <a name="onrenderglobaldata"></a>  COleServerItem::OnRenderGlobalData

Volá se rozhraním, k načtení dat v zadaném formátu po globální paměti zadaná paměťovému médiu.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura určující formát, ve které je požadované informace.

*phGlobal*<br/>
Odkazuje na popisovač do globální paměti, ve kterém má být vrácena data. Pokud byla přidělena žádná paměť, tento parametr může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je jedna dříve umístili ve `COleDataSource` pomocí [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) členskou funkci pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrací hodnotu FALSE.

Pokud *phGlobal* má hodnotu NULL, pak nové HGLOBAL by měl být přiděleno a vrácené v *phGlobal*. V opačném případě HGLOBAL určené *phGlobal* by měl být vyplněny data. Množství dat, které jsou umístěny v HGLOBAL nesmí být delší než aktuální velikost bloku paměti. Navíc bloku nejde znovu přidělit, větší velikosti.

To je moderní overridable. Tato funkce se vaše data v požadovaný formát a střední přepište. V závislosti na vašich dat můžete chtít přepsat místo toho některou z dalších verzí této funkce. Pokud chcete zpracovávat více úložných, má přednost před [OnRenderData](#onrenderdata). Pokud vaše data se v souboru nebo se s proměnnou velikostí, má přednost před [OnRenderFileData](#onrenderfiledata).

Další informace najdete v tématu [IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) a [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) v sadě Windows SDK.

##  <a name="onsetcolorscheme"></a>  COleServerItem::OnSetColorScheme

Volá se rozhraním, chcete-li určit paletu barev, která se použije při úpravách položky OLE.

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>Parametry

*lpLogPalette*<br/>
Ukazatel Windows [LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette) struktury.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se používá paletu barev; jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace typu kontejner vytvořené pomocí knihovny Microsoft Foundation Class, tato funkce je volána, když [IOleObject::SetColorScheme](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) funkce k odpovídající položce `COleClientItem` objektu je volána. Výchozí implementace vrací hodnotu FALSE. Tato funkce přepište, pokud chcete použít doporučené paletu. Serverová aplikace není nutné používat navrhované palety.

Další informace najdete v tématu [IOleObject::SetColorScheme](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) v sadě Windows SDK.

##  <a name="onsetdata"></a>  COleServerItem::OnSetData

Volá se rozhraním, aby se nahradit data položky OLE se zadanými daty.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Ukazatel [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura určující formát data.

*lpStgMedium*<br/>
Ukazatel [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktury, ve kterém jsou data uložená.

*bRelease*<br/>
Označuje, kdo je vlastníkem úložiště média po dokončení volání funkce. Volající rozhodne, kdo je zodpovědná za uvolnění prostředků přidělených jménem paměťovému médiu. Volající toho dosahuje tím, že nastavíte *bRelease*. Pokud *bRelease* je nenulová, položka serveru převezme vlastnictví, uvolnění médium po dokončení jeho použití. Když *bRelease* je 0, že volajícímu zůstane vlastnictví a položka serveru můžete použít paměťovému médiu pouze po dobu trvání volání.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Položka serveru nepřijímá vlastnictví dat, dokud ji má byly úspěšně načteny. To znamená nebere v vlastnictví Pokud vrátí hodnotu 0. Pokud zdroj dat trvá vlastnictví, takže paměťovému médiu voláním [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) funkce.

Výchozí implementace nemá žádný účinek. Přepsání této funkce můžete nahradit data položky OLE se zadanými daty. To je moderní overridable.

Další informace najdete v tématu [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium), [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc), a [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) v sadě Windows SDK.

##  <a name="onsetextent"></a>  COleServerItem::OnSetExtent

Volá se rozhraním zjistit položky OLE, kolik místa je k dispozici v dokumentu kontejneru.

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Určuje aspekt položky OLE, jejichž rozsah je určeno. Tento parametr může mít některý z následujících hodnot:

- Položky DVASPECT_CONTENT je reprezentována způsobem, že může být zobrazen jako vložený objekt uvnitř svého kontejneru.

- DVASPECT_THUMBNAIL položky se vykreslí v reprezentaci "miniaturu" tak, aby ji bylo možné zobrazit v nástroji pro procházení.

- Položka DVASPECT_ICON je reprezentován ikonou.

- Položka DVASPECT_DOCPRINT je reprezentována jako kdyby byly zobrazeny, pomocí příkazu tisknout z nabídky soubor.

*Velikost*<br/>
A [CSize](../../atl-mfc-shared/reference/csize-class.md) struktura určující novou velikost položky OLE.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Kontejner aplikace vytvořené pomocí knihovny Microsoft Foundation Class, tato funkce je volána, když [SetExtent](../../mfc/reference/coleclientitem-class.md#setextent) členskou funkci k odpovídající položce `COleClientItem` objektu je volána. Výchozí implementace sady [m_sizeExtent](#m_sizeextent) člena na zadané velikosti Pokud *nDrawAspect* je DVASPECT_CONTENT; jinak vrátí hodnotu 0. Potlačí tuto funkci provést zvláštní zpracování, když změníte velikost položky.

##  <a name="onshow"></a>  COleServerItem::OnShow

Volá se rozhraním, dáte pokyn, aby serverové aplikace, aby se zobrazila položka OLE v místě.

```
virtual void OnShow();
```

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána, když uživatel aplikace typu kontejner vytvoří položku nebo provádí operaci, jako jsou úpravy, který vyžaduje, aby položka zobrazený. Výchozí implementace pokusí aktivace na místě. Pokud se to nepovede, volání funkce `OnOpen` členskou funkci, aby se zobrazila položka OLE v samostatném okně.

Tato funkce přepište, pokud chcete provést zvláštní zpracování, pokud se zobrazí položky OLE.

##  <a name="onupdate"></a>  COleServerItem::OnUpdate

Volá se rozhraním, když se upraví položka.

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Ukazatel na položku, která změnit dokument. Může mít hodnotu NULL.

*lHint*<br/>
Obsahuje informace o změnu.

*pHint*<br/>
Ukazatel na objekt ukládání informací o změnu.

*nDrawAspect*<br/>
Hodnota z výčtu DVASPECT. Tento parametr může mít některou z následujících hodnot:

- Položky DVASPECT_CONTENT je reprezentována způsobem, že může být zobrazen jako vložený objekt uvnitř svého kontejneru.

- DVASPECT_THUMBNAIL položky se vykreslí v reprezentaci "miniaturu" tak, aby ji bylo možné zobrazit v nástroji pro procházení.

- Položka DVASPECT_ICON je reprezentován ikonou.

- Položka DVASPECT_DOCPRINT je reprezentována jako kdyby byly zobrazeny, pomocí příkazu tisknout z nabídky soubor.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá [NotifyChanged](#notifychanged), bez ohledu na to pomocného parametru či odesílatele.

##  <a name="onupdateitems"></a>  COleServerItem::OnUpdateItems

Volá se rozhraním, aby se aktualizovaly všechny položky v serverovém dokumentu.

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace volá [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) pro všechny `COleClientItem` objekty v dokumentu.

##  <a name="setitemname"></a>  COleServerItem::SetItemName

Voláním této funkce, když vytvoříte propojenou položku k nastavení jeho název.

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
Ukazatel na nový název položky.

### <a name="remarks"></a>Poznámky

Název musí být jedinečný v rámci dokumentu. Při volání serverovou aplikaci můžete upravit propojené položky aplikace používá tento název se najít položku. Není nutné volat tuto funkci pro vložené položky.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem – třída](../../mfc/reference/cdocitem-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc – třída](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer – třída](../../mfc/reference/coletemplateserver-class.md)
