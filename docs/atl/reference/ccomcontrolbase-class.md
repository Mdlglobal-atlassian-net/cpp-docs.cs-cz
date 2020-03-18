---
title: CComControlBase – třída
ms.date: 11/04/2016
f1_keywords:
- CComControlBase
- ATLCTL/ATL::CComControlBase
- ATLCTL/ATL::CComControlBase::AppearanceType
- ATLCTL/ATL::CComControlBase::CComControlBase
- ATLCTL/ATL::CComControlBase::ControlQueryInterface
- ATLCTL/ATL::CComControlBase::DoesVerbActivate
- ATLCTL/ATL::CComControlBase::DoesVerbUIActivate
- ATLCTL/ATL::CComControlBase::DoVerbProperties
- ATLCTL/ATL::CComControlBase::FireViewChange
- ATLCTL/ATL::CComControlBase::GetAmbientAppearance
- ATLCTL/ATL::CComControlBase::GetAmbientAutoClip
- ATLCTL/ATL::CComControlBase::GetAmbientBackColor
- ATLCTL/ATL::CComControlBase::GetAmbientCharSet
- ATLCTL/ATL::CComControlBase::GetAmbientCodePage
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayAsDefault
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayName
- ATLCTL/ATL::CComControlBase::GetAmbientFont
- ATLCTL/ATL::CComControlBase::GetAmbientFontDisp
- ATLCTL/ATL::CComControlBase::GetAmbientForeColor
- ATLCTL/ATL::CComControlBase::GetAmbientLocaleID
- ATLCTL/ATL::CComControlBase::GetAmbientMessageReflect
- ATLCTL/ATL::CComControlBase::GetAmbientPalette
- ATLCTL/ATL::CComControlBase::GetAmbientProperty
- ATLCTL/ATL::CComControlBase::GetAmbientRightToLeft
- ATLCTL/ATL::CComControlBase::GetAmbientScaleUnits
- ATLCTL/ATL::CComControlBase::GetAmbientShowGrabHandles
- ATLCTL/ATL::CComControlBase::GetAmbientShowHatching
- ATLCTL/ATL::CComControlBase::GetAmbientSupportsMnemonics
- ATLCTL/ATL::CComControlBase::GetAmbientTextAlign
- ATLCTL/ATL::CComControlBase::GetAmbientTopToBottom
- ATLCTL/ATL::CComControlBase::GetAmbientUIDead
- ATLCTL/ATL::CComControlBase::GetAmbientUserMode
- ATLCTL/ATL::CComControlBase::GetDirty
- ATLCTL/ATL::CComControlBase::GetZoomInfo
- ATLCTL/ATL::CComControlBase::InPlaceActivate
- ATLCTL/ATL::CComControlBase::InternalGetSite
- ATLCTL/ATL::CComControlBase::OnDraw
- ATLCTL/ATL::CComControlBase::OnDrawAdvanced
- ATLCTL/ATL::CComControlBase::OnKillFocus
- ATLCTL/ATL::CComControlBase::OnMouseActivate
- ATLCTL/ATL::CComControlBase::OnPaint
- ATLCTL/ATL::CComControlBase::OnSetFocus
- ATLCTL/ATL::CComControlBase::PreTranslateAccelerator
- ATLCTL/ATL::CComControlBase::SendOnClose
- ATLCTL/ATL::CComControlBase::SendOnDataChange
- ATLCTL/ATL::CComControlBase::SendOnRename
- ATLCTL/ATL::CComControlBase::SendOnSave
- ATLCTL/ATL::CComControlBase::SendOnViewChange
- ATLCTL/ATL::CComControlBase::SetControlFocus
- ATLCTL/ATL::CComControlBase::SetDirty
- ATLCTL/ATL::CComControlBase::m_bAutoSize
- ATLCTL/ATL::CComControlBase::m_bDrawFromNatural
- ATLCTL/ATL::CComControlBase::m_bDrawGetDataInHimetric
- ATLCTL/ATL::CComControlBase::m_bInPlaceActive
- ATLCTL/ATL::CComControlBase::m_bInPlaceSiteEx
- ATLCTL/ATL::CComControlBase::m_bNegotiatedWnd
- ATLCTL/ATL::CComControlBase::m_bRecomposeOnResize
- ATLCTL/ATL::CComControlBase::m_bRequiresSave
- ATLCTL/ATL::CComControlBase::m_bResizeNatural
- ATLCTL/ATL::CComControlBase::m_bUIActive
- ATLCTL/ATL::CComControlBase::m_bUsingWindowRgn
- ATLCTL/ATL::CComControlBase::m_bWasOnceWindowless
- ATLCTL/ATL::CComControlBase::m_bWindowOnly
- ATLCTL/ATL::CComControlBase::m_bWndLess
- ATLCTL/ATL::CComControlBase::m_hWndCD
- ATLCTL/ATL::CComControlBase::m_nFreezeEvents
- ATLCTL/ATL::CComControlBase::m_rcPos
- ATLCTL/ATL::CComControlBase::m_sizeExtent
- ATLCTL/ATL::CComControlBase::m_sizeNatural
- ATLCTL/ATL::CComControlBase::m_spAdviseSink
- ATLCTL/ATL::CComControlBase::m_spAmbientDispatch
- ATLCTL/ATL::CComControlBase::m_spClientSite
- ATLCTL/ATL::CComControlBase::m_spDataAdviseHolder
- ATLCTL/ATL::CComControlBase::m_spInPlaceSite
- ATLCTL/ATL::CComControlBase::m_spOleAdviseHolder
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
ms.openlocfilehash: 36afd716009848ccd2e2f0ab966f66f573acdfd8
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417892"
---
# <a name="ccomcontrolbase-class"></a>CComControlBase – třída

Tato třída poskytuje metody pro vytváření a správu ovládacích prvků ATL.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|Přepište, pokud vaše `m_nAppearance` burzovní vlastnost není typu **short**.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|Konstruktor|
|[CComControlBase:: ~ CComControlBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComControlBase::D oesVerbActivate](#doesverbactivate)|Kontroluje, že parametr *iVerb* používaný `IOleObjectImpl::DoVerb` buď aktivuje uživatelské rozhraní ovládacího prvku (*iVerb* Equals OLEIVERB_UIACTIVATE), definuje akci provedenou v případě, že uživatel dvakrát klikne na ovládací prvek (*iVerb* Equals OLEIVERB_PRIMARY), zobrazí ovládací prvek (*iVerb* Equals OLEIVERB_SHOW) nebo aktivuje ovládací prvek (*iVerb* Equals OLEIVERB_INPLACEACTIVATE).|
|[CComControlBase::D oesVerbUIActivate](#doesverbuiactivate)|Kontroluje, zda parametr *iVerb* používaný `IOleObjectImpl::DoVerb` způsobí, že uživatelské rozhraní ovládacího prvku bude aktivováno a vrátí hodnotu true.|
|[CComControlBase::D oVerbProperties](#doverbproperties)|Zobrazí stránky vlastností ovládacího prvku.|
|[CComControlBase::FireViewChange](#fireviewchange)|Zavolejte tuto metodu pro sdělení kontejneru pro překreslení ovládacího prvku nebo upozornění na zaregistrované jímky oznámení, že se změnilo zobrazení ovládacího prvku.|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|Načte DISPID_AMBIENT_APPEARANCE aktuální nastavení vzhledu pro ovládací prvek: 0 pro plochý a 1 pro 3D.|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Načítá DISPID_AMBIENT_AUTOCLIP, příznak označující, zda kontejner podporuje automatické oříznutí oblasti zobrazení ovládacího prvku.|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Načte DISPID_AMBIENT_BACKCOLOR, okolní barvu pozadí pro všechny ovládací prvky definované kontejnerem.|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Načítá DISPID_AMBIENT_CHARSET, okolní znaková sada pro všechny ovládací prvky, které jsou definovány kontejnerem.|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Načítá DISPID_AMBIENT_CODEPAGE, okolní znaková sada pro všechny ovládací prvky, které jsou definovány kontejnerem.|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Načítá DISPID_AMBIENT_DISPLAYASDEFAULT, příznak, který má hodnotu TRUE, pokud kontejner označil ovládací prvek v tomto webu jako výchozí tlačítko, a proto by se měl ovládací prvek tlačítko vykreslovat pomocí silného rámce.|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Načte DISPID_AMBIENT_DISPLAYNAME název kontejneru dodaný do ovládacího prvku.|
|[CComControlBase::GetAmbientFont](#getambientfont)|Načte ukazatel na okolní `IFont` rozhraní kontejneru.|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Načte ukazatel na rozhraní pro expedici `IFontDisp` v kontejneru.|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Načítá DISPID_AMBIENT_FORECOLOR, okolní barvu popředí pro všechny ovládací prvky definované kontejnerem.|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Načte DISPID_AMBIENT_LOCALEID identifikátor jazyka používaného kontejnerem.|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Načte DISPID_AMBIENT_MESSAGEREFLECT příznak označující, zda má kontejner přijímat zprávy okna (například WM_DRAWITEM) jako události.|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Načte DISPID_AMBIENT_PALETTE, který se používá pro přístup k HPALETTE kontejneru.|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Načte vlastnost kontejneru určenou *identifikátorem*.|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|Načte DISPID_AMBIENT_RIGHTTOLEFT, směr, ve kterém se obsah zobrazuje v kontejneru.|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Načte DISPID_AMBIENT_SCALEUNITS, okolní jednotky kontejneru (například palce nebo centimetry) pro zobrazení popisků.|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Načítá DISPID_AMBIENT_SHOWGRABHANDLES, příznak označující, zda kontejner umožňuje ovládacímu prvku zobrazit obslužné rutiny pro sebe sama, když je aktivní.|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Načítá DISPID_AMBIENT_SHOWHATCHING, příznak označující, zda kontejner umožňuje ovládacímu prvku, aby se zobrazil s šrafovaného vzoru, pokud je uživatelské rozhraní aktivní.|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Načte DISPID_AMBIENT_SUPPORTSMNEMONICS příznak označující, zda kontejner podporuje klávesové zkratky.|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Načítá DISPID_AMBIENT_TEXTALIGN, zarovnání textu preferované kontejnerem: 0 pro Obecné zarovnání (číslice doprava, text vlevo), 1 pro zarovnání vlevo, 2 pro zarovnání na střed a 3 pro zarovnání vpravo.|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Načte DISPID_AMBIENT_TOPTOBOTTOM, směr, ve kterém se obsah zobrazuje v kontejneru.|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|Načte DISPID_AMBIENT_UIDEAD příznak označující, zda kontejner chce ovládací prvek reagovat na akce uživatelského rozhraní.|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Načte DISPID_AMBIENT_USERMODE příznak označující, zda je kontejner v režimu běhu (TRUE) nebo v režimu návrhu (FALSE).|
|[CComControlBase:: getdirty](#getdirty)|Vrátí hodnotu datového členu `m_bRequiresSave`.|
|[CComControlBase::GetZoomInfo](#getzoominfo)|Načte hodnoty x a y čitateli a jmenovatele faktoru přiblížení pro ovládací prvek aktivovaný pro místní úpravy.|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|Způsobí přechod ovládacího prvku z neaktivního stavu do libovolného stavu, který příkaz v *iVerb* označuje.|
|[CComControlBase::InternalGetSite](#internalgetsite)|Zavolejte tuto metodu pro dotazování webu ovládacího prvku pro ukazatel na identifikované rozhraní.|
|[CComControlBase:: Draw](#ondraw)|Tuto metodu přepište, pokud chcete ovládací prvek nakreslit.|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|Výchozí `OnDrawAdvanced` připraví normalizovaný kontext zařízení pro kreslení a pak volá metodu `OnDraw` vaší třídy ovládacího prvku.|
|[CComControlBase::OnKillFocus](#onkillfocus)|Kontroluje, zda je ovládací prvek na místě aktivní a má platnou řídicí lokalitu, a poté informuje o kontejneru, že ovládací prvek ztratil fokus.|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Kontroluje, zda je uživatelské rozhraní v uživatelském režimu, a poté aktivuje ovládací prvek.|
|[CComControlBase:: propaintt](#onpaint)|Připraví kontejner pro vybarvení, získá klientskou oblast ovládacího prvku a pak zavolá metodu `OnDraw` třídy ovládacího prvku.|
|[CComControlBase:: OnSetFocus](#onsetfocus)|Kontroluje, zda je ovládací prvek na místě aktivní a má platnou řídicí lokalitu, a poté informuje o kontejneru, který ovládací prvek získal fokus.|
|[CComControlBase::P reTranslateAccelerator](#pretranslateaccelerator)|Tuto metodu přepište, pokud chcete poskytnout vlastní obslužné rutiny pro klávesové zkratky.|
|[CComControlBase::SendOnClose](#sendonclose)|Upozorní všechny informační jímky zaregistrované u držitele poradenství, že byl ovládací prvek uzavřen.|
|[CComControlBase::SendOnDataChange](#sendondatachange)|Upozorní všechny informační jímky zaregistrované u držitele poradenství, že se data ovládacího prvku změnila.|
|[CComControlBase::SendOnRename](#sendonrename)|Upozorní všechny informační jímky zaregistrované u držitele poradenství, že má ovládací prvek nový moniker.|
|[CComControlBase::SendOnSave](#sendonsave)|Upozorní všechny informační jímky zaregistrované u držitele poradenství, že byl ovládací prvek uložen.|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Upozorní všechny zaregistrované poradenské jímky, že se změnilo zobrazení ovládacího prvku.|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Nastaví nebo odebere fokus klávesnice na nebo z ovládacího prvku.|
|[CComControlBase::SetDirty](#setdirty)|Nastaví datový člen `m_bRequiresSave` na hodnotu v *bDirty*.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComControlBase:: m_bAutoSize](#m_bautosize)|Příznak označující, že ovládací prvek nemůže být jinou velikostí|
|[CComControlBase:: m_bDrawFromNatural](#m_bdrawfromnatural)|Příznak označující, že `IDataObjectImpl::GetData` a `CComControlBase::GetZoomInfo` by měl nastavit velikost ovládacího prvku z `m_sizeNatural` namísto `m_sizeExtent`.|
|[CComControlBase:: m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Příznak označující, že při kreslení má `IDataObjectImpl::GetData` použít jednotky HIMETRIC a ne pixely|
|[CComControlBase:: m_bInPlaceActive](#m_binplaceactive)|Příznak označující, že ovládací prvek je na místě aktivní|
|[CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex)|Příznak označující, že kontejner podporuje rozhraní `IOleInPlaceSiteEx` a funkce ovládacího prvku OCX96, například ovládací prvky bez oken a blikání.|
|[CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd)|Příznak označující, zda se ovládací prvek vyjednal s kontejnerem o podpoře funkcí ovládacího prvku OCX96 (například ovládací prvky bez blikání a ovládacích prvků bez oken) a zda je ovládací prvek v okně nebo bez okna.|
|[CComControlBase:: m_bRecomposeOnResize](#m_brecomposeonresize)|Příznak označující, že ovládací prvek chce znovu vytvořit svou prezentaci, když kontejner změní velikost zobrazení ovládacího prvku|
|[CComControlBase:: m_bRequiresSave](#m_brequiressave)|Příznak označující, že se ovládací prvek od posledního uložení změnil|
|[CComControlBase:: m_bResizeNatural](#m_bresizenatural)|Příznak označující, že ovládací prvek chce změnit velikost přirozeného rozsahu (jeho neškálovaná fyzická velikost), když kontejner změní velikost zobrazení ovládacího prvku|
|[CComControlBase:: m_bUIActive](#m_buiactive)|Příznak označující, že uživatelské rozhraní ovládacího prvku, například nabídky a panely nástrojů, je aktivní.|
|[CComControlBase:: m_bUsingWindowRgn](#m_busingwindowrgn)|Příznak označující, že ovládací prvek používá oblast okna poskytnutou kontejnerem.|
|[CComControlBase:: m_bWasOnceWindowless](#m_bwasoncewindowless)|Příznak označující, že ovládací prvek byl bez okna, ale může nebo nemusí být nyní bez okna.|
|[CComControlBase:: m_bWindowOnly](#m_bwindowonly)|Příznak označující, že má být ovládací prvek nastaven na okno, i v případě, že kontejner podporuje ovládací prvky bez oken.|
|[CComControlBase:: m_bWndLess](#m_bwndless)|Příznak označující, že ovládací prvek je bez okna.|
|[CComControlBase:: m_hWndCD](#m_hwndcd)|Obsahuje odkaz na popisovač okna přidružený k ovládacímu prvku.|
|[CComControlBase:: m_nFreezeEvents](#m_nfreezeevents)|Počet, kolikrát kontejner obsahuje zmrazené události (odmítl přijímat události) bez ovlivnění odmrazení událostí (přijetí událostí).|
|[CComControlBase:: m_rcPos](#m_rcpos)|Pozice v pixelech ovládacího prvku vyjádřená v souřadnicích kontejneru.|
|[CComControlBase:: m_sizeExtent](#m_sizeextent)|Rozsah ovládacího prvku v jednotkách HIMETRIC (každá jednotka je 0,01 milimetrů) pro konkrétní displej.|
|[CComControlBase:: m_sizeNatural](#m_sizenatural)|Fyzická velikost ovládacího prvku v jednotkách HIMETRIC (každá jednotka je 0,01 milimetrů).|
|[CComControlBase:: m_spAdviseSink](#m_spadvisesink)|Přímý ukazatel na poradní připojení na kontejneru ( [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)kontejneru).|
|[CComControlBase:: m_spAmbientDispatch](#m_spambientdispatch)|Objekt `CComDispatchDriver`, který umožňuje načíst a nastavit vlastnosti kontejneru pomocí ukazatele `IDispatch`.|
|[CComControlBase:: m_spClientSite](#m_spclientsite)|Ukazatel na klientský web ovládacího prvku v rámci kontejneru.|
|[CComControlBase:: m_spDataAdviseHolder](#m_spdataadviseholder)|Poskytuje standardní způsob, jak uchovávat poradenská připojení mezi datovými objekty a příjímkami pro poradenství.|
|[CComControlBase:: m_spInPlaceSite](#m_spinplacesite)|Ukazatel na ukazatel rozhraní [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)nebo [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) kontejneru.|
|[CComControlBase:: m_spOleAdviseHolder](#m_spoleadviseholder)|Poskytuje standardní implementaci způsobu uchovávání poradenských připojení.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro vytváření a správu ovládacích prvků ATL. [Třída CComControl](../../atl/reference/ccomcontrol-class.md) je odvozena od `CComControlBase`. Při vytváření standardního ovládacího prvku nebo ovládacího prvku DHTML pomocí Průvodce ovládacím prvkem ATL bude průvodce automaticky odvozovat třídu z `CComControlBase`.

Další informace o vytvoření ovládacího prvku naleznete v [kurzu ATL](../../atl/active-template-library-atl-tutorial.md). Další informace o Průvodci projektem ATL naleznete v článku [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="appearancetype"></a>CComControlBase::AppearanceType

Přepište, pokud vaše `m_nAppearance` burzovní vlastnost není typu **short**.

```
typedef short AppearanceType;
```

### <a name="remarks"></a>Poznámky

Průvodce ovládacím prvkem ATL přidává `m_nAppearance`ovou vlastnost typu short. Přepsat `AppearanceType`, pokud používáte jiný datový typ.

##  <a name="ccomcontrolbase"></a>CComControlBase::CComControlBase

Konstruktor

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>Parametry

*y*<br/>
Popisovač okna přidruženého k ovládacímu prvku

### <a name="remarks"></a>Poznámky

Inicializuje velikost ovládacího prvku na 5080X5080 jednotky HIMETRIC (2 "X2") a inicializuje hodnoty datových členů `CComControlBase` na hodnotu NULL nebo FALSE.

##  <a name="dtor"></a>CComControlBase:: ~ CComControlBase

Destruktor.

```
~CComControlBase();
```

### <a name="remarks"></a>Poznámky

Pokud je ovládací prvek v okně, `~CComControlBase` jej zničí voláním [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow).

##  <a name="controlqueryinterface"></a>CComControlBase::ControlQueryInterface

Načte ukazatel na požadované rozhraní.

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>Parametry

*identifikátor*<br/>
Identifikátor GUID požadovaného rozhraní

*ppv*<br/>
Ukazatel na ukazatel rozhraní identifikovaný *identifikátorem IID*nebo hodnotu null, pokud rozhraní nebylo nalezeno.

### <a name="remarks"></a>Poznámky

Zpracovává pouze rozhraní v tabulce map modelu COM.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

##  <a name="doesverbactivate"></a>CComControlBase::D oesVerbActivate

Kontroluje, že parametr *iVerb* používaný `IOleObjectImpl::DoVerb` buď aktivuje uživatelské rozhraní ovládacího prvku (*iVerb* Equals OLEIVERB_UIACTIVATE), definuje akci provedenou v případě, že uživatel dvakrát klikne na ovládací prvek (*iVerb* Equals OLEIVERB_PRIMARY), zobrazí ovládací prvek (*iVerb* Equals OLEIVERB_SHOW) nebo aktivuje ovládací prvek (*iVerb* Equals OLEIVERB_INPLACEACTIVATE).

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Hodnota určující akci, kterou má provést `DoVerb`.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud se *iVerb* rovná OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW nebo OLEIVERB_INPLACEACTIVATE; v opačném případě vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete přepsat pro definování vlastní aktivační operace.

##  <a name="doesverbuiactivate"></a>CComControlBase::D oesVerbUIActivate

Kontroluje, zda parametr *iVerb* používaný `IOleObjectImpl::DoVerb` způsobí, že uživatelské rozhraní ovládacího prvku bude aktivováno a vrátí hodnotu true.

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Hodnota určující akci, kterou má provést `DoVerb`.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud se *iVerb* rovná OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW nebo OLEIVERB_INPLACEACTIVATE. V opačném případě metoda vrátí hodnotu FALSE.

##  <a name="doverbproperties"></a>CComControlBase::D oVerbProperties

Zobrazí stránky vlastností ovládacího prvku.

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
Rezervovaný.

*hwndParent*<br/>
Popisovač okna obsahujícího ovládací prvek

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

##  <a name="fireviewchange"></a>CComControlBase::FireViewChange

Zavolejte tuto metodu pro sdělení kontejneru pro překreslení ovládacího prvku nebo upozornění na zaregistrované jímky oznámení, že se změnilo zobrazení ovládacího prvku.

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Je-li ovládací prvek aktivní (datový člen třídy ovládacího prvku [CComControlBase:: m_bInPlaceActive](#m_binplaceactive) má hodnotu true), upozorní kontejner, který chcete překreslit do celého ovládacího prvku. Pokud je ovládací prvek neaktivní, upozorní na zaregistrované kontrolní jímky v rámci ovládacího prvku (prostřednictvím datového členu třídy ovládacího prvku [CComControlBase:: m_spAdviseSink](#m_spadvisesink)), který změnil zobrazení ovládacího prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

##  <a name="getambientappearance"></a>CComControlBase::GetAmbientAppearance

Načte DISPID_AMBIENT_APPEARANCE aktuální nastavení vzhledu pro ovládací prvek: 0 pro plochý a 1 pro 3D.

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>Parametry

*nAppearance*<br/>
Vlastnost DISPID_AMBIENT_APPEARANCE.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

##  <a name="getambientautoclip"></a>CComControlBase::GetAmbientAutoClip

Načítá DISPID_AMBIENT_AUTOCLIP, příznak označující, zda kontejner podporuje automatické oříznutí oblasti zobrazení ovládacího prvku.

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>Parametry

*bAutoClip*<br/>
Vlastnost DISPID_AMBIENT_AUTOCLIP.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="getambientbackcolor"></a>CComControlBase::GetAmbientBackColor

Načte DISPID_AMBIENT_BACKCOLOR, okolní barvu pozadí pro všechny ovládací prvky definované kontejnerem.

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>Parametry

*BackColor*<br/>
Vlastnost DISPID_AMBIENT_BACKCOLOR.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="getambientcharset"></a>CComControlBase::GetAmbientCharSet

Načítá DISPID_AMBIENT_CHARSET, okolní znaková sada pro všechny ovládací prvky, které jsou definovány kontejnerem.

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>Parametry

*bstrCharSet*<br/>
Vlastnost DISPID_AMBIENT_CHARSET.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="getambientcodepage"></a>CComControlBase::GetAmbientCodePage

Načte DISPID_AMBIENT_CODEPAGE, okolí znakové stránky pro všechny ovládací prvky, které jsou definovány kontejnerem.

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>Parametry

*ulCodePage*<br/>
Vlastnost DISPID_AMBIENT_CODEPAGE.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="getambientdisplayasdefault"></a>CComControlBase::GetAmbientDisplayAsDefault

Načítá DISPID_AMBIENT_DISPLAYASDEFAULT, příznak, který má hodnotu TRUE, pokud kontejner označil ovládací prvek v tomto webu jako výchozí tlačítko, a proto by se měl ovládací prvek tlačítko vykreslovat pomocí silného rámce.

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*bDisplayAsDefault*<br/>
Vlastnost DISPID_AMBIENT_DISPLAYASDEFAULT.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="getambientdisplayname"></a>CComControlBase::GetAmbientDisplayName

Načte DISPID_AMBIENT_DISPLAYNAME název kontejneru dodaný do ovládacího prvku.

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>Parametry

*bstrDisplayName*<br/>
Vlastnost DISPID_AMBIENT_DISPLAYNAME.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="getambientfont"></a>CComControlBase::GetAmbientFont

Načte ukazatel na okolní `IFont` rozhraní kontejneru.

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont*<br/>
Ukazatel na rozhraní ambientního [IFont](/windows/win32/api/ocidl/nn-ocidl-ifont) kontejneru.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Pokud má vlastnost hodnotu NULL, ukazatel má hodnotu NULL. Pokud ukazatel není NULL, volající musí vydávat ukazatel.

##  <a name="getambientfontdisp"></a>CComControlBase::GetAmbientFontDisp

Načte ukazatel na rozhraní pro expedici `IFontDisp` v kontejneru.

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont*<br/>
Ukazatel na rozhraní [IFontDisp](/windows/win32/api/ocidl/nn-ocidl-ifontdisp) pro expedici kontejneru.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Pokud má vlastnost hodnotu NULL, ukazatel má hodnotu NULL. Pokud ukazatel není NULL, volající musí vydávat ukazatel.

##  <a name="getambientforecolor"></a>CComControlBase::GetAmbientForeColor

Načítá DISPID_AMBIENT_FORECOLOR, okolní barvu popředí pro všechny ovládací prvky definované kontejnerem.

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>Parametry

*ForeColor*<br/>
Vlastnost DISPID_AMBIENT_FORECOLOR.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="getambientlocaleid"></a>CComControlBase::GetAmbientLocaleID

Načte DISPID_AMBIENT_LOCALEID identifikátor jazyka používaného kontejnerem.

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>Parametry

*lcid*<br/>
Vlastnost DISPID_AMBIENT_LOCALEID.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Ovládací prvek může použít tento identifikátor k přizpůsobení uživatelského rozhraní k různým jazykům.

##  <a name="getambientmessagereflect"></a>CComControlBase::GetAmbientMessageReflect

Načte DISPID_AMBIENT_MESSAGEREFLECT příznak označující, zda má kontejner přijímat zprávy okna (například `WM_DRAWITEM`) jako události.

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>Parametry

*bMessageReflect*<br/>
Vlastnost DISPID_AMBIENT_MESSAGEREFLECT.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="getambientpalette"></a>CComControlBase::GetAmbientPalette

Načte DISPID_AMBIENT_PALETTE, který se používá pro přístup k HPALETTE kontejneru.

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>Parametry

*hPalette*<br/>
Vlastnost DISPID_AMBIENT_PALETTE.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="getambientproperty"></a>CComControlBase::GetAmbientProperty

Načte vlastnost kontejneru určenou identifikátorem *DISPID*.

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>Parametry

*DISPID*<br/>
Identifikátor vlastnosti kontejneru, který se má načíst

*var*<br/>
Proměnná pro přijetí vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Knihovna ATL poskytuje sadu pomocných funkcí pro načtení specifických vlastností, například [CComControlBase:: GetAmbientBackColor](#getambientbackcolor). Pokud není k dispozici žádná vhodná metoda, použijte `GetAmbientProperty`.

##  <a name="getambientrighttoleft"></a>CComControlBase::GetAmbientRightToLeft

Načte DISPID_AMBIENT_RIGHTTOLEFT, směr, ve kterém se obsah zobrazuje v kontejneru.

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>Parametry

*bRightToLeft*<br/>
Vlastnost DISPID_AMBIENT_RIGHTTOLEFT. Nastavte na TRUE, pokud je obsah zobrazený zprava doleva, FALSE, pokud je zobrazená zleva doprava.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="getambientscaleunits"></a>CComControlBase::GetAmbientScaleUnits

Načte DISPID_AMBIENT_SCALEUNITS, okolní jednotky kontejneru (například palce nebo centimetry) pro zobrazení popisků.

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>Parametry

*bstrScaleUnits*<br/>
Vlastnost DISPID_AMBIENT_SCALEUNITS.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="getambientshowgrabhandles"></a>CComControlBase::GetAmbientShowGrabHandles

Načítá DISPID_AMBIENT_SHOWGRABHANDLES, příznak označující, zda kontejner umožňuje ovládacímu prvku zobrazit obslužné rutiny pro sebe sama, když je aktivní.

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>Parametry

*bShowGrabHandles*<br/>
Vlastnost DISPID_AMBIENT_SHOWGRABHANDLES.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="getambientshowhatching"></a>CComControlBase::GetAmbientShowHatching

Načítá DISPID_AMBIENT_SHOWHATCHING, příznak označující, zda kontejner umožňuje ovládacímu prvku, aby se zobrazil s šrafovaném vzorem, když je uživatelské rozhraní ovládacího prvku aktivní.

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>Parametry

*bShowHatching*<br/>
Vlastnost DISPID_AMBIENT_SHOWHATCHING.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="getambientsupportsmnemonics"></a>CComControlBase::GetAmbientSupportsMnemonics

Načte DISPID_AMBIENT_SUPPORTSMNEMONICS příznak označující, zda kontejner podporuje klávesové zkratky.

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>Parametry

*bSupportsMnemonics*<br/>
Vlastnost DISPID_AMBIENT_SUPPORTSMNEMONICS.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="getambienttextalign"></a>CComControlBase::GetAmbientTextAlign

Načítá DISPID_AMBIENT_TEXTALIGN, zarovnání textu preferované kontejnerem: 0 pro Obecné zarovnání (číslice doprava, text vlevo), 1 pro zarovnání vlevo, 2 pro zarovnání na střed a 3 pro zarovnání vpravo.

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>Parametry

*nTextAlign*<br/>
Vlastnost DISPID_AMBIENT_TEXTALIGN.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="getambienttoptobottom"></a>CComControlBase::GetAmbientTopToBottom

Načte DISPID_AMBIENT_TOPTOBOTTOM, směr, ve kterém se obsah zobrazuje v kontejneru.

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>Parametry

*bTopToBottom*<br/>
Vlastnost DISPID_AMBIENT_TOPTOBOTTOM. Nastavte na hodnotu TRUE, pokud se zobrazí text shora dolů, hodnota FALSE, pokud je zobrazená zdola nahoru.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="getambientuidead"></a>CComControlBase::GetAmbientUIDead

Načte DISPID_AMBIENT_UIDEAD příznak označující, zda kontejner chce ovládací prvek reagovat na akce uživatelského rozhraní.

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>Parametry

*bUIDead*<br/>
Vlastnost DISPID_AMBIENT_UIDEAD.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Je-li nastavena hodnota TRUE, ovládací prvek by neměl reagovat. Tento příznak platí bez ohledu na příznak DISPID_AMBIENT_USERMODE. Viz [CComControlBase:: GetAmbientUserMode](#getambientusermode).

##  <a name="getambientusermode"></a>CComControlBase::GetAmbientUserMode

Načte DISPID_AMBIENT_USERMODE příznak označující, zda je kontejner v režimu běhu (TRUE) nebo v režimu návrhu (FALSE).

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>Parametry

*bUserMode*<br/>
Vlastnost DISPID_AMBIENT_USERMODE.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="getdirty"></a>CComControlBase:: getdirty

Vrátí hodnotu datového členu `m_bRequiresSave`.

```
BOOL GetDirty();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu datového členu [m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Poznámky

Tato hodnota je nastavena pomocí [CComControlBase:: SetDirty](#setdirty).

##  <a name="getzoominfo"></a>CComControlBase::GetZoomInfo

Načte hodnoty x a y čitateli a jmenovatele faktoru přiblížení pro ovládací prvek aktivovaný pro místní úpravy.

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*dži*<br/>
Struktura, která bude obsahovat čitatel a jmenovatel faktoru přiblížení. Další informace najdete v tématu [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).

### <a name="remarks"></a>Poznámky

Faktor přiblížení je poměr přirozené velikosti ovládacího prvku k jeho aktuálnímu rozsahu.

##  <a name="inplaceactivate"></a>CComControlBase::InPlaceActivate

Způsobí přechod ovládacího prvku z neaktivního stavu do libovolného stavu, který příkaz v *iVerb* označuje.

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Hodnota určující akci, kterou má provést [IOleObjectImpl::D overb](../../atl/reference/ioleobjectimpl-class.md#doverb).

*prcPosRect*<br/>
Ukazatel na pozici místního ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Před aktivací Tato metoda zkontroluje, zda má ovládací prvek klientský server, zkontroluje, jak velká část ovládacího prvku je viditelná a získá umístění ovládacího prvku v nadřazeném okně. Po aktivaci ovládacího prvku Tato metoda aktivuje uživatelské rozhraní ovládacího prvku a oznámí kontejneru, aby byl ovládací prvek viditelný.

Tato metoda také načte ukazatel rozhraní `IOleInPlaceSite`, `IOleInPlaceSiteEx`nebo `IOleInPlaceSiteWindowless` pro ovládací prvek a uloží jej do datového členu třídy ovládacího prvku [CComControlBase:: m_spInPlaceSite](#m_spinplacesite). Datové členy třídy ovládacího prvku [CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase:: m_bWndLess](#m_bwndless), [CComControlBase:: m_bWasOnceWindowless](#m_bwasoncewindowless)a [CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd) jsou nastaveny na hodnotu true podle potřeby.

##  <a name="internalgetsite"></a>CComControlBase::InternalGetSite

Zavolejte tuto metodu pro dotazování webu ovládacího prvku pro ukazatel na identifikované rozhraní.

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identifikátor IID ukazatele rozhraní, který by měl být vrácen v *ppUnkSite*.

*ppUnkSite*<br/>
Adresa proměnné ukazatele, která obdrží ukazatel rozhraní požadovaný v *riid*.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Pokud lokalita podporuje rozhraní požadované v *riid*, ukazatel se vrátí prostřednictvím *ppUnkSite*. V opačném případě je *ppUnkSite* nastaveno na hodnotu null.

##  <a name="m_bautosize"></a>CComControlBase:: m_bAutoSize

Příznak označující, že ovládací prvek nemůže být jinou velikostí

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>Poznámky

Tento příznak je kontrolován `IOleObjectImpl::SetExtent` a v případě hodnoty TRUE způsobí, že funkce vrátí E_FAIL.

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Pokud přidáte možnost **automatické velikosti** na kartě [akcie](../../atl/reference/stock-properties-atl-control-wizard.md) Průvodce ovládacím prvkem ATL, průvodce automaticky vytvoří tohoto datového člena ve třídě ovládacího prvku, vytvoří metody PUT a Get pro vlastnost a podporuje [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) pro automatické oznamování kontejneru při změně vlastnosti.

##  <a name="m_bdrawfromnatural"></a>CComControlBase:: m_bDrawFromNatural

Příznak označující, že `IDataObjectImpl::GetData` a `CComControlBase::GetZoomInfo` by měl nastavit velikost ovládacího prvku z `m_sizeNatural` namísto `m_sizeExtent`.

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_bdrawgetdatainhimetric"></a>CComControlBase:: m_bDrawGetDataInHimetric

Příznak označující, že při kreslení má `IDataObjectImpl::GetData` použít jednotky HIMETRIC a ne pixely

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>Poznámky

Každá logická jednotka HIMETRIC je 0,01 mm.

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_binplaceactive"></a>CComControlBase:: m_bInPlaceActive

Příznak označující, že ovládací prvek je na místě aktivní

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>Poznámky

To znamená, že ovládací prvek je viditelný a jeho okno, pokud je viditelné, ale jeho nabídky a panely nástrojů nemusí být aktivní. Příznak `m_bUIActive` označuje, že uživatelské rozhraní ovládacího prvku, jako jsou nabídky, je také aktivní.

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_binplacesiteex"></a>CComControlBase:: m_bInPlaceSiteEx

Příznak označující, že kontejner podporuje rozhraní `IOleInPlaceSiteEx` a funkce ovládacího prvku OCX96, například ovládací prvky bez oken a blikání.

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Datový člen `m_spInPlaceSite` odkazuje na rozhraní [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)nebo [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) v závislosti na hodnotě `m_bWndLess` a `m_bInPlaceSiteEx`ch příznaků. (Datový člen `m_bNegotiatedWnd` musí být TRUE, aby byl ukazatel `m_spInPlaceSite` platný.)

Pokud je `m_bWndLess` FALSE a `m_bInPlaceSiteEx` je TRUE, `m_spInPlaceSite` je ukazatel rozhraní `IOleInPlaceSiteEx`. V části [m_spInPlaceSite](#m_spinplacesite) najdete tabulku znázorňující vztah mezi těmito třemi datovými členy.

##  <a name="m_bnegotiatedwnd"></a>CComControlBase:: m_bNegotiatedWnd

Příznak označující, zda se ovládací prvek vyjednal s kontejnerem o podpoře funkcí ovládacího prvku OCX96 (například ovládací prvky bez blikání a ovládacích prvků bez oken) a zda je ovládací prvek v okně nebo bez okna.

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Aby byl ukazatel `m_spInPlaceSite` platný, musí mít příznak `m_bNegotiatedWnd` hodnotu TRUE.

##  <a name="m_brecomposeonresize"></a>CComControlBase:: m_bRecomposeOnResize

Příznak označující, že ovládací prvek chce znovu vytvořit svou prezentaci, když kontejner změní velikost zobrazení ovládacího prvku

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Tento příznak kontroluje [IOleObjectImpl:: SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) a při hodnotě true `SetExtent` upozorní kontejner zobrazení změn. Pokud je tento příznak nastaven, musí být také nastaven bit OLEMISC_RECOMPOSEONRESIZE v výčtu [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) .

##  <a name="m_brequiressave"></a>CComControlBase:: m_bRequiresSave

Příznak označující, že se ovládací prvek od posledního uložení změnil

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>Poznámky

Hodnotu `m_bRequiresSave` lze nastavit pomocí [CComControlBase:: SetDirty](#setdirty) a načíst pomocí [CComControlBase:: getdirty](#getdirty).

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_bresizenatural"></a>CComControlBase:: m_bResizeNatural

Příznak označující, že ovládací prvek chce změnit velikost přirozeného rozsahu (jeho neškálovaná fyzická velikost), když kontejner změní velikost zobrazení ovládacího prvku

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>Poznámky

Tento příznak je kontrolován `IOleObjectImpl::SetExtent` a v případě hodnoty TRUE je velikost předaná do `SetExtent` přiřazena `m_sizeNatural`.

Velikost předaná do `SetExtent` je vždy přiřazena `m_sizeExtent`, bez ohledu na hodnotu `m_bResizeNatural`.

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_buiactive"></a>CComControlBase:: m_bUIActive

Příznak označující, že uživatelské rozhraní ovládacího prvku, například nabídky a panely nástrojů, je aktivní.

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>Poznámky

Příznak `m_bInPlaceActive` označuje, že je ovládací prvek aktivní, ale není aktivní jeho uživatelské rozhraní.

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_busingwindowrgn"></a>CComControlBase:: m_bUsingWindowRgn

Příznak označující, že ovládací prvek používá oblast okna poskytnutou kontejnerem.

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_bwasoncewindowless"></a>CComControlBase:: m_bWasOnceWindowless

Příznak označující, že ovládací prvek byl bez okna, ale může nebo nemusí být nyní bez okna.

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_bwindowonly"></a>CComControlBase:: m_bWindowOnly

Příznak označující, že má být ovládací prvek nastaven na okno, i v případě, že kontejner podporuje ovládací prvky bez oken.

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_bwndless"></a>CComControlBase:: m_bWndLess

Příznak označující, že ovládací prvek je bez okna.

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Datový člen `m_spInPlaceSite` odkazuje na rozhraní [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)nebo [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) v závislosti na hodnotě příznaků `m_bWndLess` a [CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex) . (Datový člen [CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd) musí mít hodnotu true, aby ukazatel [CComControlBase:: m_spInPlaceSite](#m_spinplacesite) byl platný.)

Pokud je `m_bWndLess` TRUE, `m_spInPlaceSite` je ukazatel rozhraní `IOleInPlaceSiteWindowless`. V tématu [CComControlBase:: m_spInPlaceSite](#m_spinplacesite) v tabulce zobrazující kompletní relaci mezi těmito datovými členy.

##  <a name="m_hwndcd"></a>CComControlBase:: m_hWndCD

Obsahuje odkaz na popisovač okna přidružený k ovládacímu prvku.

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_nfreezeevents"></a>CComControlBase:: m_nFreezeEvents

Počet, kolikrát kontejner obsahuje zmrazené události (odmítl přijímat události) bez ovlivnění odmrazení událostí (přijetí událostí).

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_rcpos"></a>CComControlBase:: m_rcPos

Pozice v pixelech ovládacího prvku vyjádřená v souřadnicích kontejneru.

```
RECT m_rcPos;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_sizeextent"></a>CComControlBase:: m_sizeExtent

Rozsah ovládacího prvku v jednotkách HIMETRIC (každá jednotka je 0,01 milimetrů) pro konkrétní displej.

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Tato velikost se škáluje zobrazením. Fyzická velikost ovládacího prvku je určena v datovém členu `m_sizeNatural` a je opravena.

Velikost můžete převést na pixely s globální funkcí [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

##  <a name="m_sizenatural"></a>CComControlBase:: m_sizeNatural

Fyzická velikost ovládacího prvku v jednotkách HIMETRIC (každá jednotka je 0,01 milimetrů).

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Tato velikost je pevná, ale velikost v `m_sizeExtent` je zvětšena zobrazením.

Velikost můžete převést na pixely s globální funkcí [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

##  <a name="m_spadvisesink"></a>CComControlBase:: m_spAdviseSink

Přímý ukazatel na poradní připojení na kontejneru ( [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)kontejneru).

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_spambientdispatch"></a>CComControlBase:: m_spAmbientDispatch

Objekt `CComDispatchDriver`, který umožňuje načíst a nastavit vlastnosti objektu prostřednictvím ukazatele `IDispatch`.

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_spclientsite"></a>CComControlBase:: m_spClientSite

Ukazatel na klientský web ovládacího prvku v rámci kontejneru.

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_spdataadviseholder"></a>CComControlBase:: m_spDataAdviseHolder

Poskytuje standardní způsob, jak uchovávat poradenská připojení mezi datovými objekty a příjímkami pro poradenství.

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Datový objekt je ovládací prvek, který může přenášet data a implementuje [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject), jejichž metody určují formát a přenos středníku dat.

Rozhraní `m_spDataAdviseHolder` implementuje [IDataObject::D Advise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) a [IDataObject::D odradit](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) metody pro vytvoření a odstranění poradenských připojení ke kontejneru. Kontejner ovládacího prvku musí implementovat jímku služby Advise tím, že podporuje rozhraní [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) .

##  <a name="m_spinplacesite"></a>CComControlBase:: m_spInPlaceSite

Ukazatel na ukazatel rozhraní [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)nebo [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) kontejneru.

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Ukazatel `m_spInPlaceSite` je platný pouze v případě, že příznak [m_bNegotiatedWnd](#m_bnegotiatedwnd) má hodnotu true.

Následující tabulka ukazuje, jak typ ukazatele `m_spInPlaceSite` závisí na příznacích [m_bWndLess](#m_bwndless) a [m_bInPlaceSiteExch](#m_binplacesiteex) datových členů:

|Typ m_spInPlaceSite|Hodnota m_bWndLess|Hodnota m_bInPlaceSiteEx|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|PRAVDA|TRUE nebo FALSE|
|`IOleInPlaceSiteEx`|CHYBNÉ|PRAVDA|
|`IOleInPlaceSite`|CHYBNÉ|CHYBNÉ|

##  <a name="m_spoleadviseholder"></a>CComControlBase:: m_spOleAdviseHolder

Poskytuje standardní implementaci způsobu uchovávání poradenských připojení.

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Chcete-li použít tohoto datového člena v rámci třídy ovládacího prvku, je nutné jej deklarovat jako datový člen ve třídě ovládacího prvku. Vaše třída ovládacího prvku nedědí tohoto datového člena ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Rozhraní `m_spOleAdviseHolder` implementuje metody [IOleObject:: Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) a [IOleObject:: Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) pro vytváření a odstraňování poradenských připojení ke kontejneru. Kontejner ovládacího prvku musí implementovat jímku služby Advise tím, že podporuje rozhraní [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) .

##  <a name="ondraw"></a>CComControlBase:: Draw

Tuto metodu přepište, pokud chcete ovládací prvek nakreslit.

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*dži*<br/>
Odkaz na strukturu [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) , která obsahuje informace o kreslení, jako je například aspekt vykreslování, ovládací prvky svázané a zda je výkres optimalizován.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Výchozí `OnDraw` odstraní nebo obnoví kontext zařízení nebo nedělá nic v závislosti na příznacích nastavených v [CComControlBase:: OnDrawAdvanced](#ondrawadvanced).

Metoda `OnDraw` je automaticky přidána do vaší třídy ovládacího prvku při vytvoření ovládacího prvku pomocí Průvodce ovládacím prvkem ATL. Výchozí `OnDraw` Průvodce nakreslí obdélník s popiskem ATL 8,0.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CComControlBase:: GetAmbientAppearance](#getambientappearance).

##  <a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced

Výchozí `OnDrawAdvanced` připraví normalizovaný kontext zařízení pro kreslení a pak volá metodu `OnDraw` vaší třídy ovládacího prvku.

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*dži*<br/>
Odkaz na strukturu [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) , která obsahuje informace o kreslení, jako je například aspekt vykreslování, ovládací prvky svázané a zda je výkres optimalizován.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete přijmout kontext zařízení předaný kontejnerem bez jeho normalizace.

Další podrobnosti najdete v tématu [CComControlBase::-Draw](#ondraw) .

##  <a name="onkillfocus"></a>CComControlBase::OnKillFocus

Kontroluje, zda je ovládací prvek na místě aktivní a má platnou řídicí lokalitu, a poté informuje o kontejneru, že ovládací prvek ztratil fokus.

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Rezervovaný.

*wParam*<br/>
Rezervovaný.

*lParam*<br/>
Rezervovaný.

*bHandled*<br/>
Příznak, který označuje, zda byla zpráva okna úspěšně zpracována. Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

Vždycky vrátí hodnotu 1.

##  <a name="onmouseactivate"></a>CComControlBase::OnMouseActivate

Kontroluje, zda je uživatelské rozhraní v uživatelském režimu, a poté aktivuje ovládací prvek.

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Rezervovaný.

*wParam*<br/>
Rezervovaný.

*lParam*<br/>
Rezervovaný.

*bHandled*<br/>
Příznak, který označuje, zda byla zpráva okna úspěšně zpracována. Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

Vždycky vrátí hodnotu 1.

##  <a name="onpaint"></a>CComControlBase:: propaintt

Připraví kontejner pro vybarvení, získá klientskou oblast ovládacího prvku a pak zavolá metodu `OnDrawAdvanced` třídy ovládacího prvku.

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Rezervovaný.

*wParam*<br/>
Existující HDC.

*lParam*<br/>
Rezervovaný.

*Získání výsledku LRESULT*<br/>
Rezervovaný.

### <a name="return-value"></a>Návratová hodnota

Vždycky vrátí nulu.

### <a name="remarks"></a>Poznámky

Pokud *wParam* není NULL, `OnPaint` předpokládá, že obsahuje platný HDC a použije ji místo [CComControlBase:: m_hWndCD](#m_hwndcd).

##  <a name="onsetfocus"></a>CComControlBase:: OnSetFocus

Kontroluje, zda je ovládací prvek na místě aktivní a má platnou řídicí lokalitu, a poté informuje o kontejneru, který ovládací prvek získal fokus.

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Rezervovaný.

*wParam*<br/>
Rezervovaný.

*lParam*<br/>
Rezervovaný.

*bHandled*<br/>
Příznak, který označuje, zda byla zpráva okna úspěšně zpracována. Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

Vždycky vrátí hodnotu 1.

### <a name="remarks"></a>Poznámky

Pošle oznámení do kontejneru, který ovládací prvek obdržel fokus.

##  <a name="pretranslateaccelerator"></a>CComControlBase::P reTranslateAccelerator

Tuto metodu přepište, pokud chcete poskytnout vlastní obslužné rutiny pro klávesové zkratky.

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Rezervovaný.

*hRet*<br/>
Rezervovaný.

### <a name="return-value"></a>Návratová hodnota

Ve výchozím nastavení vrátí hodnotu FALSE.

##  <a name="sendonclose"></a>CComControlBase::SendOnClose

Upozorní všechny informační jímky zaregistrované u držitele poradenství, že byl ovládací prvek uzavřen.

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Pošle oznámení, že ovládací prvek uzavřel své poradenské jímky.

##  <a name="sendondatachange"></a>CComControlBase::SendOnDataChange

Upozorní všechny informační jímky zaregistrované u držitele poradenství, že se data ovládacího prvku změnila.

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>Parametry

*advf*<br/>
Příznaky pro upozornění, které určují, jak se provádí volání metody [IAdviseSink:: OnDataChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange) . Hodnoty jsou z výčtu [ADVF](/windows/win32/api/objidl/ne-objidl-advf) .

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="sendonrename"></a>CComControlBase::SendOnRename

Upozorní všechny informační jímky zaregistrované u držitele poradenství, že má ovládací prvek nový moniker.

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>Parametry

*Key*<br/>
Ukazatel na nový moniker ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Pošle oznámení, že se změnil moniker ovládacího prvku.

##  <a name="sendonsave"></a>CComControlBase::SendOnSave

Upozorní všechny informační jímky zaregistrované u držitele poradenství, že byl ovládací prvek uložen.

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Pošle oznámení, že ovládací prvek právě uložil svá data.

##  <a name="sendonviewchange"></a>CComControlBase::SendOnViewChange

Upozorní všechny zaregistrované poradenské jímky, že se změnilo zobrazení ovládacího prvku.

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>Parametry

*dwAspect*<br/>
Aspekt nebo zobrazení ovládacího prvku.

*lindex*<br/>
Část zobrazení, která se změnila. Platný je pouze-1.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

`SendOnViewChange` volá [IAdviseSink:: OnViewChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange). Jediná aktuálně podporovaná hodnota *Lindex* je-1, což znamená, že celé zobrazení je zajímavé.

##  <a name="setcontrolfocus"></a>CComControlBase::SetControlFocus

Nastaví nebo odebere fokus klávesnice na nebo z ovládacího prvku.

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>Parametry

*bGrab*<br/>
Je-li nastavena hodnota TRUE, nastaví fokus klávesnice na volající ovládací prvek. Pokud je hodnota FALSE, odebere fokus klávesnice z ovládacího prvku volání, pokud má fokus.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud ovládací prvek úspěšně obdrží fokus. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pro ovládací prvek v okně se zavolá funkce Windows API [SetFocus](/windows/win32/api/winuser/nf-winuser-setfocus) . Pro řízení bez oken se volá [IOleInPlaceSiteWindowless:: SetFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) . Prostřednictvím tohoto volání ovládací prvek bez oken získá fokus klávesnice a může reagovat na zprávy okna.

##  <a name="setdirty"></a>CComControlBase::SetDirty

Nastaví datový člen `m_bRequiresSave` na hodnotu v *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*bDirty*<br/>
Hodnota datového členu [CComControlBase:: m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Poznámky

`SetDirty(TRUE)` by měla být volána k označení toho, že se ovládací prvek od posledního uložení změnil. Hodnota `m_bRequiresSave` je načtena pomocí [CComControlBase:: Getdirty](#getdirty).

## <a name="see-also"></a>Viz také

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
