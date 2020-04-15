---
title: COleServerItem – třída
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
ms.openlocfilehash: 5373075cf6dfc54e6e2368e46f48f317fcec64d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376116"
---
# <a name="coleserveritem-class"></a>COleServerItem – třída

Poskytuje rozhraní serveru položkám OLE.

## <a name="syntax"></a>Syntaxe

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleServerItem::COleServerItem](#coleserveritem)|Vytvoří `COleServerItem` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|Umístí formáty prezentace a `COleDataSource` převodu do objektu.|
|[COleServerItem::CopyToClipboard](#copytoclipboard)|Zkopíruje položku do schránky.|
|[COleServerItem::DoDragDrop](#dodragdrop)|Provede operaci přetažení myší.|
|[COleServerItem::GetClipboardData](#getclipboarddata)|Získá zdroj dat pro použití při přenosu dat (přetažení nebo schránky).|
|[COleServerItem::GetDocument](#getdocument)|Vrátí dokument serveru, který obsahuje položku.|
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|Získá CF_EMBEDSOURCE data pro položku OLE.|
|[COleServerItem::GetItemName](#getitemname)|Vrátí název položky. Používá se pouze pro propojené položky.|
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|Získá CF_LINKSOURCE data pro položku OLE.|
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|Získá CF_OBJECTDESCRIPTOR data pro položku OLE.|
|[COleServerItem::Jepřipojeno](#isconnected)|Označuje, zda je položka aktuálně připojena k aktivnímu kontejneru.|
|[COleServerItem::IsLinkedItem](#islinkeditem)|Označuje, zda položka představuje propojenou položku OLE.|
|[COleServerItem::NotifyChanged](#notifychanged)|Aktualizuje všechny kontejnery s automatickou aktualizací odkazu.|
|[ColeServerItem::Ondoverb](#ondoverb)|Volána k provedení slovesa.|
|[COleServerItem::Ondraw](#ondraw)|Volána, když kontejner požaduje nakreslit položku; provádění.|
|[COleServerItem::OnDrawEx](#ondrawex)|Nazývá se pro výkres specializované položky.|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|Volat rámci získat data, která by byly zkopírovány do schránky.|
|[COleServerItem::OnGetExtent](#ongetextent)|Volat rámci načíst velikost položky OLE.|
|[COleServerItem::OnInitFromData](#oninitfromdata)|Volat rámci inicializovat položku OLE pomocí obsahu objektu přenosu dat zadané.|
|[ColeServerItem::OnQueryUpdateItems](#onqueryupdateitems)|Volána k určení, zda všechny propojené položky vyžadují aktualizaci.|
|[COleServerItem::OnRenderData](#onrenderdata)|Načte data jako součást zpožděného vykreslování.|
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|Načte data `CFile` do objektu jako součást zpožděného vykreslování.|
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|Načte data do HGLOBAL jako součást zpožděného vykreslování.|
|[COleServerItem::onsetcolorscheme](#onsetcolorscheme)|Nazývá se nastavení barevného schématu položky.|
|[coleserveritem::onsetdata](#onsetdata)|Volána k nastavení dat položky.|
|[COleServerItem::Délkarozsahu](#onsetextent)|Volat rámci nastavit velikost položky OLE.|
|[COleServerItem::OnUpdate](#onupdate)|Nazývá se při změně některé části dokumentu, do které položka patří.|
|[COleServerItem::OnUpdateItems](#onupdateitems)|Nazývá se aktualizace mezipaměti prezentace všech položek v dokumentu serveru.|
|[COleServerItem::SetItemName](#setitemname)|Nastaví název položky. Používá se pouze pro propojené položky.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleServerItem::GetDataSource](#getdatasource)|Získá objekt, který slouží k ukládání formátů převodu.|
|[COleServerItem::OnHide](#onhide)|Volat rámci skrýt položku OLE.|
|[COleServerItem::OnOpen](#onopen)|Volat rámci k zobrazení položky OLE ve vlastním okně nejvyšší úrovně.|
|[COleServerItem::OnShow](#onshow)|Volána, když kontejner požaduje zobrazit položku.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COleServerItem::m_sizeExtent](#m_sizeextent)|Informuje server o tom, kolik položky OLE je viditelné.|

## <a name="remarks"></a>Poznámky

Propojená položka může představovat část nebo celý dokument serveru. Vložená položka vždy představuje celý dokument serveru.

Třída `COleServerItem` definuje několik overridable členské funkce, které jsou volány knihovny dynamické propojení systému OLE (DLL), obvykle v reakci na požadavky z aplikace kontejneru. Tyto členské funkce umožňují aplikaci kontejneru manipulovat s položkou nepřímo různými způsoby, například zobrazením, spuštěním jejích sloves nebo načítáním dat v různých formátech.

Chcete-li použít `COleServerItem`, odvodit třídu z něj a implementovat [OnDraw](#ondraw) a [Serializovat](../../mfc/reference/cobject-class.md#serialize) členské funkce. Funkce `OnDraw` poskytuje reprezentaci metasouboru položky, což umožňuje její zobrazení při otevření aplikace kontejneru složený dokument. Funkce `Serialize` `CObject` poskytuje nativní reprezentaci položky, což umožňuje přenesení vložené položky mezi serverovými a kontejnerovými aplikacemi. [OnGetExtent](#ongetextent) poskytuje přirozenou velikost položky do kontejneru, povolení kontejneru velikost položky.

Další informace o serverech a souvisejících tématech naleznete v článku [Servery: Implementace serveru](../../mfc/servers-implementing-a-server.md) a Vytvoření aplikace kontejneru/serveru v článku [Kontejnery: Pokročilé funkce](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="coleserveritemaddotherclipboarddata"></a><a name="addotherclipboarddata"></a>COleServerItem::AddOtherClipboardData

Volání této funkce umístit formáty prezentace a převodu `COleDataSource` pro položku OLE v zadaném objektu.

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>Parametry

*pZdroj dat*<br/>
Ukazatel na `COleDataSource` objekt, ve kterém by měla být umístěna data.

### <a name="remarks"></a>Poznámky

Chcete-li poskytnout formát prezentace (obrázek metasouboru) pro položku, musíte implementovat členská funkci [OnDraw.](#ondraw) Chcete-li podporovat jiné formáty převodu, zaregistrujte je pomocí objektu [COleDataSource](../../mfc/reference/coledatasource-class.md) vráceném [getdatasource](#getdatasource) a přepište členskou funkci [OnRenderData,](#onrenderdata) abyste poskytli data ve formátech, které chcete podporovat.

## <a name="coleserveritemcoleserveritem"></a><a name="coleserveritem"></a>COleServerItem::COleServerItem

Vytvoří `COleServerItem` objekt a přidá jej do kolekce položek dokumentu serveru.

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*pServerDoc*<br/>
Ukazatel na dokument, který bude obsahovat novou položku.

*bAutoDelete*<br/>
Příznak označující, zda lze objekt odstranit při uvolnění odkazu na něj. Pokud je `COleServerItem` objekt nedílnou součástí dat dokumentu, které je nutné odstranit, nastavte tuto hodnotu na hodnotu NEPRAVDA. Tuto hodnotu nastavte na hodnotu TRUE, pokud se jedná o sekundární strukturu používanou k identifikaci oblasti v datech dokumentu, kterou lze odstranit v rámci.

## <a name="coleserveritemcopytoclipboard"></a><a name="copytoclipboard"></a>COleServerItem::CopyToClipboard

Volání této funkce zkopírovat položku OLE do schránky.

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>Parametry

*bIncludeLink*<br/>
Pokud mají být data propojení zkopírována do schránky, nastavte tuto hodnotu na hodnotu TRUE. Pokud serverová aplikace nepodporuje odkazy, nastavte tuto hodnotu na hodnotu NEPRAVDA.

### <a name="remarks"></a>Poznámky

Funkce používá členskou funkci [OnGetClipboardData](#ongetclipboarddata) k vytvoření objektu [COleDataSource](../../mfc/reference/coledatasource-class.md) obsahujícího data položky OLE v podporovaných formátech. Funkce pak umístí `COleDataSource` objekt do schránky pomocí funkce [COleDataSource::SetClipboard.](../../mfc/reference/coledatasource-class.md#setclipboard) Objekt `COleDataSource` obsahuje nativní data položky a její reprezentaci v CF_METAFILEPICT formátu a také data ve všech formátech převodu, které se rozhodnete podporovat. Musíte mít implementovány [Serialize](../../mfc/reference/cobject-class.md#serialize) a [OnDraw](#ondraw) pro tuto člennou funkci pracovat.

## <a name="coleserveritemdodragdrop"></a><a name="dodragdrop"></a>COleServerItem::DoDragDrop

Volání `DoDragDrop` členské funkce k provedení operace přetažení myší.

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
Obdélník položky na obrazovce, v obrazových bodech vzhledem k oblasti klienta.

*ptOffset*<br/>
Posun od *lpItemRect,* kde byla pozice myši v době přetažení.

*bIncludeLink*<br/>
Pokud mají být data propojení zkopírována do schránky, nastavte tuto hodnotu na hodnotu TRUE. Nastavte ji na HODNOTU FALSE, pokud aplikace nepodporuje odkazy.

*dwEfekty*<br/>
Určuje efekty, které zdroj přetažení povolí v operaci přetažení (kombinace Kopírovat, Přesunout a Propojit).

*lpRectStartDrag*<br/>
Ukazatel na obdélník, který definuje, kde přetažení skutečně začíná. Další informace naleznete v následující části poznámky.

### <a name="return-value"></a>Návratová hodnota

Hodnota z výčtu DROPEFFECT. Pokud je DROPEFFECT_MOVE, původní data by měla být odebrána.

### <a name="remarks"></a>Poznámky

Operace přetažení se nespustí okamžitě. Čeká, dokud kurzor myši opustí obdélník určený *lpRectStartDrag* nebo dokud neuplyne zadaný počet milisekund. Pokud *je lpRectStartDrag* null, použije se výchozí obdélník, aby se přetažení spustilo, když se kurzor myši přesune o jeden obrazový bod.

Doba zpoždění je určena nastavením klíče registru. Čas zpoždění můžete změnit voláním [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) nebo [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Pokud nezadáte čas zpoždění, použije se výchozí hodnota 200 milisekund. Doba zpoždění přetažení je uložena následujícím způsobem:

- Doba zpoždění přetažení systému Windows NT je uložena v HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- Windows 3.x Drag delay time je uložen v WIN. ini, v části [Windows}.

- Windows 95/98 Doba zpoždění přetažení je uložena ve verzi win uložené v mezipaměti. Ini.

Další informace o tom, jak jsou informace o zpoždění přetažení uloženy v registru nebo v . INI, viz [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) v sadě Windows SDK.

## <a name="coleserveritemgetclipboarddata"></a><a name="getclipboarddata"></a>COleServerItem::GetClipboardData

Volání této funkce vyplnit zadaný [COleDataSource](../../mfc/reference/coledatasource-class.md) objekt se všemi daty, které by byly zkopírovány do schránky, pokud jste [volali CopyToClipboard](#copytoclipboard) (stejná data by také být přeneseny, pokud jste [volali DoDragDrop](#dodragdrop)).

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>Parametry

*pZdroj dat*<br/>
Ukazatel na `COleDataSource` objekt, který obdrží data položky OLE ve všech podporovaných formátech.

*bIncludeLink*<br/>
TRUE, pokud by měla být data propojení zkopírována do schránky. FALSE, pokud serverová aplikace nepodporuje odkazy.

*lpOffset*<br/>
Posun kurzoru myši v obrazových bodech od počátku objektu.

*lpVelikost*<br/>
Velikost objektu v obrazových bodech.

### <a name="remarks"></a>Poznámky

Tato funkce volá členskou funkci [GetEmbedSourceData,](#getembedsourcedata) aby získala nativní data pro položku OLE, a zavolá členskou funkci [AddOtherClipboardData,](#addotherclipboarddata) aby získala formát prezentace a všechny podporované formáty převodu. Pokud *bIncludeLink* je PRAVDA, funkce také volá [GetLinkSourceData](#getlinksourcedata) získat data propojení pro položku.

Tuto funkci přepište, pokud chcete umístit `COleDataSource` formáty do objektu `CopyToClipboard`před nebo za tyto formáty dodané společností .

## <a name="coleserveritemgetdatasource"></a><a name="getdatasource"></a>COleServerItem::GetDataSource

Volání této funkce získat [COleDataSource](../../mfc/reference/coledatasource-class.md) objekt používaný k ukládání formátů převodu, které podporuje serverová aplikace.

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `COleDataSource` objekt použitý k uložení formátů převodu.

### <a name="remarks"></a>Poznámky

Pokud chcete, aby serverová aplikace nabízela data v různých formátech během operací `COleDataSource` přenosu dat, zaregistrujte tyto formáty s objektem vráceným touto funkcí. Chcete-li například zadat CF_TEXT reprezentaci položky OLE pro funkci Schránka nebo operace `COleDataSource` přetažení, zaregistrujte formát `OnRenderXxxData` s objektem, který tato funkce vrátí, a potom přepsat členskou funkci, aby byla data poskytnuta.

## <a name="coleserveritemgetdocument"></a><a name="getdocument"></a>COleServerItem::GetDocument

Volání této funkce získat ukazatel na dokument, který obsahuje položku.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dokument, který obsahuje položku; Null, pokud položka není součástí dokumentu.

### <a name="remarks"></a>Poznámky

To umožňuje přístup k dokumentu serveru, který `COleServerItem` jste předali jako argument konstruktoru.

## <a name="coleserveritemgetembedsourcedata"></a><a name="getembedsourcedata"></a>COleServerItem::GetEmbedSourceData

Volání této funkce získat CF_EMBEDSOURCE data pro položku OLE.

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpStgStřední*<br/>
Ukazatel na [stgmedium](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) strukturu, která obdrží CF_EMBEDSOURCE data pro položku OLE.

### <a name="remarks"></a>Poznámky

Tento formát obsahuje nativní data položky. Chcete-li, `Serialize` aby tato funkce fungovala správně, je nutné implementovat členská funkci.

Výsledek pak lze přidat do zdroje dat pomocí [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Tato funkce je volána automaticky [COleServerItem::OnGetClipboardData](#ongetclipboarddata).

Další informace naleznete v tématu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) v sadě Windows SDK.

## <a name="coleserveritemgetitemname"></a><a name="getitemname"></a>COleServerItem::GetItemName

Volání této funkce získat název položky.

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název položky.

### <a name="remarks"></a>Poznámky

Obvykle voláte tuto funkci pouze pro propojené položky.

## <a name="coleserveritemgetlinksourcedata"></a><a name="getlinksourcedata"></a>COleServerItem::GetLinkSourceData

Volání této funkce získat CF_LINKSOURCE data pro položku OLE.

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpStgStřední*<br/>
Ukazatel na [stgmedium](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) strukturu, která obdrží CF_LINKSOURCE data pro položku OLE.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tento formát zahrnuje CLSID popisující typ položky OLE a informace potřebné k vyhledání dokumentu obsahujícího položku OLE.

Výsledek pak lze přidat do zdroje dat s [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Tato funkce je volána automaticky [OnGetClipboardData](#ongetclipboarddata).

Další informace naleznete v tématu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) v sadě Windows SDK.

## <a name="coleserveritemgetobjectdescriptordata"></a><a name="getobjectdescriptordata"></a>COleServerItem::GetObjectDescriptorData

Volání této funkce získat CF_OBJECTDESCRIPTOR data pro položku OLE.

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpOffset*<br/>
Posun klepnutí myší z levého horního rohu položky OLE. Může být NULL.

*lpVelikost*<br/>
Velikost položky OLE. Může být NULL.

*lpStgStřední*<br/>
Ukazatel na [stgmedium](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) strukturu, která obdrží CF_OBJECTDESCRIPTOR data pro položku OLE.

### <a name="remarks"></a>Poznámky

Informace jsou zkopírovány do `STGMEDIUM` struktury, na kterou poukazuje *lpStgMedium*. Tento formát obsahuje informace potřebné pro dialogové okno Vložit jinak.

Další informace naleznete v tématu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) v sadě Windows SDK.

## <a name="coleserveritemisconnected"></a><a name="isconnected"></a>COleServerItem::Jepřipojeno

Volání této funkce zobrazíte, pokud je připojena položka OLE.

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je položka připojena; jinak 0.

### <a name="remarks"></a>Poznámky

Položka OLE je považována za připojenou, pokud jeden nebo více kontejnerů má odkazy na položku. Položka je připojena, pokud je její počet odkazů větší než 0 nebo pokud se jedná o vloženou položku.

## <a name="coleserveritemislinkeditem"></a><a name="islinkeditem"></a>COleServerItem::IsLinkedItem

Volání této funkce zobrazíte, pokud položka OLE je propojená položka.

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je položka propojená položka; jinak 0.

### <a name="remarks"></a>Poznámky

Položka je propojena, pokud je položka platná a není vrácena v seznamu vložených položek dokumentu. Propojená položka může nebo nemusí být připojena ke kontejneru.

Je běžné používat stejnou třídu pro propojené i vložené položky. `IsLinkedItem`umožňuje, aby se propojené položky chovaly jinak než vložené položky, i když mnohokrát je kód běžný.

## <a name="coleserveritemm_sizeextent"></a><a name="m_sizeextent"></a>COleServerItem::m_sizeExtent

Tento člen informuje server, kolik objektu je viditelné v dokumentu kontejneru.

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>Poznámky

Výchozí implementace [OnSetExtent](#onsetextent) nastaví tento člen.

## <a name="coleserveritemnotifychanged"></a><a name="notifychanged"></a>COleServerItem::NotifyChanged

Volání této funkce po změně propojené položky.

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Hodnota z výčtu DVASPECT, která označuje, který aspekt položky OLE se změnil. Tento parametr může mít některou z následujících hodnot:

- DVASPECT_CONTENT Item je reprezentován a to takovým způsobem, že může být zobrazen jako vložený objekt uvnitř kontejneru.

- DVASPECT_THUMBNAIL Položka je vykreslena v "miniatuře", aby ji bylo možné zobrazit v nástroji pro procházení.

- DVASPECT_ICON položka je reprezentována ikonou.

- DVASPECT_DOCPRINT Položka je reprezentována, jako by byla vytištěna pomocí příkazu Tisk z nabídky Soubor.

### <a name="remarks"></a>Poznámky

Pokud je položka kontejneru propojena s dokumentem s automatickým propojením, položka se aktualizuje tak, aby odrážela změny. V kontejnerových aplikacích napsaných pomocí knihovny tříd Microsoft Foundation je [cOleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange) volána jako odpověď.

## <a name="coleserveritemondoverb"></a><a name="ondoverb"></a>ColeServerItem::Ondoverb

Volat rámci k provedení zadané sloveso.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iSponož*<br/>
Určuje sloveso, které má být spuštěno. Může to být některá z následujících možností:

|Hodnota|Význam|Symbol|
|-----------|-------------|------------|
|0|primární požadavek|OLEIVERB_PRIMARY|
|1|Sekundární sloveso|(None)|
|- 1|Zobrazit položku pro úpravy|OLEIVERB_SHOW|
|- 2|Upravit položku v samostatném okně|OLEIVERB_OPEN|
|- 3|Skrýt položku|OLEIVERB_HIDE|

Hodnota -1 je obvykle alias pro jiné sloveso. Pokud otevřené úpravy není podporována, -2 má stejný účinek jako -1. Další hodnoty naleznete v tématu [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud byla aplikace kontejneru zapsána pomocí knihovny tříd Microsoft Foundation, je tato funkce volána, když je volána členská funkce [COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate) členské funkce odpovídajícího `COleClientItem` objektu. Výchozí implementace volá členskou funkci [OnShow,](#onshow) pokud je zadáno primární sloveso nebo OLEIVERB_SHOW, [OnOpen,](#onopen) pokud je zadáno sekundární sloveso nebo OLEIVERB_OPEN, a [OnHide,](#onhide) pokud je zadánOLEIVERB_HIDE. Výchozí volání `OnShow` implementace, pokud *iVerb* není jedním z výše uvedených sloves.

Přepsat tuto funkci, pokud primární sloveso nezobrazuje položku. Pokud je například položka zvukovou nahrávkou a její primární sloveso je Přehrát, nebudete muset zobrazit serverovou aplikaci pro přehrání položky.

Další informace naleznete v tématu [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) v sadě Windows SDK.

## <a name="coleserveritemondraw"></a><a name="ondraw"></a>COleServerItem::Ondraw

Volat rámci k vykreslení položky OLE do metasouboru.

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na [cdc](../../mfc/reference/cdc-class.md) objekt, na kterém chcete nakreslit položku. Kontext zobrazení je automaticky připojen k kontextu zobrazení atributu, takže můžete volat funkce atributu, i když by to metasoubor specifické pro zařízení.

*rVelikost*<br/>
Velikost, v jednotkách HIMETRIC, ve kterém chcete nakreslit metasoubor.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla položka úspěšně vylosována; jinak 0.

### <a name="remarks"></a>Poznámky

Reprezentace metasouboru položky OLE se používá k zobrazení položky v aplikaci kontejneru. Pokud byla aplikace kontejneru napsána pomocí knihovny tříd Microsoft Foundation, metasoubor je používán členskou funkcí [Draw](../../mfc/reference/coleclientitem-class.md#draw) odpovídajícího objektu [COleClientItem.](../../mfc/reference/coleclientitem-class.md) Neexistuje žádná výchozí implementace. Chcete-li položku nakreslit do zadaného kontextu zařízení, je nutné přepsat tuto funkci.

## <a name="coleserveritemondrawex"></a><a name="ondrawex"></a>COleServerItem::OnDrawEx

Nazývá rámec pro všechny výkresy.

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na [cdc](../../mfc/reference/cdc-class.md) objekt, na kterém chcete nakreslit položku. Řadič domény je automaticky připojen k atributu DC, takže můžete volat funkce atributu, i když by to metafile specifické pro zařízení.

*nDrawAspect*<br/>
Hodnota z výčtu DVASPECT. Tento parametr může mít některou z následujících hodnot:

- DVASPECT_CONTENT Item je reprezentován a to takovým způsobem, že může být zobrazen jako vložený objekt uvnitř kontejneru.

- DVASPECT_THUMBNAIL Položka je vykreslena v "miniatuře", aby ji bylo možné zobrazit v nástroji pro procházení.

- DVASPECT_ICON položka je reprezentována ikonou.

- DVASPECT_DOCPRINT Položka je reprezentována, jako by byla vytištěna pomocí příkazu Tisk z nabídky Soubor.

*rVelikost*<br/>
Velikost položky v jednotkách HIMETRIC.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla položka úspěšně vylosována; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace `OnDraw` volá, když DVASPECT se rovná DVASPECT_CONTENT; v opačném případě selže.

Přepsat tuto funkci poskytnout data prezentace pro aspekty než DVASPECT_CONTENT, jako je například DVASPECT_ICON nebo DVASPECT_THUMBNAIL.

## <a name="coleserveritemongetclipboarddata"></a><a name="ongetclipboarddata"></a>COleServerItem::OnGetClipboardData

Volat rámci získat `COleDataSource` objekt obsahující všechna data, která by byla umístěna na schránce voláním [CopyToClipboard](#copytoclipboard) členské funkce.

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>Parametry

*bIncludeLink*<br/>
Pokud mají být data propojení zkopírována do schránky, nastavte tuto hodnotu na hodnotu TRUE. Pokud serverová aplikace nepodporuje odkazy, nastavte tuto hodnotu na hodnotu NEPRAVDA.

*lpOffset*<br/>
Posun kurzoru myši od počátku objektu v obrazových bodech.

*lpVelikost*<br/>
Velikost objektu v obrazových bodech.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [cOleDataSource](../../mfc/reference/coledatasource-class.md) objekt obsahující data schránky.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce volá [GetClipboardData](#getclipboarddata).

## <a name="coleserveritemongetextent"></a><a name="ongetextent"></a>COleServerItem::OnGetExtent

Volat rámci načíst velikost, v jednotkách HIMETRIC položky OLE.

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Určuje aspekt položky OLE, jejíž hranice mají být načteny. Tento parametr může mít některou z následujících hodnot:

- DVASPECT_CONTENT Item je reprezentován a to takovým způsobem, že může být zobrazen jako vložený objekt uvnitř kontejneru.

- DVASPECT_THUMBNAIL Položka je vykreslena v "miniatuře", aby ji bylo možné zobrazit v nástroji pro procházení.

- DVASPECT_ICON položka je reprezentována ikonou.

- DVASPECT_DOCPRINT Položka je reprezentována, jako by byla vytištěna pomocí příkazu Tisk z nabídky Soubor.

*rVelikost*<br/>
Odkaz na `CSize` objekt, který obdrží velikost položky OLE.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud byla aplikace kontejneru napsána pomocí knihovny tříd Microsoft Foundation, je `COleClientItem` tato funkce volána při volání členské funkce [GetExtent](../../mfc/reference/coleclientitem-class.md#getextent) odpovídajícího objektu. Výchozí implementace neprovede žádné provádění. Musíte ji implementovat sami. Přepsat tuto funkci, pokud chcete provést speciální zpracování při zpracování požadavku na velikost položky OLE.

## <a name="coleserveritemonhide"></a><a name="onhide"></a>COleServerItem::OnHide

Volat rámci skrýt položku OLE.

```
virtual void OnHide();
```

### <a name="remarks"></a>Poznámky

Výchozí volání `COleServerDoc::OnShowDocument( FALSE )`. Funkce také upozorní kontejner, že položka OLE byla skryta. Přepsat tuto funkci, pokud chcete provést speciální zpracování při skrytí položky OLE.

## <a name="coleserveritemoninitfromdata"></a><a name="oninitfromdata"></a>COleServerItem::OnInitFromData

Volat rámci inicializovat položku OLE pomocí obsahu *pDataObject*.

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>Parametry

*objekt pDataObject*<br/>
Ukazatel na datový objekt OLE obsahující data v různých formátech pro inicializaci položky OLE.

*bTvorba*<br/>
PRAVDA, pokud je funkce volána k inicializaci položky OLE nově vytvořené aplikací kontejneru. FALSE, pokud je funkce volána jako náhrada obsahu již existující položky OLE.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *bCreation* je PRAVDA, tato funkce je volána, pokud kontejner implementuje Vložit nový objekt na základě aktuálního výběru. Vybraná data se použijí při vytváření nové položky OLE. Například při výběru oblasti buněk v tabulkovém procesoru a následném vytvoření grafu na základě hodnot ve vybrané oblasti pomocí příkazu Vložit nový objekt. Výchozí implementace neprovede žádné provádění. Přepište tuto funkci a zvolte přijatelný formát z těch, které nabízí *pDataObject* a inicializovat položku OLE na základě poskytnutých dat. Tohle je pokročilé překažné.

Další informace naleznete v [tématu IOleObject::InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) v sadě Windows SDK.

## <a name="coleserveritemonopen"></a><a name="onopen"></a>COleServerItem::OnOpen

Volat rámci k zobrazení položky OLE v samostatné instanci serverové aplikace, nikoli na místě.

```
virtual void OnOpen();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace aktivuje první okno rámce zobrazující dokument, který obsahuje položku OLE; Pokud je aplikace mini-server, výchozí implementace zobrazuje hlavní okno. Funkce také upozorní kontejner, že položka OLE byla otevřena.

Přepsat tuto funkci, pokud chcete provést speciální zpracování při otevírání položky OLE. To je běžné zejména u propojených položek, kde chcete nastavit výběr na odkaz při jeho otevření.

Další informace naleznete v tématu [IOleClientSite::OnShowWindow](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) v sadě Windows SDK.

## <a name="coleserveritemonqueryupdateitems"></a><a name="onqueryupdateitems"></a>ColeServerItem::OnQueryUpdateItems

Volat rámci k určení, zda všechny propojené položky v aktuálním dokumentu serveru jsou zastaralé.

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud dokument obsahuje položky, které potřebují aktualizace; 0, pokud jsou všechny položky aktuální.

### <a name="remarks"></a>Poznámky

Položka je zastaralá, pokud byl její zdrojový dokument změněn, ale propojená položka nebyla aktualizována tak, aby odrážela změny v dokumentu.

## <a name="coleserveritemonrenderdata"></a><a name="onrenderdata"></a>COleServerItem::OnRenderData

Volat rámci načíst data v zadaném formátu.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) strukturu určující formát, ve kterém jsou požadovány informace.

*lpStgStřední*<br/>
Odkazuje na [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) strukturu, ve kterém mají být vrácena data.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je dříve `COleDataSource` umístěn v objektu pomocí [delayrenderdata](../../mfc/reference/coledatasource-class.md#delayrenderdata) nebo [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) členfunkce pro zpožděné vykreslování. Výchozí implementace této funkce volá [OnRenderFileData](#onrenderfiledata) nebo [OnRenderGlobalData](#onrenderglobaldata), pokud je dodané paměťové médium soubor emituje nebo paměť. Pokud není zadán ani jeden z těchto formátů, výchozí implementace vrátí 0 a neprovede žádné.

Pokud *lpStgMedium*-> *tymed* je TYMED_NULL, STGMEDIUM by měla být přidělena a vyplněna podle *lpFormatEtc->tymed*. Pokud není TYMED_NULL, STGMEDIUM by měla být vyplněna na místě s daty.

Tohle je pokročilé překažné. Přepište tuto funkci a poskytněte data v požadovaném formátu a médiu. V závislosti na datech můžete místo toho přepsat jednu z dalších verzí této funkce. Pokud jsou data malá a pevná, přepište . `OnRenderGlobalData` Pokud jsou data v souboru nebo mají proměnnou velikost, přepište to `OnRenderFileData`.

Další informace naleznete v [tématech IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)a [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) v sadách Windows SDK.

## <a name="coleserveritemonrenderfiledata"></a><a name="onrenderfiledata"></a>COleServerItem::OnRenderFileData

Volat rámci načíst data v zadaném formátu, když médium úložiště je soubor.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) strukturu určující formát, ve kterém jsou požadovány informace.

*pSoubor*<br/>
Odkazuje na `CFile` objekt, ve kterém mají být data vykreslena.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je dříve `COleDataSource` umístěn v objektu pomocí [delayrenderdata](../../mfc/reference/coledatasource-class.md#delayrenderdata) členské funkce pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrátí hodnotu NEPRAVDA.

Tohle je pokročilé překažné. Přepište tuto funkci a poskytněte data v požadovaném formátu a médiu. V závislosti na datech můžete místo toho přepsat jednu z dalších verzí této funkce. Pokud chcete zpracovat více paměťových médií, přepište [OnRenderData](#onrenderdata). Pokud jsou data v souboru nebo má proměnnou velikost, přepište [onRenderFileData](#onrenderfiledata).

Další informace naleznete v tématu [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) a [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v sadě Windows SDK.

## <a name="coleserveritemonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleServerItem::OnRenderGlobalData

Volat rámci načíst data v zadaném formátu, pokud zadané paměťové médium je globální paměti.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) strukturu určující formát, ve kterém jsou požadovány informace.

*phGlobální*<br/>
Odkazuje na popisovač globální paměti, ve kterém mají být vrácena data. Pokud nebyla přidělena žádná paměť, může být tento parametr null.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je dříve `COleDataSource` umístěn v objektu pomocí [delayrenderdata](../../mfc/reference/coledatasource-class.md#delayrenderdata) členské funkce pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrátí hodnotu NEPRAVDA.

Pokud *phGlobal* je NULL, pak nový HGLOBAL by měly být přiděleny a vráceny v *phGlobal*. V opačném případě hglobal určené *phGlobal* by měla být vyplněna data. Množství dat umístěných v HGLOBAL nesmí překročit aktuální velikost bloku paměti. Také blok nelze přerozděleny na větší velikost.

Tohle je pokročilé překažné. Přepište tuto funkci a poskytněte data v požadovaném formátu a médiu. V závislosti na datech můžete místo toho přepsat jednu z dalších verzí této funkce. Pokud chcete zpracovat více paměťových médií, přepište [OnRenderData](#onrenderdata). Pokud jsou data v souboru nebo má proměnnou velikost, přepište [onRenderFileData](#onrenderfiledata).

Další informace naleznete v tématu [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) a [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v sadě Windows SDK.

## <a name="coleserveritemonsetcolorscheme"></a><a name="onsetcolorscheme"></a>COleServerItem::onsetcolorscheme

Volat rámci určit paletu barev, které mají být použity při úpravách položky OLE.

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>Parametry

*lpLogPalette*<br/>
Ukazatel na strukturu Windows [LOGPALETTE.](/windows/win32/api/wingdi/ns-wingdi-logpalette)

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud se používá paleta barev; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud byla aplikace kontejneru zapsána pomocí knihovny tříd Microsoft Foundation, je tato funkce volána, když je volána funkce [IOleObject::SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) odpovídajícího `COleClientItem` objektu. Výchozí implementace vrátí hodnotu NEPRAVDA. Přepsat tuto funkci, pokud chcete použít doporučenou paletu. Serverová aplikace není nutné používat navrhovanou paletu.

Další informace naleznete v tématu [IOleObject::SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) v sadě Windows SDK.

## <a name="coleserveritemonsetdata"></a><a name="onsetdata"></a>coleserveritem::onsetdata

Volat rámci nahradit data položky OLE zadanými daty.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Ukazatel na [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) strukturu určující formát dat.

*lpStgStřední*<br/>
Ukazatel na [stgmedium](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) strukturu, ve kterém jsou data umístěna.

*bUvolnění*<br/>
Označuje, kdo má vlastnictví paměťového média po dokončení volání funkce. Volající rozhodne, kdo je zodpovědný za uvolnění prostředků přidělených jménem paměťového média. Volající to provádí nastavením *bRelease*. Pokud *bRelease* je nenulová, položka serveru přebírá vlastnictví, uvolnění média po dokončení jeho použití. Když *bRelease* je 0, volající si zachová vlastnictví a položka serveru můžete použít paměťové médium pouze po dobu trvání volání.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Položka serveru nepřevezme vlastnictví dat, dokud je úspěšně nezíská. To znamená, že nepřevezme vlastnictví, pokud vrátí 0. Pokud zdroj dat převezme vlastnictví, uvolní paměťové médium voláním [releasestgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) funkce.

Výchozí implementace neprovede žádné provádění. Přepište tuto funkci a nahraďte data položky OLE zadanými daty. Tohle je pokročilé překažné.

Další informace naleznete v tématech [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)a [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) v sadě Windows SDK.

## <a name="coleserveritemonsetextent"></a><a name="onsetextent"></a>COleServerItem::Délkarozsahu

Volat rámci sdělit ole položku, kolik místa je k dispozici v dokumentu kontejneru.

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Určuje aspekt položky OLE, jejíž hranice jsou zadávány. Tento parametr může mít některou z následujících hodnot:

- DVASPECT_CONTENT Item je reprezentován a to takovým způsobem, že může být zobrazen jako vložený objekt uvnitř kontejneru.

- DVASPECT_THUMBNAIL Položka je vykreslena v "miniatuře", aby ji bylo možné zobrazit v nástroji pro procházení.

- DVASPECT_ICON položka je reprezentována ikonou.

- DVASPECT_DOCPRINT Položka je reprezentována, jako by byla vytištěna pomocí příkazu Tisk z nabídky Soubor.

*Velikost*<br/>
A [CSize](../../atl-mfc-shared/reference/csize-class.md) struktura určující novou velikost položky OLE.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud byla aplikace kontejneru napsána pomocí knihovny tříd Microsoft Foundation, je `COleClientItem` tato funkce volána při volání členské funkce [SetExtent](../../mfc/reference/coleclientitem-class.md#setextent) odpovídajícího objektu. Výchozí implementace nastaví [člen m_sizeExtent](#m_sizeextent) na zadanou velikost, pokud je DVASPECT_CONTENT *nDrawAspect;* jinak vrátí 0. Přepište tuto funkci a proveďte speciální zpracování při změně velikosti položky.

## <a name="coleserveritemonshow"></a><a name="onshow"></a>COleServerItem::OnShow

Volat rámci pokyn serverové aplikace k zobrazení položky OLE na místě.

```
virtual void OnShow();
```

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána, když uživatel aplikace kontejneru vytvoří položku nebo provede sloveso, například Upravit, které vyžaduje, aby se položka zobrazila. Výchozí implementace se pokusí na místě aktivace. Pokud se to nezdaří, funkce zavolá členskou `OnOpen` funkci k zobrazení položky OLE v samostatném okně.

Přepsat tuto funkci, pokud chcete provést speciální zpracování při zobrazení položky OLE.

## <a name="coleserveritemonupdate"></a><a name="onupdate"></a>COleServerItem::OnUpdate

Volat rámci při změně položky.

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>Parametry

*pOdesílatelí*<br/>
Ukazatel na položku, která dokument upravila. Může být NULL.

*lTip*<br/>
Obsahuje informace o úpravě.

*pHint*<br/>
Ukazatel na objekt ukládající informace o změně.

*nDrawAspect*<br/>
Hodnota z výčtu DVASPECT. Tento parametr může mít některou z následujících hodnot:

- DVASPECT_CONTENT Item je reprezentován a to takovým způsobem, že může být zobrazen jako vložený objekt uvnitř kontejneru.

- DVASPECT_THUMBNAIL Položka je vykreslena v "miniatuře", aby ji bylo možné zobrazit v nástroji pro procházení.

- DVASPECT_ICON položka je reprezentována ikonou.

- DVASPECT_DOCPRINT Položka je reprezentována, jako by byla vytištěna pomocí příkazu Tisk z nabídky Soubor.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá [NotifyChanged](#notifychanged), bez ohledu na nápovědu nebo odesílatele.

## <a name="coleserveritemonupdateitems"></a><a name="onupdateitems"></a>COleServerItem::OnUpdateItems

Volat rámci aktualizovat všechny položky v dokumentu serveru.

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace volá [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) pro všechny `COleClientItem` objekty v dokumentu.

## <a name="coleserveritemsetitemname"></a><a name="setitemname"></a>COleServerItem::SetItemName

Tuto funkci volání při vytváření propojené položky nastavit její název.

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
Ukazatel na nový název položky.

### <a name="remarks"></a>Poznámky

Název musí být jedinečný v dokumentu. Pokud je serverová aplikace volána k úpravám propojené položky, použije tento název k vyhledání položky. Není nutné volat tuto funkci pro vložené položky.

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem – třída](../../mfc/reference/cdocitem-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)<br/>
[Třída COleServerDoc](../../mfc/reference/coleserverdoc-class.md)<br/>
[Třída COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
