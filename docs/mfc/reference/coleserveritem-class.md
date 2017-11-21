---
title: "Třída COleServerItem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f56f356de8cb85bb919469a189618220c0843f3d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="coleserveritem-class"></a>COleServerItem – třída
Poskytuje rozhraní serveru položkám OLE.  
  
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
  
|Název|Popis|  
|----------|-----------------|  
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|Prezentační a převod formátů v umístí `COleDataSource` objektu.|  
|[COleServerItem::CopyToClipboard](#copytoclipboard)|Kopíruje položku do schránky.|  
|[COleServerItem::DoDragDrop](#dodragdrop)|Provede operaci přetažení myší.|  
|[COleServerItem::GetClipboardData](#getclipboarddata)|Získá zdroj dat pro použití v přenos dat (přetahování nebo schránky).|  
|[COleServerItem::GetDocument](#getdocument)|Vrátí dokumentu na serveru, který obsahuje položky.|  
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|Získá **CF_EMBEDSOURCE** dat položky OLE.|  
|[COleServerItem::GetItemName](#getitemname)|Vrací název položky. Používá se pouze propojené položky.|  
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|Získá `CF_LINKSOURCE` dat položky OLE.|  
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|Získá **CF_OBJECTDESCRIPTOR** dat položky OLE.|  
|[COleServerItem::IsConnected](#isconnected)|Určuje, zda položka je aktuálně připojena k active kontejneru.|  
|[COleServerItem::IsLinkedItem](#islinkeditem)|Určuje, zda položka reprezentuje propojené položky OLE.|  
|[COleServerItem::NotifyChanged](#notifychanged)|Aktualizuje všechny kontejnery aktualizace automatické propojení.|  
|[COleServerItem::OnDoVerb](#ondoverb)|Volá se provést operaci.|  
|[COleServerItem::OnDraw](#ondraw)|Voláno, když kontejneru požaduje k vykreslení položky; implementace vyžaduje.|  
|[COleServerItem::OnDrawEx](#ondrawex)|Volá se pro kreslení specializované položky.|  
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|Voláno rámcem získat data, která bude zkopírován do schránky.|  
|[COleServerItem::OnGetExtent](#ongetextent)|Voláno rámcem načíst velikost položky OLE.|  
|[COleServerItem::OnInitFromData](#oninitfromdata)|Voláno rámcem k chybě při inicializaci obsah zadaného objektu přenos dat pomocí položky OLE.|  
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|Voláno k určení, zda všechny propojené položky vyžadují aktualizaci.|  
|[COleServerItem::OnRenderData](#onrenderdata)|Načte data v rámci zpožděné vykreslování.|  
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|Načítání dat do `CFile` objektu jako součást zpožděné vykreslování.|  
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|Načte data do `HGLOBAL` jako součást zpožděné vykreslování.|  
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|Volá se pro nastavení položky barevné schéma.|  
|[COleServerItem::OnSetData](#onsetdata)|Voláno k nastavení dat položky.|  
|[COleServerItem::OnSetExtent](#onsetextent)|Voláno rámcem nastavit velikost položky OLE.|  
|[COleServerItem::OnUpdate](#onupdate)|Volá se při patří některé části dokumentu, položka se změní.|  
|[COleServerItem::OnUpdateItems](#onupdateitems)|Volat za účelem aktualizace mezipaměti prezentace všechny položky v dokumentu na serveru.|  
|[COleServerItem::SetItemName](#setitemname)|Nastaví název položky. Používá se pouze propojené položky.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleServerItem::GetDataSource](#getdatasource)|Získá objekt použitý k uložení převod formátů.|  
|[COleServerItem::OnHide](#onhide)|Voláno rámcem ke skrytí položek OLE.|  
|[COleServerItem::OnOpen](#onopen)|Voláno rámcem zobrazíte položky OLE v samostatném okně nejvyšší úrovně.|  
|[COleServerItem::OnShow](#onshow)|Voláno, když kontejneru požaduje zobrazíte položky.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleServerItem::m_sizeExtent](#m_sizeextent)|Server informuje o tom, kolik položek OLE je viditelné.|  
  
## <a name="remarks"></a>Poznámky  
 Propojené položky může představovat některé nebo všechny dokumentu na serveru. Vložené položky vždy představuje dokument celý server.  
  
 `COleServerItem` Třída definuje několik přepisovatelné členské funkce, které jsou volány OLE systému dynamické knihovny (DLL), obvykle v reakci na požadavky z aplikace kontejneru. Povolit tyto členské funkce kontejneru aplikace k manipulaci s položka nepřímo různými způsoby, například jeho zobrazení, provádění jeho příkazy nebo načítá data v různých formátech.  
  
 Chcete-li použít `COleServerItem`, odvození třídy z něj a implementaci [OnDraw –](#ondraw) a [serializace](../../mfc/reference/cobject-class.md#serialize) členské funkce. `OnDraw` Funkce poskytuje reprezentaci metafile položky, díky kterému jej zobrazí, když aplikace kontejneru otevře složeného dokumentu. `Serialize` Funkce `CObject` poskytuje nativní reprezentaci položky, povolení vložené položky přenos mezi aplikacemi serveru a kontejneru. [OnGetExtent](#ongetextent) poskytuje přirozené velikost položky do kontejneru, povolení kontejner, aby velikost položky.  
  
 Další informace o serverech a související témata, najdete v článku [servery: implementace serveru](../../mfc/servers-implementing-a-server.md) a "Vytváření Server/kontejner aplikace" v článku [kontejnery: pokročilé funkce](../../mfc/containers-advanced-features.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleServerItem`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="addotherclipboarddata"></a>COleServerItem::AddOtherClipboardData  
 Volání této funkce umístit prezentace a převod formátů pro OLE položku v zadané `COleDataSource` objektu.  
  
```  
void AddOtherClipboardData(COleDataSource* pDataSource);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataSource`  
 Ukazatel `COleDataSource` objektu, ve kterém má být umístěn data.  
  
### <a name="remarks"></a>Poznámky  
 Jste implementovali [OnDraw –](#ondraw) – členská funkce určení formátu prezentace (obrázek metafile) pro položku. Pro podporu dalších formátů převodu, zaregistrujte je pomocí [coledatasource –](../../mfc/reference/coledatasource-class.md) objekt vrácený [GetDataSource](#getdatasource) a přepsat [OnRenderData](#onrenderdata) členské funkce Zadejte data v formáty, které chcete podporovat.  
  
##  <a name="coleserveritem"></a>COleServerItem::COleServerItem  
 Vytvoří `COleServerItem` objektu a přidává ji k dokumentu server kolekce položek dokumentu.  
  
```  
COleServerItem(
    COleServerDoc* pServerDoc,  
    BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Parametry  
 `pServerDoc`  
 Ukazatel na dokument, který bude obsahovat nová položka.  
  
 `bAutoDelete`  
 Příznak, který udává, zda objekt může být odstraněny při odkazu na vydání. Tuto možnost nastavíte na **FALSE** Pokud `COleServerItem` objekt je nedílnou součástí vašeho dokumentu data, která je nutné odstranit. Tuto možnost nastavíte na **TRUE** Pokud se objekt sekundární struktura použít k identifikaci rozsah v datech vašeho dokumentu, který může odstranit rozhraní.  
  
##  <a name="copytoclipboard"></a>COleServerItem::CopyToClipboard  
 Volání této funkce OLE položku zkopírovat do schránky.  
  
```  
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `bIncludeLink`  
 Tuto možnost nastavíte na **TRUE** Pokud data propojení by se měl zkopírovat do schránky. Tuto možnost nastavíte na **FALSE** Pokud vaše serverová aplikace nepodporuje odkazy.  
  
### <a name="remarks"></a>Poznámky  
 Funkce, která používá [OnGetClipboardData](#ongetclipboarddata) – členská funkce k vytvoření [coledatasource –](../../mfc/reference/coledatasource-class.md) objekt obsahující data OLE položky v formátů podporovaných. Funkce pak umístí `COleDataSource` objektu do schránky pomocí [COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) funkce. `COleDataSource` Objekt zahrnuje nativní datové položky a jeho reprezentace v `CF_METAFILEPICT` formátu, jakož i dat v jakékoli převod formátů rozhodnete podporovat. Jste implementovali [serializace](../../mfc/reference/cobject-class.md#serialize) a [OnDraw –](#ondraw) pro tento člen funkce fungovat.  
  
##  <a name="dodragdrop"></a>COleServerItem::DoDragDrop  
 Volání `DoDragDrop` – členská funkce k provedení operace přetažení myší.  
  
```  
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,  
    CPoint ptOffset,  
    BOOL bIncludeLink = FALSE,  
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,  
    LPCRECT lpRectStartDrag = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpRectItem*  
 Položky obdélníku na obrazovce, v pixelech, relativně k klientské oblasti.  
  
 `ptOffset`  
 Posun od `lpItemRect` kde pozice myši byl v době přetahování.  
  
 `bIncludeLink`  
 Tuto možnost nastavíte na **TRUE** Pokud data propojení by se měl zkopírovat do schránky. Nastavte ji na **FALSE** Pokud vaše aplikace nepodporuje odkazy.  
  
 `dwEffects`  
 Určuje účinky, které vám umožní zdroje operace přetažení v operaci přetažení (kombinaci kopírovat, přesunout a odkaz).  
  
 `lpRectStartDrag`  
 Ukazatel na obdélníku, která definuje, kde přetáhněte skutečně spustí. Další informace naleznete v následující části poznámky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota z `DROPEFFECT` výčtu. Pokud je `DROPEFFECT_MOVE`, měla by být odebrána původní data.  
  
### <a name="remarks"></a>Poznámky  
 Operaci přetažení myší nespustí okamžitě. Čeká, dokud myší opustí rámeček určeného `lpRectStartDrag` nebo dokud předané zadaný počet milisekund. Pokud `lpRectStartDrag` je **NULL**, obdélníku výchozí se používá, aby přetahování spustí, když se ukazatelem myši přesune o bod.  
  
 Doba zpoždění je určena nastavení klíče registru. Doba zpoždění lze změnit pomocí volání [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) nebo [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Pokud nezadáte čas zpoždění, se používá výchozí hodnota je 200 MS. Doba zpoždění přetažení se ukládají následujícím způsobem:  
  
-   Doba zpoždění systému Windows NT přetáhněte je uložená v HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.  
  
-   Doba zpoždění přetáhněte 3.x Windows je uložená v WIN. Soubor INI, části [Windows}.  
  
-   Doba zpoždění Windows 95/98 přetáhněte je uložená v mezipaměti verzi WIN. INI.  
  
 Pro další informace o tom, přetáhněte zpoždění informace jsou uloženy v registru buď nebo. Soubor INI, najdete v části [WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) ve Windows SDK.  
  
##  <a name="getclipboarddata"></a>COleServerItem::GetClipboardData  
 Volání této funkce k vyplnění zadaný [coledatasource –](../../mfc/reference/coledatasource-class.md) objekt se všechna data, která bude zkopírován do schránky, pokud jste volali metodu [CopyToClipboard](#copytoclipboard) (stejná data se přenáší taky, pokud jste volá se [metody DoDragDrop](#dodragdrop)).  
  
```  
void GetClipboardData(
    COleDataSource* pDataSource,  
    BOOL bIncludeLink = FALSE,  
    LPPOINT lpOffset = NULL,  
    LPSIZE lpSize = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataSource`  
 Ukazatel `COleDataSource` objekt, který bude přijímat data OLE položky ve všech podporovaných formátů.  
  
 `bIncludeLink`  
 **Hodnota TRUE,** Pokud data propojení by se měl zkopírovat do schránky. **FALSE** Pokud vaše serverová aplikace nepodporuje odkazy.  
  
 `lpOffset`  
 Posun v pixelech myší z tohoto počátku objektu.  
  
 `lpSize`  
 Velikost objektu v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá [GetEmbedSourceData](#getembedsourcedata) – členská funkce získat nativní data pro položky OLE a volání [AddOtherClipboardData](#addotherclipboarddata) – členská funkce získat formát prezentace a všechny Podporované formáty převod. Pokud `bIncludeLink` je **TRUE**, také voláním funkce [GetLinkSourceData](#getlinksourcedata) k získání dat odkaz pro položku.  
  
 Funkci přepsat, pokud chcete uvést do formátů `COleDataSource` objekt před nebo po tyto formáty poskytl `CopyToClipboard`.  
  
##  <a name="getdatasource"></a>COleServerItem::GetDataSource  
 Volání této funkce můžete získat [coledatasource –](../../mfc/reference/coledatasource-class.md) objekt použitý k uložení převod formátů, které podporuje serverové aplikace.  
  
```  
COleDataSource* GetDataSource();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `COleDataSource` objekt použitý k uložení převod formátů.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete, vaše serverová aplikace nabízet data v různých formátech při přenosu dat operace, zaregistrujte tyto formáty se `COleDataSource` objekt vrácený pomocí této funkce. Například, pokud chcete zadat **CF_TEXT** reprezentace položky OLE pro schránku nebo operací přetažení myší, by zaregistrovat formát s `COleDataSource` objekt funkce vrátí hodnotu a pak přepsání  **OnRenderXxxData** – členská funkce poskytovat data.  
  
##  <a name="getdocument"></a>COleServerItem::GetDocument  
 Volání této funkce získání ukazatele v dokumentu, který obsahuje položky.  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na dokument, který obsahuje položku; **NULL** Pokud položka není součástí dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 To umožňuje přístup k dokumentu serveru, který můžete předat jako argument k `COleServerItem` konstruktor.  
  
##  <a name="getembedsourcedata"></a>COleServerItem::GetEmbedSourceData  
 Volání této funkce můžete získat **CF_EMBEDSOURCE** dat položky OLE.  
  
```  
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parametry  
 `lpStgMedium`  
 Ukazatel [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktura, která bude přijímat **CF_EMBEDSOURCE** data pro položku OLE.  
  
### <a name="remarks"></a>Poznámky  
 Tento formát obsahuje nativní datové položky. Jste implementovali `Serialize` – členská funkce pro tuto funkci správně fungovat.  
  
 Výsledek lze přidat ke zdroji dat pomocí [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Tato funkce je volána automaticky [COleServerItem::OnGetClipboardData](#ongetclipboarddata).  
  
 Další informace najdete v tématu [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) ve Windows SDK.  
  
##  <a name="getitemname"></a>COleServerItem::GetItemName  
 Volání této funkce se získat název položky.  
  
```  
const CString& GetItemName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název položky.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se obvykle volat pouze pro propojené položky.  
  
##  <a name="getlinksourcedata"></a>COleServerItem::GetLinkSourceData  
 Volání této funkce můžete získat `CF_LINKSOURCE` dat položky OLE.  
  
```  
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parametry  
 `lpStgMedium`  
 Ukazatel [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktura, která bude přijímat `CF_LINKSOURCE` data pro položku OLE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tento formát obsahuje CLSID popisující typ položky OLE a informace potřebné k vyhledání dokument obsahující položky OLE.  
  
 Výsledek lze přidat ke zdroji dat s [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Tato funkce je volána automaticky [OnGetClipboardData](#ongetclipboarddata).  
  
 Další informace najdete v tématu [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) ve Windows SDK.  
  
##  <a name="getobjectdescriptordata"></a>COleServerItem::GetObjectDescriptorData  
 Volání této funkce můžete získat **CF_OBJECTDESCRIPTOR** dat položky OLE.  
  
```  
void GetObjectDescriptorData(
    LPPOINT lpOffset,  
    LPSIZE lpSize,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parametry  
 `lpOffset`  
 Posunutí myši klikněte na tlačítko z levého horního rohu položky OLE. Může být **NULL**.  
  
 `lpSize`  
 Velikost položky OLE. Může být **NULL**.  
  
 `lpStgMedium`  
 Ukazatel [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktura, která bude přijímat **CF_OBJECTDESCRIPTOR** data pro položku OLE.  
  
### <a name="remarks"></a>Poznámky  
 Informace se zkopírují **STGMEDIUM** struktura na kterou odkazuje `lpStgMedium`. Tento formát obsahuje informace potřebné pro dialogové okno Vložit jinak.  
  
 Další informace najdete v tématu [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) ve Windows SDK.  
  
##  <a name="isconnected"></a>COleServerItem::IsConnected  
 Volání této funkce, pokud je připojený položky OLE.  
  
```  
BOOL IsConnected() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je položka připojená; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Položky OLE považuje za připojení, pokud jeden nebo více kontejnerů odkazy na položky. Položku je připojený, pokud jeho referenční počet je větší než 0 nebo pokud je vložené položky.  
  
##  <a name="islinkeditem"></a>COleServerItem::IsLinkedItem  
 Volání této funkce, které chcete zobrazit, pokud je položka OLE propojené položky.  
  
```  
BOOL IsLinkedItem() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je položka propojené položky; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Položku souvisí, pokud položka je platný, nevrátí v dokumentu seznam vložených položek. Propojené položky může nebo nemusí být připojen do kontejneru.  
  
 Je běžné použití stejné třídy pro propojené a vložené položky. `IsLinkedItem`je možné provádět propojené položky chovat jinak než vložené položky, i když mnohokrát kód je běžné.  
  
##  <a name="m_sizeextent"></a>COleServerItem::m_sizeExtent  
 Tento člen informuje server, kolik objektu je zobrazen v kontejneru dokumentu.  
  
```  
CSize m_sizeExtent;  
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementaci [OnSetExtent](#onsetextent) nastaví tento člen.  
  
##  <a name="notifychanged"></a>COleServerItem::NotifyChanged  
 Po změně propojené položky volání této funkce.  
  
```  
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>Parametry  
 `nDrawAspect`  
 Hodnota z `DVASPECT` výčtu, která určuje, které aspekt položky OLE se změnila. Tento parametr může mít některý z následujících hodnot:  
  
- `DVASPECT_CONTENT`Položka je reprezentována tak, že lze zobrazit jako vložený objekt uvnitř jeho kontejneru.  
  
- `DVASPECT_THUMBNAIL`Položka je vykreslen v znázornění "miniaturu" tak, aby ji bylo možné zobrazit v nástroji procházení.  
  
- `DVASPECT_ICON`Položka je reprezentována ikonu.  
  
- `DVASPECT_DOCPRINT`Položka je reprezentována jako kdyby byly vytisknout, pomocí příkazu Tisk z nabídky soubor.  
  
### <a name="remarks"></a>Poznámky  
 Pokud položku kontejneru je propojený s automatické propojení dokumentu, položku aktualizovat tak, aby odrážely změny. V kontejneru aplikací vytvořených pomocí knihovny Microsoft Foundation Class [COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange) je volána v odpovědi.  
  
##  <a name="ondoverb"></a>COleServerItem::OnDoVerb  
 Voláno rámcem provést zadanou operaci.  
  
```  
virtual void OnDoVerb(LONG iVerb);
```  
  
### <a name="parameters"></a>Parametry  
 `iVerb`  
 Určuje příkaz provést. Může být některého z následujících akcí:  
  
|Hodnota|Význam|Symbol|  
|-----------|-------------|------------|  
|0|primární požadavek|`OLEIVERB_PRIMARY`|  
|1|Sekundární operace|(Žádný)|  
|- 1|Položka zobrazení pro úpravy|`OLEIVERB_SHOW`|  
|- 2|Upravit položku v samostatném okně.|`OLEIVERB_OPEN`|  
|- 3|Skrytí položek|`OLEIVERB_HIDE`|  
  
 Hodnota-1 je obvykle alias pro jiný příkaz. Pokud otevřete úpravy není podporován, -2 má stejný účinek jako hodnotu -1. Další hodnoty, najdete v části [Funkce IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace kontejneru vytvořené pomocí knihovny Microsoft Foundation Class, tato funkce je volána, když [COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate) – členská funkce k odpovídající položce `COleClientItem` objektu se říká. Výchozí implementace volá [viditelnost](#onshow) člen fungovat, pokud primární požadavek nebo `OLEIVERB_SHOW` není zadaný, [při otevření](#onopen) Pokud příkaz sekundární nebo `OLEIVERB_OPEN` je zadán a [Skrytí](#onhide) Pokud `OLEIVERB_HIDE` je zadán. Výchozí implementace volá `OnShow` Pokud `iVerb` není jedním z výše uvedených příkazů.  
  
 Funkci přepište, pokud primární požadavek nezobrazuje položka. Například pokud je položka záznam zvuku a jeho primární požadavek je Play, nebude máte zobrazíte serverová aplikace k přehrání položky.  
  
 Další informace najdete v tématu [Funkce IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) ve Windows SDK.  
  
##  <a name="ondraw"></a>COleServerItem::OnDraw  
 Voláno rámcem k vykreslení položky OLE do metasoubory.  
  
```  
virtual BOOL OnDraw(
    CDC* pDC,  
    CSize& rSize) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Ukazatel [CDC](../../mfc/reference/cdc-class.md) objekt, u kterého k vykreslení položky. Kontext zobrazení je automaticky připojená k kontext atribut zobrazení, bude možné volat funkce atribut, i když to proto by zkontrolujte metafile konkrétní zařízení.  
  
 `rSize`  
 Velikost v **HIMETRIC** jednotky, ve kterém k vykreslení metafile.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě, že položka byla úspěšně vykreslovány; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Reprezentace metafile položky OLE slouží k zobrazení položky v aplikaci kontejneru. Aplikace kontejneru vytvořené pomocí knihovny Microsoft Foundation Class, je používán metafile [kreslení](../../mfc/reference/coleclientitem-class.md#draw) – členská funkce k odpovídající položce [COleClientItem](../../mfc/reference/coleclientitem-class.md) objektu. Neexistuje žádný výchozí implementace. Je nutné přepsat tuto funkci k vykreslení položky do kontextu zařízení zadat.  
  
##  <a name="ondrawex"></a>COleServerItem::OnDrawEx  
 Voláno rámcem pro všechny kreslení.  
  
```  
virtual BOOL OnDrawEx(
    CDC* pDC,  
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Ukazatel [CDC](../../mfc/reference/cdc-class.md) objekt, u kterého k vykreslení položky. Řadič domény je automaticky připojená k atribut řadič domény, bude možné volat funkce atribut, i když to proto by zkontrolujte metafile konkrétní zařízení.  
  
 `nDrawAspect`  
 Hodnota z `DVASPECT` výčtu. Tento parametr může mít některý z následujících hodnot:  
  
- `DVASPECT_CONTENT`Položka je reprezentována tak, že lze zobrazit jako vložený objekt uvnitř jeho kontejneru.  
  
- `DVASPECT_THUMBNAIL`Položka je vykreslen v znázornění "miniaturu" tak, aby ji bylo možné zobrazit v nástroji procházení.  
  
- `DVASPECT_ICON`Položka je reprezentována ikonu.  
  
- `DVASPECT_DOCPRINT`Položka je reprezentována jako kdyby byly vytisknout, pomocí příkazu Tisk z nabídky soubor.  
  
 `rSize`  
 Velikost položky v **HIMETRIC** jednotky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě, že položka byla úspěšně vykreslovány; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace volá `OnDraw` při `DVASPECT` rovná `DVASPECT_CONTENT`; v opačném případě se nezdaří.  
  
 Přepsání této funkce zajistit prezentace dat pro aspekty jiné než `DVASPECT_CONTENT`, jako například `DVASPECT_ICON` nebo `DVASPECT_THUMBNAIL`.  
  
##  <a name="ongetclipboarddata"></a>COleServerItem::OnGetClipboardData  
 Voláno rámcem získat `COleDataSource` objekt obsahující všechna data, která by umístit do schránky voláním [CopyToClipboard](#copytoclipboard) – členská funkce.  
  
```  
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,  
    LPPOINT lpOffset,  
    LPSIZE lpSize);
```  
  
### <a name="parameters"></a>Parametry  
 `bIncludeLink`  
 Tuto možnost nastavíte na **TRUE** Pokud data propojení by se měl zkopírovat do schránky. Tuto možnost nastavíte na **FALSE** Pokud vaše serverová aplikace nepodporuje odkazy.  
  
 `lpOffset`  
 Posun myší z tohoto počátku objektu v pixelech.  
  
 `lpSize`  
 Velikost objektu v pixelech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [coledatasource –](../../mfc/reference/coledatasource-class.md) objekt obsahující data ze schránky.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce volá [GetClipboardData](#getclipboarddata).  
  
##  <a name="ongetextent"></a>COleServerItem::OnGetExtent  
 Voláno rámcem načíst velikostí, v **HIMETRIC** jednotky položky OLE.  
  
```  
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>Parametry  
 `nDrawAspect`  
 Určuje aspektů OLE položek, jejichž hranice jsou mají být načteny. Tento parametr může mít některý z následujících hodnot:  
  
- `DVASPECT_CONTENT`Položka je reprezentována tak, že lze zobrazit jako vložený objekt uvnitř jeho kontejneru.  
  
- `DVASPECT_THUMBNAIL`Položka je vykreslen v znázornění "miniaturu" tak, aby ji bylo možné zobrazit v nástroji procházení.  
  
- `DVASPECT_ICON`Položka je reprezentována ikonu.  
  
- `DVASPECT_DOCPRINT`Položka je reprezentována jako kdyby byly vytisknout, pomocí příkazu Tisk z nabídky soubor.  
  
 `rSize`  
 Odkaz na `CSize` objektu, která bude přijímat velikost položky OLE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace kontejneru vytvořené pomocí knihovny Microsoft Foundation Class, tato funkce je volána, když [GetExtent](../../mfc/reference/coleclientitem-class.md#getextent) – členská funkce k odpovídající položce `COleClientItem` objektu se říká. Výchozí implementace neprovede žádnou akci. Je nutné implementovat ho sami. Tato funkce přepsání, pokud chcete provést speciální zpracování při zpracování požadavku pro velikost položky OLE.  
  
##  <a name="onhide"></a>COleServerItem::OnHide  
 Voláno rámcem ke skrytí položek OLE.  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání výchozí **COleServerDoc::OnShowDocument (FALSE)**. Funkce taky upozorní kontejneru je skrytý položky OLE. Tato funkce přepsání, pokud chcete provést speciální zpracování při skrytí položky OLE.  
  
##  <a name="oninitfromdata"></a>COleServerItem::OnInitFromData  
 Voláno rámcem se inicializovat OLE položku pomocí obsah `pDataObject`.  
  
```  
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,  
    BOOL bCreation);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataObject`  
 Ukazatel na objekt OLE dat obsahující data v různých formátech pro inicializaci položky OLE.  
  
 `bCreation`  
 **Hodnota TRUE,** Pokud je tato funkce volána k chybě při inicializaci položku OLE se nově vytvořené aplikace kontejneru. **FALSE** Pokud je tato funkce volána nahradit obsah již existující položky OLE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `bCreation` je **TRUE**, tato funkce je volána, pokud kontejner implementuje vložit nový objekt v závislosti na aktuální výběr. Vybraná data se používá při vytváření nové položky OLE. Například když vyberete oblast buněk v tabulkovém programu a potom použít vložit nový objekt k vytvoření grafu na základě hodnot ve vybrané oblasti. Výchozí implementace neprovede žádnou akci. Přepsání této funkci můžete zvolit přijatelný formát od těch, které nabízí `pDataObject` a inicializace OLE položky na základě dat poskytuje. Toto je rozšířené přepisovatelné.  
  
 Další informace najdete v tématu [IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) ve Windows SDK.  
  
##  <a name="onopen"></a>COleServerItem::OnOpen  
 Voláno rámcem zobrazíte položky OLE v samostatné instanci serverové aplikace, a nikoli na místě.  
  
```  
virtual void OnOpen();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace aktivuje prvním okně s rámečkem zobrazení dokumentu, který obsahuje položky OLE; Pokud aplikace mini serveru, výchozí implementace znázorňuje hlavní okno. Funkce taky upozorní kontejneru se otevřelo položky OLE.  
  
 Tato funkce přepsání, pokud chcete provést speciální zpracování při otevírání položky OLE. To je obzvláště běžné s propojené položky, kde chcete nastavit výběr na odkaz, když je otevřen.  
  
 Další informace najdete v tématu [IOleClientSite::OnShowWindow](http://msdn.microsoft.com/library/windows/desktop/ms688658) ve Windows SDK.  
  
##  <a name="onqueryupdateitems"></a>COleServerItem::OnQueryUpdateItems  
 Voláno rámcem k určení, zda všechny propojené položky v aktuálním dokumentu serveru jsou zastaralé.  
  
```  
virtual BOOL OnQueryUpdateItems();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, jestli má dokument položky, které vyžadují aktualizace; 0, pokud jsou všechny položky aktuální.  
  
### <a name="remarks"></a>Poznámky  
 Položka je zastaralý, pokud byl změněn jeho zdrojový dokument, ale propojená položka nebyla aktualizována, aby odpovídalo změnám v dokumentu.  
  
##  <a name="onrenderdata"></a>COleServerItem::OnRenderData  
 Voláno rámcem k načtení dat v zadaném formátu.  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura určující formát, ve které je požadované informace.  
  
 `lpStgMedium`  
 Odkazuje na [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktury, ve kterém má být vrácen data.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Zadaný formát je jeden dříve umístili ve `COleDataSource` pomocí [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) nebo [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) – členská funkce pro zpožděné vykreslování. Výchozí implementace této funkce volá [OnRenderFileData](#onrenderfiledata) nebo [OnRenderGlobalData](#onrenderglobaldata), pokud zadaný úložné médium je soubor nebo paměti. Jestliže je zadán ani jeden z těchto formátů, výchozí implementace vrátí hodnotu 0 a neprovede žádnou akci.  
  
 Pokud `lpStgMedium` ->  *objekt tymed* je **TYMED_NULL**, **STGMEDIUM** by měla přidělená a vyplněna podle specifikace *lpFormatEtc -> objekt tymed*. Není-li **TYMED_NULL**, **STGMEDIUM** je nutné zadat místní s daty.  
  
 Toto je rozšířené přepisovatelné. Funkci poskytnout vaše data v požadovaný formát a střední přepište. V závislosti na vaše data můžete místo toho jeden z jiné verze této funkce přepsání. Pokud vaše data jsou malé a pevnou velikost, mají přednost před `OnRenderGlobalData`. Pokud vaše data jsou v souboru nebo s proměnnou velikostí, mají přednost před `OnRenderFileData`.  
  
 Další informace najdete v tématu [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431), [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812), [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177), a [objekt TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) ve Windows SDK.  
  
##  <a name="onrenderfiledata"></a>COleServerItem::OnRenderFileData  
 Voláno rámcem k načtení dat v zadaném formátu, když úložné médium je soubor.  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura určující formát, ve které je požadované informace.  
  
 `pFile`  
 Odkazuje na `CFile` objektu, ve kterém má být vykreslen data.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Zadaný formát je jeden dříve umístili ve `COleDataSource` pomocí [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) – členská funkce pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrací **FALSE**.  
  
 Toto je rozšířené přepisovatelné. Funkci poskytnout vaše data v požadovaný formát a střední přepište. V závislosti na vaše data můžete místo toho jeden z jiné verze této funkce přepsání. Pokud chcete zpracovat více úložných médií, mají přednost před [OnRenderData](#onrenderdata). Pokud vaše data jsou v souboru nebo s proměnnou velikostí, mají přednost před [OnRenderFileData](#onrenderfiledata).  
  
 Další informace najdete v tématu [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
##  <a name="onrenderglobaldata"></a>COleServerItem::OnRenderGlobalData  
 Voláno rámcem k načtení dat v zadaném formátu, když střední zadané úložiště je globální paměť.  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura určující formát, ve které je požadované informace.  
  
 `phGlobal`  
 Odkazuje na popisovač pro globální paměť, ve kterém má být vrácen data. Pokud byl přidělen není dostatek paměti, tento parametr může být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Zadaný formát je jeden dříve umístili ve `COleDataSource` pomocí [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) – členská funkce pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrací **FALSE**.  
  
 Pokud `phGlobal` je **NULL**, pak nový `HGLOBAL` by měl být přidělené a vrácených v `phGlobal`. V opačném `HGLOBAL` specifikováno na základě `phGlobal` by mělo být zadáno s daty. Množství dat umístěny `HGLOBAL` nesmí být delší než aktuální velikost bloku paměti. Navíc bloku nelze znovu přidělit, větší velikost.  
  
 Toto je rozšířené přepisovatelné. Funkci poskytnout vaše data v požadovaný formát a střední přepište. V závislosti na vaše data můžete místo toho jeden z jiné verze této funkce přepsání. Pokud chcete zpracovat více úložných médií, mají přednost před [OnRenderData](#onrenderdata). Pokud vaše data jsou v souboru nebo s proměnnou velikostí, mají přednost před [OnRenderFileData](#onrenderfiledata).  
  
 Další informace najdete v tématu [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
##  <a name="onsetcolorscheme"></a>COleServerItem::OnSetColorScheme  
 Voláno rámcem k určení paletu barev, který se má použít při úpravě položky OLE.  
  
```  
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```  
  
### <a name="parameters"></a>Parametry  
 `lpLogPalette`  
 Ukazatel na Windows [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se používá paletu barev; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace kontejneru vytvořené, pomocí knihovny Microsoft Foundation Class, tato funkce je volána, když [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) funkce k odpovídající položce `COleClientItem` objektu se říká. Výchozí implementace vrací **FALSE**. Tato funkce přepsání, pokud chcete použít doporučené palety. Aplikace serveru není potřeba použít navrhované paletu.  
  
 Další informace najdete v tématu [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) ve Windows SDK.  
  
##  <a name="onsetdata"></a>COleServerItem::OnSetData  
 Voláno rámcem nahradit dat OLE položky se zadanými daty.  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Ukazatel na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura určující formát data.  
  
 `lpStgMedium`  
 Ukazatel na [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktury, ve kterém se nachází data.  
  
 `bRelease`  
 Určuje, kdo je vlastníkem úložiště střední po dokončení volání funkce. Volající rozhodne, který je zodpovědný za uvolnění prostředky přidělené jménem paměťového média. Volající dosahuje tím, že nastavení `bRelease`. Pokud `bRelease` je nenulové hodnoty, položku serveru trvá vlastnictví, uvolnění médium, až se dokončí, jeho použití. Když `bRelease` je 0, volající uchovává vlastnictví a položku serveru můžete použít úložiště střední pouze po dobu trvání volání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Položka serveru nevyžaduje vlastnictví dat, dokud ho má byly úspěšně načteny. To znamená, že se nevyžaduje vlastnictví Pokud vrátí hodnotu 0. Pokud zdroj dat používá vlastnictví, uvolní úložné médium voláním [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) funkce.  
  
 Výchozí implementace neprovede žádnou akci. Přepsání této funkci můžete nahradit dat OLE položky se zadanými daty. Toto je rozšířené přepisovatelné.  
  
 Další informace najdete v tématu [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812), [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177), a [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) ve Windows SDK.  
  
##  <a name="onsetextent"></a>COleServerItem::OnSetExtent  
 Voláno rámcem říct OLE položek, kolik místa je možné v kontejneru dokumentu.  
  
```  
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,  
    const CSize& size);
```  
  
### <a name="parameters"></a>Parametry  
 `nDrawAspect`  
 Určuje aspektů OLE položek, jejichž hranice jsou specifikované. Tento parametr může mít některý z následujících hodnot:  
  
- `DVASPECT_CONTENT`Položka je reprezentována tak, že lze zobrazit jako vložený objekt uvnitř jeho kontejneru.  
  
- `DVASPECT_THUMBNAIL`Položka je vykreslen v znázornění "miniaturu" tak, aby ji bylo možné zobrazit v nástroji procházení.  
  
- `DVASPECT_ICON`Položka je reprezentována ikonu.  
  
- `DVASPECT_DOCPRINT`Položka je reprezentována jako kdyby byly vytisknout, pomocí příkazu Tisk z nabídky soubor.  
  
 `size`  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) struktura určení nové velikosti položky OLE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace kontejneru vytvořené pomocí knihovny Microsoft Foundation Class, tato funkce je volána, když [SetExtent](../../mfc/reference/coleclientitem-class.md#setextent) – členská funkce k odpovídající položce `COleClientItem` objektu se říká. Výchozí implementace sady [m_sizeExtent](#m_sizeextent) člen zadané velikosti Pokud `nDrawAspect` je `DVASPECT_CONTENT`; jinak vrátí hodnotu 0. Funkci provést zvláštní zpracování, když změníte velikost položky přepište.  
  
##  <a name="onshow"></a>COleServerItem::OnShow  
 Voláno rámcem dáte pokyn, aby serverová aplikace zobrazíte položky OLE na místě.  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána obvykle, když uživatel aplikace kontejneru vytvoří položku nebo provede operaci, jako jsou úpravy, které vyžaduje položku, která se má zobrazit. Výchozí implementace pokusí aktivace na místě. Pokud tato možnost selže, volání funkce `OnOpen` – členská funkce zobrazíte položky OLE v samostatném okně.  
  
 Tato funkce přepsání, pokud chcete provést zvláštní zpracování, pokud se zobrazí položka OLE.  
  
##  <a name="onupdate"></a>COleServerItem::OnUpdate  
 Voláno rámcem, pokud položka byla změněna.  
  
```  
virtual void OnUpdate(
    COleServerItem* pSender,  
    LPARAM lHint,  
    CObject* pHint,  
    DVASPECT nDrawAspect);
```  
  
### <a name="parameters"></a>Parametry  
 `pSender`  
 Ukazatel na položku upravit dokumentu. Může být **NULL**.  
  
 `lHint`  
 Obsahuje informace o této úpravy.  
  
 `pHint`  
 Ukazatel na objekt ukládání informací o úpravy.  
  
 `nDrawAspect`  
 Hodnota z `DVASPECT` výčtu. Tento parametr může mít jednu z následujících hodnot:  
  
- `DVASPECT_CONTENT`Položka je reprezentována tak, že lze zobrazit jako vložený objekt uvnitř jeho kontejneru.  
  
- `DVASPECT_THUMBNAIL`Položka je vykreslen v znázornění "miniaturu" tak, aby ji bylo možné zobrazit v nástroji procházení.  
  
- `DVASPECT_ICON`Položka je reprezentována ikonu.  
  
- `DVASPECT_DOCPRINT`Položka je reprezentována jako kdyby byly vytisknout, pomocí příkazu Tisk z nabídky soubor.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace volá [NotifyChanged](#notifychanged)bez ohledu na nápovědu a odesílatele.  
  
##  <a name="onupdateitems"></a>COleServerItem::OnUpdateItems  
 Voláno rámcem aktualizovat všechny položky v dokumentu na serveru.  
  
```  
virtual void OnUpdateItems();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace volá [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) pro všechny `COleClientItem` objekty v dokumentu.  
  
##  <a name="setitemname"></a>COleServerItem::SetItemName  
 Když vytvoříte propojené položky k nastavení jeho název, volání této funkce.  
  
```  
void SetItemName(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszItemName`  
 Ukazatel na nový název položky.  
  
### <a name="remarks"></a>Poznámky  
 Název musí být jedinečný v rámci dokumentu. Když serverová aplikace se nazývá upravit propojené položky, aplikace tento název používá k nalezení položky. Není nutné pro volání této funkce pro vložené položky.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC HIERSVR](../../visual-cpp-samples.md)   
 [CDocItem – třída](../../mfc/reference/cdocitem-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)   
 [COleServerDoc – třída](../../mfc/reference/coleserverdoc-class.md)   
 [COleTemplateServer – třída](../../mfc/reference/coletemplateserver-class.md)
