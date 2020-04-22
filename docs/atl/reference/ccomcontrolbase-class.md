---
title: Třída CComControlBase
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
ms.openlocfilehash: 15cfa205337248181f02e6a1218d49e75bda58e6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748107"
---
# <a name="ccomcontrolbase-class"></a>Třída CComControlBase

Tato třída poskytuje metody pro vytváření a správu ovládacích prvků ATL.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Název|Popis|
|----------|-----------------|
|[CComControlBase::Typ vzhledu](#appearancetype)|Přepsat, pokud `m_nAppearance` vaše zásoby vlastnost není typu **krátké**.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|Konstruktor|
|[CComControlBase::~CComControlBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComControlBase::Rozhraní ControlQueryInterface](#controlqueryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Zkontroluje, zda parametr `IOleObjectImpl::DoVerb` *iVerb* použitý buď aktivuje uživatelské rozhraní ovládacího prvku (*iVerb* se rovná OLEIVERB_UIACTIVATE), definuje akci přijatou při poklepání na ovládací prvek (*iVerb* se rovná OLEIVERB_PRIMARY), zobrazí ovládací prvek (*iVerb* se rovná OLEIVERB_SHOW), nebo aktivuje ovládací prvek (*iVerb* se rovná OLEIVERB_INPLACEACTIVATE).|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Zkontroluje, zda parametr `IOleObjectImpl::DoVerb` *iVerb* používaný způsobí aktivaci uživatelského rozhraní ovládacího prvku a vrátí hodnotu TRUE.|
|[CComControlBase::DoVerbProperties](#doverbproperties)|Zobrazí stránky vlastností ovládacího prvku.|
|[Ccomcontrolbase::FireViewChange](#fireviewchange)|Volání této metody sdělit kontejneru překreslit ovládací prvek nebo upozornit registrované doporučit jímky, že zobrazení ovládacího prvku se změnil.|
|[Ccomcontrolbase::GetAmbientVzhled](#getambientappearance)|Načte DISPID_AMBIENT_APPEARANCE, aktuální nastavení vzhledu ovládacího prvku: 0 pro ploché a 1 pro 3D.|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Načte DISPID_AMBIENT_AUTOCLIP, příznak označující, zda kontejner podporuje automatické oříznutí oblasti zobrazení ovládacího prvku.|
|[Ccomcontrolbase::GetAmbientBackColor](#getambientbackcolor)|Načte DISPID_AMBIENT_BACKCOLOR, barvu pozadí okolí pro všechny ovládací prvky definované kontejnerem.|
|[Ccomcontrolbase::Getambientcharset](#getambientcharset)|Načte DISPID_AMBIENT_CHARSET, okolní znakovou sadu pro všechny ovládací prvky, definované kontejneru.|
|[CcomControlBase::GetAmbientCodePage](#getambientcodepage)|Načte DISPID_AMBIENT_CODEPAGE, okolní znakovou sadu pro všechny ovládací prvky, definované kontejneru.|
|[Ccomcontrolbase::GetambientDisplayAsVýchozí](#getambientdisplayasdefault)|Načte DISPID_AMBIENT_DISPLAYASDEFAULT, příznak, který je TRUE, pokud kontejner označil ovládací prvek na této stránce jako výchozí tlačítko, a proto by se ovládací prvek tlačítka měl kreslit sám s tlustším rámečkem.|
|[CcomControlBase::GetambientDisplayName](#getambientdisplayname)|Načte DISPID_AMBIENT_DISPLAYNAME, název kontejneru dodal ovládacímu prvku.|
|[CcomControlBase::GetAmbientFont](#getambientfont)|Načte ukazatel na okolní `IFont` rozhraní kontejneru.|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Načte ukazatel na okolí `IFontDisp` rozhraní odeslání kontejneru.|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Načte DISPID_AMBIENT_FORECOLOR, barvu okolí popředí pro všechny ovládací prvky definované kontejnerem.|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Načte DISPID_AMBIENT_LOCALEID, identifikátor jazyka používaného kontejneru.|
|[Ccomcontrolbase::GetAmbientMessageReflect](#getambientmessagereflect)|Načte DISPID_AMBIENT_MESSAGEREFLECT, příznak označující, zda kontejner chce přijímat zprávy okna (například WM_DRAWITEM) jako události.|
|[Ccomcontrolbase::GetAmbientPalette](#getambientpalette)|Načte DISPID_AMBIENT_PALETTE, slouží k přístupu k kontejneru HPALETTE.|
|[CcomControlBase::GetAmbientProperty](#getambientproperty)|Načte vlastnost kontejneru určenou *id*.|
|[Ccomcontrolbase::GetambientRightToLeft](#getambientrighttoleft)|Načte DISPID_AMBIENT_RIGHTTOLEFT, směr, ve kterém je obsah zobrazen kontejnerem.|
|[CcomControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Načte DISPID_AMBIENT_SCALEUNITS okolní jednotky kontejneru (například palce nebo centimetry) pro zobrazení popisků.|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Načte DISPID_AMBIENT_SHOWGRABHANDLES, příznak označující, zda kontejner umožňuje ovládací prvek zobrazit úchyty pro sebe při aktivní.|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Načte DISPID_AMBIENT_SHOWHATCHING, příznak označující, zda kontejner umožňuje ovládací prvek zobrazit sám se šrafovaným vzorem, když je aktivní.|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Načte DISPID_AMBIENT_SUPPORTSMNEMONICS příznak označující, zda kontejner podporuje mnemotechnické pomůcky klávesnice.|
|[Ccomcontrolbase::GetAmbientTextAlign](#getambienttextalign)|Načte DISPID_AMBIENT_TEXTALIGN, zarovnání textu upřednostňované kontejnerem: 0 pro obecné zarovnání (čísla vpravo, text vlevo), 1 pro zarovnání vlevo, 2 pro zarovnání na střed a 3 pro pravé zarovnání.|
|[Ccomcontrolbase::GetambienttopToBottom](#getambienttoptobottom)|Načte DISPID_AMBIENT_TOPTOBOTTOM, směr, ve kterém je obsah zobrazen kontejnerem.|
|[Ccomcontrolbase::GetambientuiDead](#getambientuidead)|Načte DISPID_AMBIENT_UIDEAD příznak označující, zda kontejner chce, aby ovládací prvek reagoval na akce uživatelského rozhraní.|
|[CcomControlBase::GetAmbientUserMode](#getambientusermode)|Načte DISPID_AMBIENT_USERMODE příznak označující, zda je kontejner v režimu spuštění (TRUE) nebo v režimu návrhu (FALSE).|
|[Ccomcontrolbase::GetDirty](#getdirty)|Vrátí hodnotu datového člena `m_bRequiresSave`.|
|[Ccomcontrolbase::GetZoomInfo](#getzoominfo)|Načte hodnoty x a y čitatela a jmenovatele faktoru přiblížení pro ovládací prvek aktivovaný pro úpravy na místě.|
|[Ccomcontrolbase::InplaceActivate](#inplaceactivate)|Způsobí, že ovládací prvek přechod z neaktivní ho stavu do libovolného stavu sloveso v *iVerb* označuje.|
|[CComControlBase::InternalGetSite](#internalgetsite)|Volání této metody k dotazu na server ovládacího prvku pro ukazatel na identifikované rozhraní.|
|[Ccomcontrolbase::Ondraw](#ondraw)|Přepsat tuto metodu k nakreslení ovládacího prvku.|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|Výchozí `OnDrawAdvanced` připraví normalizované zařízení kontextu pro kreslení, pak volá `OnDraw` metodu třídy ovládacího prvku.|
|[Ccomcontrolbase::OnKillFocus](#onkillfocus)|Zkontroluje, zda je ovládací prvek aktivní na místě a má platný řídicí web, pak informuje kontejner, že ovládací prvek ztratil fokus.|
|[Ccomcontrolbase::OnMouseActivate](#onmouseactivate)|Zkontroluje, zda je uživatelské rozhraní v uživatelském režimu, a poté aktivuje ovládací prvek.|
|[Ccomcontrolbase::OnPaint](#onpaint)|Připraví kontejner pro malování, získá klientskou oblast ovládacího prvku a `OnDraw` pak zavolá metodu třídy ovládacího prvku.|
|[Ccomcontrolbase::OnSetFocus](#onsetfocus)|Zkontroluje, zda je ovládací prvek aktivní na místě a má platné řídicí místo, pak informuje kontejner, na který ovládací prvek získal fokus.|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Přepsat tuto metodu poskytnout vlastní obslužné rutiny akcelerátoru klávesnice.|
|[Ccomcontrolbase::SendOnclose](#sendonclose)|Upozorní všechny poradní propady registrované u držitele advise, že ovládací prvek byl uzavřen.|
|[CcomControlBase::SendOnDataChange](#sendondatachange)|Upozorní všechny poradní propady registrované u držitele advise, že se změnila data ovládacího prvku.|
|[CComControlBase::SendOnRename](#sendonrename)|Upozorní všechny poradní jímky registrované u držitele advise, že ovládací prvek má nový zástupný název.|
|[Ccomcontrolbase::SendOnSave](#sendonsave)|Upozorní všechny poradní jímky registrované u držitele advise, že ovládací prvek byl uložen.|
|[Ccomcontrolbase::SendOnViewChange](#sendonviewchange)|Upozorní všechny registrované poradní propady, že zobrazení ovládacího prvku se změnilo.|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Nastaví nebo odebere fokus klávesnice na ovládací prvek nebo z ovládacího prvku.|
|[CComControlBase::SetDirty](#setdirty)|Nastaví datový `m_bRequiresSave` člen na hodnotu v *bDirty*.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|Příznak označující ovládací prvek nemůže mít jinou velikost.|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Příznak `IDataObjectImpl::GetData` označující, `CComControlBase::GetZoomInfo` že a by `m_sizeNatural` měl `m_sizeExtent`nastavit velikost ovládacího prvku z spíše než z .|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Příznak označující, že `IDataObjectImpl::GetData` by měl používat HIMETRIC jednotky a ne pixely při kreslení.|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Příznak označující, že ovládací prvek je aktivní na místě.|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Příznak označující kontejner `IOleInPlaceSiteEx` podporuje rozhraní a ovládací prvky OCX96, jako jsou ovládací prvky bez oken a bez blikání.|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Příznak označující, zda ovládací prvek vyjednal s kontejnerem o podpoře funkcí ovládacího prvku OCX96 (například ovládací prvky bez blikání a bez oken) a zda je ovládací prvek v okně nebo bez oken.|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Příznak označující ovládací prvek chce změnit kompose jeho prezentace při kontejneru změní velikost zobrazení ovládacího prvku.|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Příznak označující, že ovládací prvek byl od posledního uložení změněn.|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Příznak označující ovládací prvek chce změnit velikost jeho přirozený rozsah (jeho neškálované fyzické velikosti) při kontejneru změní velikost zobrazení ovládacího prvku.|
|[CComControlBase::m_bUIActive](#m_buiactive)|Příznak označující uživatelské rozhraní ovládacího prvku, například nabídky a panely nástrojů, je aktivní.|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Příznak označující ovládací prvek používá oblast okna dodaného kontejnerem.|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Příznak označující ovládací prvek byl bez oken, ale může nebo nemusí být bez oken nyní.|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|Příznak označující ovládací prvek by měl být v okně, i v případě, že kontejner podporuje ovládací prvky bez oken.|
|[CComControlBase::m_bWndLess](#m_bwndless)|Příznak označující ovládací prvek je bez oken.|
|[CComControlBase::m_hWndCD](#m_hwndcd)|Obsahuje odkaz na popisovač okna přidružený k ovládacímu prvku.|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Počet, kolikrát kontejner zmrazil události (odmítl přijmout události) bez zasahující horečné události (přijetí událostí).|
|[CComControlBase::m_rcPos](#m_rcpos)|Pozice v obrazových bodech ovládacího prvku, vyjádřené v souřadnicích kontejneru.|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|Rozsah řízení v jednotkách HIMETRIC (každá jednotka je 0,01 milimetru) pro konkrétní displej.|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|Fyzikální velikost řízení v jednotkách HIMETRIC (každá jednotka je 0,01 milimetru).|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Přímý ukazatel na poradní připojení na kontejneru [(kontejneru IAdviseSink).](/windows/win32/api/objidl/nn-objidl-iadvisesink)|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|Objekt, `CComDispatchDriver` který umožňuje načíst a nastavit vlastnosti `IDispatch` kontejneru prostřednictvím ukazatele.|
|[CComControlBase::m_spClientSite](#m_spclientsite)|Ukazatel na klientské lokality ovládacího prvku v rámci kontejneru.|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Poskytuje standardní prostředky pro uložení informačních připojení mezi datovými objekty a poradenství jímky.|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Ukazatel na [kontejneru IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)nebo [IOleInPlaceSiteSitebez](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) ukazatele rozhraní.|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Poskytuje standardní implementaci způsob, jak držet poradní připojení.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro vytváření a správu ovládacích prvků ATL. [CComControl Třída](../../atl/reference/ccomcontrol-class.md) je `CComControlBase`odvozena od . Když vytvoříte ovládací prvek Standardní ovládací prvek nebo DHTML pomocí Průvodce ovládacím prvkem ATL, průvodce automaticky odvodí vaši třídu z `CComControlBase`aplikace .

Další informace o vytvoření ovládacího prvku naleznete v [kurzu atl](../../atl/active-template-library-atl-tutorial.md). Další informace o Průvodci projektem atl naleznete v článku [Vytvoření projektu atl](../../atl/reference/creating-an-atl-project.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="ccomcontrolbaseappearancetype"></a><a name="appearancetype"></a>CComControlBase::Typ vzhledu

Přepsat, pokud `m_nAppearance` vaše zásoby vlastnost není typu **krátké**.

```
typedef short AppearanceType;
```

### <a name="remarks"></a>Poznámky

Průvodce řízením atl přidá `m_nAppearance` vlastnost stock typu short. Přepište, `AppearanceType` pokud používáte jiný datový typ.

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="ccomcontrolbase"></a>CComControlBase::CComControlBase

Konstruktor

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Popisovač okna přidruženého k ovládacímu prvku.

### <a name="remarks"></a>Poznámky

Inicializuje velikost ovládacího prvku na 5080X5080 HIMETRIC jednotky (2 "X2") a inicializuje hodnoty `CComControlBase` datových členů na HODNOTU NULL nebo FALSE.

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="dtor"></a>CComControlBase::~CComControlBase

Destruktor.

```
~CComControlBase();
```

### <a name="remarks"></a>Poznámky

Pokud je ovládací prvek `~CComControlBase` v okně, zničí jej voláním [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow).

## <a name="ccomcontrolbasecontrolqueryinterface"></a><a name="controlqueryinterface"></a>CComControlBase::Rozhraní ControlQueryInterface

Načte ukazatel na požadované rozhraní.

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
Identifikátor GUID požadovaného rozhraní.

*Ppv*<br/>
Ukazatel rozhraní identifikovaný *iid*nebo NULL, pokud rozhraní není nalezeno.

### <a name="remarks"></a>Poznámky

Zpracovává pouze rozhraní v tabulce mapy COM.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

## <a name="ccomcontrolbasedoesverbactivate"></a><a name="doesverbactivate"></a>CComControlBase::DoesVerbActivate

Zkontroluje, zda parametr `IOleObjectImpl::DoVerb` *iVerb* použitý buď aktivuje uživatelské rozhraní ovládacího prvku (*iVerb* se rovná OLEIVERB_UIACTIVATE), definuje akci přijatou při poklepání na ovládací prvek (*iVerb* se rovná OLEIVERB_PRIMARY), zobrazí ovládací prvek (*iVerb* se rovná OLEIVERB_SHOW), nebo aktivuje ovládací prvek (*iVerb* se rovná OLEIVERB_INPLACEACTIVATE).

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iSponož*<br/>
Hodnota označující akci, která `DoVerb`má být provedena .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud se *funkce iVerb* rovná OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW nebo OLEIVERB_INPLACEACTIVATE; v opačném případě vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete přepsat a definovat vlastní aktivační sloveso.

## <a name="ccomcontrolbasedoesverbuiactivate"></a><a name="doesverbuiactivate"></a>CComControlBase::DoesVerbUIActivate

Zkontroluje, zda parametr `IOleObjectImpl::DoVerb` *iVerb* používaný způsobí aktivaci uživatelského rozhraní ovládacího prvku a vrátí hodnotu TRUE.

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iSponož*<br/>
Hodnota označující akci, která `DoVerb`má být provedena .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud se *funkce iVerb* rovná OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW nebo OLEIVERB_INPLACEACTIVATE. V opačném případě vrátí metoda hodnotu NEPRAVDA.

## <a name="ccomcontrolbasedoverbproperties"></a><a name="doverbproperties"></a>CComControlBase::DoVerbProperties

Zobrazí stránky vlastností ovládacího prvku.

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>Parametry

*č. PosRec*<br/>
Vyhrazeno.

*hwndParent*<br/>
Popisovač okna obsahující ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

## <a name="ccomcontrolbasefireviewchange"></a><a name="fireviewchange"></a>Ccomcontrolbase::FireViewChange

Volání této metody sdělit kontejneru překreslit ovládací prvek nebo upozornit registrované doporučit jímky, že zobrazení ovládacího prvku se změnil.

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je ovládací prvek aktivní (datový člen třídy ovládacího prvku [CComControlBase:::m_bInPlaceActive](#m_binplaceactive) je TRUE), upozorní kontejner, který chcete překreslit celý ovládací prvek. Pokud je ovládací prvek neaktivní, upozorní registrovaný ovládací prvek doporučit jímky (prostřednictvím datového člena třídy ovládacího prvku [CComControlBase::m_spAdviseSink)](#m_spadvisesink)že zobrazení ovládacího prvku se změnilo.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

## <a name="ccomcontrolbasegetambientappearance"></a><a name="getambientappearance"></a>Ccomcontrolbase::GetAmbientVzhled

Načte DISPID_AMBIENT_APPEARANCE, aktuální nastavení vzhledu ovládacího prvku: 0 pro ploché a 1 pro 3D.

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>Parametry

*nVzhled*<br/>
Objekt DISPID_AMBIENT_APPEARANCE.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

## <a name="ccomcontrolbasegetambientautoclip"></a><a name="getambientautoclip"></a>CComControlBase::GetAmbientAutoClip

Načte DISPID_AMBIENT_AUTOCLIP, příznak označující, zda kontejner podporuje automatické oříznutí oblasti zobrazení ovládacího prvku.

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>Parametry

*bAutomatický klip*<br/>
Objekt DISPID_AMBIENT_AUTOCLIP.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ccomcontrolbasegetambientbackcolor"></a><a name="getambientbackcolor"></a>Ccomcontrolbase::GetAmbientBackColor

Načte DISPID_AMBIENT_BACKCOLOR, barvu pozadí okolí pro všechny ovládací prvky definované kontejnerem.

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>Parametry

*Backcolor*<br/>
Objekt DISPID_AMBIENT_BACKCOLOR.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ccomcontrolbasegetambientcharset"></a><a name="getambientcharset"></a>Ccomcontrolbase::Getambientcharset

Načte DISPID_AMBIENT_CHARSET, okolní znakovou sadu pro všechny ovládací prvky, definované kontejneru.

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>Parametry

*bstrCharSet*<br/>
Ubytovací zařízení DISPID_AMBIENT_CHARSET.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="ccomcontrolbasegetambientcodepage"></a><a name="getambientcodepage"></a>CcomControlBase::GetAmbientCodePage

Načte DISPID_AMBIENT_CODEPAGE, okolní znakovou stránku pro všechny ovládací prvky, definované kontejneru.

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>Parametry

*ulCodePage*<br/>
Objekt DISPID_AMBIENT_CODEPAGE.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="ccomcontrolbasegetambientdisplayasdefault"></a><a name="getambientdisplayasdefault"></a>Ccomcontrolbase::GetambientDisplayAsVýchozí

Načte DISPID_AMBIENT_DISPLAYASDEFAULT, příznak, který je TRUE, pokud kontejner označil ovládací prvek na této stránce jako výchozí tlačítko, a proto by se ovládací prvek tlačítka měl kreslit sám s tlustším rámečkem.

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*bDisplayAsVýchozí*<br/>
Objekt DISPID_AMBIENT_DISPLAYASDEFAULT.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ccomcontrolbasegetambientdisplayname"></a><a name="getambientdisplayname"></a>CcomControlBase::GetambientDisplayName

Načte DISPID_AMBIENT_DISPLAYNAME, název kontejneru dodal ovládacímu prvku.

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>Parametry

*bstrDisplayName*<br/>
Objekt DISPID_AMBIENT_DISPLAYNAME.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ccomcontrolbasegetambientfont"></a><a name="getambientfont"></a>CcomControlBase::GetAmbientFont

Načte ukazatel na okolní `IFont` rozhraní kontejneru.

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>Parametry

*ppPísmo*<br/>
Ukazatel na okolní rozhraní [iFont](/windows/win32/api/ocidl/nn-ocidl-ifont) kontejneru.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je vlastnost NULL, ukazatel je NULL. Pokud ukazatel není NULL, volající musí uvolnit ukazatel.

## <a name="ccomcontrolbasegetambientfontdisp"></a><a name="getambientfontdisp"></a>CComControlBase::GetAmbientFontDisp

Načte ukazatel na okolí `IFontDisp` rozhraní odeslání kontejneru.

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parametry

*ppPísmo*<br/>
Ukazatel na okolní rozhraní [iFontDisp aplikace IFontDisp.](/windows/win32/api/ocidl/nn-ocidl-ifontdisp)

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Pokud je vlastnost NULL, ukazatel je NULL. Pokud ukazatel není NULL, volající musí uvolnit ukazatel.

## <a name="ccomcontrolbasegetambientforecolor"></a><a name="getambientforecolor"></a>CComControlBase::GetAmbientForeColor

Načte DISPID_AMBIENT_FORECOLOR, barvu okolí popředí pro všechny ovládací prvky definované kontejnerem.

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>Parametry

*Forecolor*<br/>
Nemovitost DISPID_AMBIENT_FORECOLOR.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ccomcontrolbasegetambientlocaleid"></a><a name="getambientlocaleid"></a>CComControlBase::GetAmbientLocaleID

Načte DISPID_AMBIENT_LOCALEID, identifikátor jazyka používaného kontejneru.

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>Parametry

*lcid*<br/>
Objekt DISPID_AMBIENT_LOCALEID.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Ovládací prvek můžete použít tento identifikátor přizpůsobit své uživatelské rozhraní do různých jazyků.

## <a name="ccomcontrolbasegetambientmessagereflect"></a><a name="getambientmessagereflect"></a>Ccomcontrolbase::GetAmbientMessageReflect

Načte DISPID_AMBIENT_MESSAGEREFLECT příznak označující, zda kontejner chce přijímat `WM_DRAWITEM`zprávy okna (například) jako události.

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>Parametry

*bMessageReflect*<br/>
Objekt DISPID_AMBIENT_MESSAGEREFLECT.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ccomcontrolbasegetambientpalette"></a><a name="getambientpalette"></a>Ccomcontrolbase::GetAmbientPalette

Načte DISPID_AMBIENT_PALETTE, slouží k přístupu k kontejneru HPALETTE.

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>Parametry

*hPaleta*<br/>
Nemovitost DISPID_AMBIENT_PALETTE.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ccomcontrolbasegetambientproperty"></a><a name="getambientproperty"></a>CcomControlBase::GetAmbientProperty

Načte vlastnost kontejneru určenou *dispid*.

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
Identifikátor vlastnosti kontejneru, která má být načtena.

*var*<br/>
Proměnná pro příjem vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Společnost ATL poskytla sadu pomocných funkcí pro načtení určitých vlastností, například [CComControlBase::GetAmbientBackColor](#getambientbackcolor). Není-li k dispozici vhodná metoda, použijte `GetAmbientProperty`.

## <a name="ccomcontrolbasegetambientrighttoleft"></a><a name="getambientrighttoleft"></a>Ccomcontrolbase::GetambientRightToLeft

Načte DISPID_AMBIENT_RIGHTTOLEFT, směr, ve kterém je obsah zobrazen kontejnerem.

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>Parametry

*bRightToLeft*<br/>
Nemovitost DISPID_AMBIENT_RIGHTTOLEFT. Nastavte hodnotu TRUE, pokud je obsah zobrazen zprava doleva, NEPRAVDA, pokud je zobrazen zleva doprava.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="ccomcontrolbasegetambientscaleunits"></a><a name="getambientscaleunits"></a>CcomControlBase::GetAmbientScaleUnits

Načte DISPID_AMBIENT_SCALEUNITS okolní jednotky kontejneru (například palce nebo centimetry) pro zobrazení popisků.

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>Parametry

*jednotky bstrScale*<br/>
Nemovitost DISPID_AMBIENT_SCALEUNITS.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ccomcontrolbasegetambientshowgrabhandles"></a><a name="getambientshowgrabhandles"></a>CComControlBase::GetAmbientShowGrabHandles

Načte DISPID_AMBIENT_SHOWGRABHANDLES, příznak označující, zda kontejner umožňuje ovládací prvek zobrazit úchyty pro sebe při aktivní.

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>Parametry

*bZobrazitGrabHandles*<br/>
Nemovitost DISPID_AMBIENT_SHOWGRABHANDLES.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ccomcontrolbasegetambientshowhatching"></a><a name="getambientshowhatching"></a>CComControlBase::GetAmbientShowHatching

Načte DISPID_AMBIENT_SHOWHATCHING, příznak označující, zda kontejner umožňuje ovládací prvek zobrazit sám se šrafovaným vzorem, když je aktivní uživatelské rozhraní ovládacího prvku.

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>Parametry

*bShowHatching*<br/>
Nemovitost DISPID_AMBIENT_SHOWHATCHING.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ccomcontrolbasegetambientsupportsmnemonics"></a><a name="getambientsupportsmnemonics"></a>CComControlBase::GetAmbientSupportsMnemonics

Načte DISPID_AMBIENT_SUPPORTSMNEMONICS příznak označující, zda kontejner podporuje mnemotechnické pomůcky klávesnice.

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>Parametry

*bPodporujeMnemonics*<br/>
Objekt DISPID_AMBIENT_SUPPORTSMNEMONICS.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ccomcontrolbasegetambienttextalign"></a><a name="getambienttextalign"></a>Ccomcontrolbase::GetAmbientTextAlign

Načte DISPID_AMBIENT_TEXTALIGN, zarovnání textu upřednostňované kontejnerem: 0 pro obecné zarovnání (čísla vpravo, text vlevo), 1 pro zarovnání vlevo, 2 pro zarovnání na střed a 3 pro pravé zarovnání.

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>Parametry

*nZarovnání textu*<br/>
Objekt DISPID_AMBIENT_TEXTALIGN.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ccomcontrolbasegetambienttoptobottom"></a><a name="getambienttoptobottom"></a>Ccomcontrolbase::GetambienttopToBottom

Načte DISPID_AMBIENT_TOPTOBOTTOM, směr, ve kterém je obsah zobrazen kontejnerem.

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>Parametry

*bTopToBottom*<br/>
Nemovitost DISPID_AMBIENT_TOPTOBOTTOM. Nastavte hodnotu TRUE, pokud je text zobrazen shora dolů, NEPRAVDA, pokud je zobrazen zdola nahoru.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="ccomcontrolbasegetambientuidead"></a><a name="getambientuidead"></a>Ccomcontrolbase::GetambientuiDead

Načte DISPID_AMBIENT_UIDEAD příznak označující, zda kontejner chce, aby ovládací prvek reagoval na akce uživatelského rozhraní.

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>Parametry

*bUIMrtvý*<br/>
Objekt DISPID_AMBIENT_UIDEAD.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Pokud TRUE, ovládací prvek by neměl reagovat. Tento příznak platí bez ohledu na příznak DISPID_AMBIENT_USERMODE. Viz [ccomcontrolbase::GetambientUserMode](#getambientusermode).

## <a name="ccomcontrolbasegetambientusermode"></a><a name="getambientusermode"></a>CcomControlBase::GetAmbientUserMode

Načte DISPID_AMBIENT_USERMODE příznak označující, zda je kontejner v režimu spuštění (TRUE) nebo v režimu návrhu (FALSE).

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>Parametry

*bRežim uživatele*<br/>
Objekt DISPID_AMBIENT_USERMODE.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ccomcontrolbasegetdirty"></a><a name="getdirty"></a>Ccomcontrolbase::GetDirty

Vrátí hodnotu datového člena `m_bRequiresSave`.

```
BOOL GetDirty();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu [m_bRequiresSave](#m_brequiressave)datového člena .

### <a name="remarks"></a>Poznámky

Tato hodnota je nastavena pomocí [CComControlBase::SetDirty](#setdirty).

## <a name="ccomcontrolbasegetzoominfo"></a><a name="getzoominfo"></a>Ccomcontrolbase::GetZoomInfo

Načte hodnoty x a y čitatela a jmenovatele faktoru přiblížení pro ovládací prvek aktivovaný pro úpravy na místě.

```cpp
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*Di*<br/>
Struktura, která bude obsahovat zoom faktoru čitatel a jmenovatel. Další informace naleznete [v tématu ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).

### <a name="remarks"></a>Poznámky

Faktor zvětšení je poměr přirozené velikosti ovládacího prvku v jeho aktuálním rozsahu.

## <a name="ccomcontrolbaseinplaceactivate"></a><a name="inplaceactivate"></a>Ccomcontrolbase::InplaceActivate

Způsobí, že ovládací prvek přechod z neaktivní ho stavu do libovolného stavu sloveso v *iVerb* označuje.

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>Parametry

*iSponož*<br/>
Hodnota označující akci, která má být provedena [iOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb).

*č. PosRect*<br/>
Ukazatel na pozici ovládacího prvku na místě.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Před aktivací tato metoda zkontroluje, zda má ovládací prvek klientský web, zkontroluje, kolik ovládacího prvku je viditelné, a získá umístění ovládacího prvku v nadřazeném okně. Po aktivaci ovládacího prvku tato metoda aktivuje uživatelské rozhraní ovládacího prvku a řekne kontejneru, aby ovládací prvek viditelný.

Tato metoda také `IOleInPlaceSite`načte , `IOleInPlaceSiteEx`nebo `IOleInPlaceSiteWindowless` ukazatel rozhraní pro ovládací prvek a uloží jej do datového člena třídy ovládacího prvku [CComControlBase::m_spInPlaceSite](#m_spinplacesite). Datové členy třídy ovládacího prvku [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase::m_bWndLess](#m_bwndless), [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)a [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) jsou podle potřeby nastaveny na hodnotu true.

## <a name="ccomcontrolbaseinternalgetsite"></a><a name="internalgetsite"></a>CComControlBase::InternalGetSite

Volání této metody k dotazu na server ovládacího prvku pro ukazatel na identifikované rozhraní.

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>Parametry

*riid řekl:*<br/>
IID ukazatele rozhraní, který by měl být vrácen v *ppUnkSite*.

*ppUnkSite*<br/>
Adresa proměnné ukazatele, která přijímá ukazatel rozhraní požadovaný v *riid*.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Pokud web podporuje rozhraní požadované v *riid*, ukazatel je vrácena pomocí *ppUnkSite*. V opačném případě je *hodnota ppUnkSite* nastavena na hodnotu NULL.

## <a name="ccomcontrolbasem_bautosize"></a><a name="m_bautosize"></a>CComControlBase::m_bAutoSize

Příznak označující ovládací prvek nemůže mít jinou velikost.

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>Poznámky

Tento příznak je `IOleObjectImpl::SetExtent` kontrolována a pokud TRUE, způsobí, že funkce vrátit E_FAIL.

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

Pokud přidáte možnost **Automatické velikosti** na kartě [Vlastnosti na skladě](../../atl/reference/stock-properties-atl-control-wizard.md) průvodce řízení atl, průvodce automaticky vytvoří tento datový člen ve třídě ovládacího prvku, vytvoří metody put a get pro vlastnost a podporuje [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) automaticky upozornit kontejner při změně vlastnosti.

## <a name="ccomcontrolbasem_bdrawfromnatural"></a><a name="m_bdrawfromnatural"></a>CComControlBase::m_bDrawFromNatural

Příznak `IDataObjectImpl::GetData` označující, `CComControlBase::GetZoomInfo` že a by `m_sizeNatural` měl `m_sizeExtent`nastavit velikost ovládacího prvku z spíše než z .

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_bdrawgetdatainhimetric"></a><a name="m_bdrawgetdatainhimetric"></a>CComControlBase::m_bDrawGetDataInHimetric

Příznak označující, že `IDataObjectImpl::GetData` by měl používat HIMETRIC jednotky a ne pixely při kreslení.

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>Poznámky

Každá logická jednotka HIMETRIC je 0,01 milimetru.

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_binplaceactive"></a><a name="m_binplaceactive"></a>CComControlBase::m_bInPlaceActive

Příznak označující, že ovládací prvek je aktivní na místě.

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>Poznámky

To znamená, že ovládací prvek je viditelný a jeho okno, pokud existuje, je viditelné, ale jeho nabídky a panely nástrojů nemusí být aktivní. Příznak `m_bUIActive` označuje, že je aktivní také uživatelské rozhraní ovládacího prvku, například nabídky.

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_binplacesiteex"></a><a name="m_binplacesiteex"></a>CComControlBase::m_bInPlaceSiteEx

Příznak označující kontejner `IOleInPlaceSiteEx` podporuje rozhraní a ovládací prvky OCX96, jako jsou ovládací prvky bez oken a bez blikání.

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

Datový člen `m_spInPlaceSite` odkazuje na [rozhraní IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)nebo [IOleInPlaceSiteSiteless,](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) v závislosti na hodnotě `m_bWndLess` a `m_bInPlaceSiteEx` příznaky. (Datový člen `m_bNegotiatedWnd` musí mít `m_spInPlaceSite` hodnotu TRUE, aby byl ukazatel platný.)

Pokud `m_bWndLess` je `m_bInPlaceSiteEx` FALSE a `m_spInPlaceSite` je `IOleInPlaceSiteEx` PRAVDA, je ukazatel rozhraní. Informace [o m_spInPlaceSite](#m_spinplacesite) v tabulce s relací mezi těmito třemi datovými členy naleznete v m_spInPlaceSite.

## <a name="ccomcontrolbasem_bnegotiatedwnd"></a><a name="m_bnegotiatedwnd"></a>CComControlBase::m_bNegotiatedWnd

Příznak označující, zda ovládací prvek vyjednal s kontejnerem o podpoře funkcí ovládacího prvku OCX96 (například ovládací prvky bez blikání a bez oken) a zda je ovládací prvek v okně nebo bez oken.

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

Příznak `m_bNegotiatedWnd` musí být TRUE, `m_spInPlaceSite` aby byl ukazatel platný.

## <a name="ccomcontrolbasem_brecomposeonresize"></a><a name="m_brecomposeonresize"></a>CComControlBase::m_bRecomposeOnResize

Příznak označující ovládací prvek chce změnit kompose jeho prezentace při kontejneru změní velikost zobrazení ovládacího prvku.

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

Tento příznak je kontrolován [iOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) a `SetExtent` pokud TRUE upozorní kontejner změny zobrazení. Pokud je tento příznak nastaven, OLEMISC_RECOMPOSEONRESIZE bit ve výčtu [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) by měla být také nastavena.

## <a name="ccomcontrolbasem_brequiressave"></a><a name="m_brequiressave"></a>CComControlBase::m_bRequiresSave

Příznak označující, že ovládací prvek byl od posledního uložení změněn.

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>Poznámky

Hodnotu `m_bRequiresSave` lze nastavit pomocí [CComControlBase::SetDirty](#setdirty) a načtena pomocí [CComControlBase::GetDirty](#getdirty).

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_bresizenatural"></a><a name="m_bresizenatural"></a>CComControlBase::m_bResizeNatural

Příznak označující ovládací prvek chce změnit velikost jeho přirozený rozsah (jeho neškálované fyzické velikosti) při kontejneru změní velikost zobrazení ovládacího prvku.

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>Poznámky

Tento příznak je `IOleObjectImpl::SetExtent` zkontrolován a pokud true, `SetExtent` velikost `m_sizeNatural`předaná do je přiřazena .

Velikost předaná do `SetExtent` `m_sizeExtent`je vždy přiřazena `m_bResizeNatural`, bez ohledu na hodnotu .

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_buiactive"></a><a name="m_buiactive"></a>CComControlBase::m_bUIActive

Příznak označující uživatelské rozhraní ovládacího prvku, například nabídky a panely nástrojů, je aktivní.

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>Poznámky

Příznak `m_bInPlaceActive` označuje, že ovládací prvek je aktivní, ale ne, že jeho uživatelské rozhraní je aktivní.

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_busingwindowrgn"></a><a name="m_busingwindowrgn"></a>CComControlBase::m_bUsingWindowRgn

Příznak označující ovládací prvek používá oblast okna dodaného kontejnerem.

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_bwasoncewindowless"></a><a name="m_bwasoncewindowless"></a>CComControlBase::m_bWasOnceWindowless

Příznak označující ovládací prvek byl bez oken, ale může nebo nemusí být bez oken nyní.

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_bwindowonly"></a><a name="m_bwindowonly"></a>CComControlBase::m_bWindowOnly

Příznak označující ovládací prvek by měl být v okně, i v případě, že kontejner podporuje ovládací prvky bez oken.

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_bwndless"></a><a name="m_bwndless"></a>CComControlBase::m_bWndLess

Příznak označující ovládací prvek je bez oken.

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

Datový člen `m_spInPlaceSite` odkazuje na [iOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)nebo [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) rozhraní, `m_bWndLess` v závislosti na hodnotě a [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex) příznaky. (Datový člen [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) musí být TRUE pro [CComControlBase::m_spInPlaceSite](#m_spinplacesite) ukazatel platný.)

Pokud `m_bWndLess` je `m_spInPlaceSite` TRUE, `IOleInPlaceSiteWindowless` je ukazatel rozhraní. Viz [CComControlBase::m_spInPlaceSite](#m_spinplacesite) pro tabulku zobrazující úplnou relaci mezi těmito datovými členy.

## <a name="ccomcontrolbasem_hwndcd"></a><a name="m_hwndcd"></a>CComControlBase::m_hWndCD

Obsahuje odkaz na popisovač okna přidružený k ovládacímu prvku.

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_nfreezeevents"></a><a name="m_nfreezeevents"></a>CComControlBase::m_nFreezeEvents

Počet, kolikrát kontejner zmrazil události (odmítl přijmout události) bez zasahující horečné události (přijetí událostí).

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_rcpos"></a><a name="m_rcpos"></a>CComControlBase::m_rcPos

Pozice v obrazových bodech ovládacího prvku, vyjádřené v souřadnicích kontejneru.

```
RECT m_rcPos;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_sizeextent"></a><a name="m_sizeextent"></a>CComControlBase::m_sizeExtent

Rozsah řízení v jednotkách HIMETRIC (každá jednotka je 0,01 milimetru) pro konkrétní displej.

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

Tato velikost je zmenšena displejem. Fyzická velikost ovládacího prvku `m_sizeNatural` je určena v datovém členu a je pevná.

Velikost můžete převést na obrazové body pomocí globální funkce [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

## <a name="ccomcontrolbasem_sizenatural"></a><a name="m_sizenatural"></a>CComControlBase::m_sizeNatural

Fyzikální velikost řízení v jednotkách HIMETRIC (každá jednotka je 0,01 milimetru).

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

Tato velikost je pevná, `m_sizeExtent` zatímco velikost v je měřítko podle displeje.

Velikost můžete převést na obrazové body pomocí globální funkce [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

## <a name="ccomcontrolbasem_spadvisesink"></a><a name="m_spadvisesink"></a>CComControlBase::m_spAdviseSink

Přímý ukazatel na poradní připojení na kontejneru [(kontejneru IAdviseSink).](/windows/win32/api/objidl/nn-objidl-iadvisesink)

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_spambientdispatch"></a><a name="m_spambientdispatch"></a>CComControlBase::m_spAmbientDispatch

Objekt, `CComDispatchDriver` který umožňuje načíst a nastavit vlastnosti `IDispatch` objektu prostřednictvím ukazatele.

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_spclientsite"></a><a name="m_spclientsite"></a>CComControlBase::m_spClientSite

Ukazatel na klientské lokality ovládacího prvku v rámci kontejneru.

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

## <a name="ccomcontrolbasem_spdataadviseholder"></a><a name="m_spdataadviseholder"></a>CComControlBase::m_spDataAdviseHolder

Poskytuje standardní prostředky pro uložení informačních připojení mezi datovými objekty a poradenství jímky.

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

Datový objekt je ovládací prvek, který může přenášet data a který implementuje [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject), jehož metody určují formát a přenosové médium dat.

Rozhraní `m_spDataAdviseHolder` implementuje metody [IDataObject::DAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) a [IDataObject::DUnadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) pro vytvoření a odstranění informačních připojení ke kontejneru. Kontejner ovládacího prvku musí implementovat přepínač jímky podporou rozhraní [IAdviseSink.](/windows/win32/api/objidl/nn-objidl-iadvisesink)

## <a name="ccomcontrolbasem_spinplacesite"></a><a name="m_spinplacesite"></a>CComControlBase::m_spInPlaceSite

Ukazatel na [kontejneru IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)nebo [IOleInPlaceSiteSitebez](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) ukazatele rozhraní.

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

Ukazatel `m_spInPlaceSite` je platný pouze v případě, [že příznak m_bNegotiatedWnd](#m_bnegotiatedwnd) je TRUE.

Následující tabulka ukazuje, `m_spInPlaceSite` jak typ ukazatele závisí na [m_bWndLess](#m_bwndless) a [m_bInPlaceSiteEx](#m_binplacesiteex) příznaky datových členů:

|typ m_spInPlaceSite|m_bWndLess hodnota|m_bInPlaceSiteEx hodnota|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|TRUE|PRAVDA nebo NEPRAVDA|
|`IOleInPlaceSiteEx`|FALSE|TRUE|
|`IOleInPlaceSite`|FALSE|FALSE|

## <a name="ccomcontrolbasem_spoleadviseholder"></a><a name="m_spoleadviseholder"></a>CComControlBase::m_spOleAdviseHolder

Poskytuje standardní implementaci způsob, jak držet poradní připojení.

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Chcete-li použít tento datový člen v rámci třídy ovládacího prvku, musíte deklarovat jako datový člen ve vaší třídě ovládacího prvku. Vaše třída ovládacího prvku nezdědí tento datový člen ze základní třídy, protože je deklarována v rámci unie v základní třídě.

Rozhraní `m_spOleAdviseHolder` implementuje [metody IOleObject::Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) a [IOleObject::Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) pro vytvoření a odstranění informačních připojení ke kontejneru. Kontejner ovládacího prvku musí implementovat přepínač jímky podporou rozhraní [IAdviseSink.](/windows/win32/api/objidl/nn-objidl-iadvisesink)

## <a name="ccomcontrolbaseondraw"></a><a name="ondraw"></a>Ccomcontrolbase::Ondraw

Přepsat tuto metodu k nakreslení ovládacího prvku.

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*Di*<br/>
Odkaz na [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) strukturu, která obsahuje informace o výkresu, jako je například aspekt kreslení, hranice ovládacího prvku a to, zda je výkres optimalizován nebo ne.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Výchozí `OnDraw` odstraní nebo obnoví kontext zařízení nebo neprovede žádné, v závislosti na příznaky nastavené v [CComControlBase::OnDrawAdvanced](#ondrawadvanced).

Metoda `OnDraw` je automaticky přidána do třídy ovládacího prvku při vytváření ovládacího prvku pomocí Průvodce řízením ATL. Výchozí nastavení `OnDraw` průvodce nakreslí obdélník s popiskem "ATL 8.0".

### <a name="example"></a>Příklad

Viz příklad [ccomcontrolbase::GetAmbientAppearance](#getambientappearance).

## <a name="ccomcontrolbaseondrawadvanced"></a><a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced

Výchozí `OnDrawAdvanced` připraví normalizované zařízení kontextu pro kreslení, pak volá `OnDraw` metodu třídy ovládacího prvku.

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*Di*<br/>
Odkaz na [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) strukturu, která obsahuje informace o výkresu, jako je například aspekt kreslení, hranice ovládacího prvku a to, zda je výkres optimalizován nebo ne.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu, pokud chcete přijmout kontext zařízení předaný kontejneru bez normalizace.

Další podrobnosti naleznete v [tématu CComControlBase::OnDraw.](#ondraw)

## <a name="ccomcontrolbaseonkillfocus"></a><a name="onkillfocus"></a>Ccomcontrolbase::OnKillFocus

Zkontroluje, zda je ovládací prvek aktivní na místě a má platný řídicí web, pak informuje kontejner, že ovládací prvek ztratil fokus.

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Vyhrazeno.

*wParam*<br/>
Vyhrazeno.

*Lparam*<br/>
Vyhrazeno.

*bManipulováno*<br/>
Příznak, který označuje, zda byla zpráva okna úspěšně zpracována. Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí 1.

## <a name="ccomcontrolbaseonmouseactivate"></a><a name="onmouseactivate"></a>Ccomcontrolbase::OnMouseActivate

Zkontroluje, zda je uživatelské rozhraní v uživatelském režimu, a poté aktivuje ovládací prvek.

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Vyhrazeno.

*wParam*<br/>
Vyhrazeno.

*Lparam*<br/>
Vyhrazeno.

*bManipulováno*<br/>
Příznak, který označuje, zda byla zpráva okna úspěšně zpracována. Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí 1.

## <a name="ccomcontrolbaseonpaint"></a><a name="onpaint"></a>Ccomcontrolbase::OnPaint

Připraví kontejner pro malování, získá klientskou oblast ovládacího prvku a `OnDrawAdvanced` pak zavolá metodu třídy ovládacího prvku.

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Vyhrazeno.

*wParam*<br/>
Existující HDC.

*Lparam*<br/>
Vyhrazeno.

*lVýsledek*<br/>
Vyhrazeno.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí nulu.

### <a name="remarks"></a>Poznámky

Pokud *wParam* není `OnPaint` NULL, předpokládá, že obsahuje platný HDC a používá jej místo [CComControlBase::m_hWndCD](#m_hwndcd).

## <a name="ccomcontrolbaseonsetfocus"></a><a name="onsetfocus"></a>Ccomcontrolbase::OnSetFocus

Zkontroluje, zda je ovládací prvek aktivní na místě a má platné řídicí místo, pak informuje kontejner, na který ovládací prvek získal fokus.

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Vyhrazeno.

*wParam*<br/>
Vyhrazeno.

*Lparam*<br/>
Vyhrazeno.

*bManipulováno*<br/>
Příznak, který označuje, zda byla zpráva okna úspěšně zpracována. Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí 1.

### <a name="remarks"></a>Poznámky

Odešle oznámení do kontejneru, že ovládací prvek obdržel fokus.

## <a name="ccomcontrolbasepretranslateaccelerator"></a><a name="pretranslateaccelerator"></a>CComControlBase::PreTranslateAccelerator

Přepsat tuto metodu poskytnout vlastní obslužné rutiny akcelerátoru klávesnice.

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Vyhrazeno.

*hRet*<br/>
Vyhrazeno.

### <a name="return-value"></a>Návratová hodnota

Ve výchozím nastavení vrátí hodnotu NEPRAVDA.

## <a name="ccomcontrolbasesendonclose"></a><a name="sendonclose"></a>Ccomcontrolbase::SendOnclose

Upozorní všechny poradní propady registrované u držitele advise, že ovládací prvek byl uzavřen.

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Odešle oznámení, že ovládací prvek uzavřel své poradní propady.

## <a name="ccomcontrolbasesendondatachange"></a><a name="sendondatachange"></a>CcomControlBase::SendOnDataChange

Upozorní všechny poradní propady registrované u držitele advise, že se změnila data ovládacího prvku.

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>Parametry

*advf*<br/>
Poradit příznaky, které určují, jak se provádí volání [IAdviseSink::OnDataChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange) je provedena. Hodnoty jsou z výčtu [ADVF.](/windows/win32/api/objidl/ne-objidl-advf)

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="ccomcontrolbasesendonrename"></a><a name="sendonrename"></a>CComControlBase::SendOnRename

Upozorní všechny poradní jímky registrované u držitele advise, že ovládací prvek má nový zástupný název.

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>Parametry

*Pmk*<br/>
Ukazatel na nový zástupné název ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Odešle oznámení, že zástupný název ovládacího prvku byl změněn.

## <a name="ccomcontrolbasesendonsave"></a><a name="sendonsave"></a>Ccomcontrolbase::SendOnSave

Upozorní všechny poradní jímky registrované u držitele advise, že ovládací prvek byl uložen.

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Odešle oznámení, že ovládací prvek právě uložil svá data.

## <a name="ccomcontrolbasesendonviewchange"></a><a name="sendonviewchange"></a>Ccomcontrolbase::SendOnViewChange

Upozorní všechny registrované poradní propady, že zobrazení ovládacího prvku se změnilo.

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>Parametry

*dwAspect*<br/>
Aspekt nebo zobrazení ovládacího prvku.

*Lindex*<br/>
Část zobrazení, která se změnila. Pouze -1 je platný.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

`SendOnViewChange`volání [IAdviseSink::OnViewChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange). Jedinou hodnotou *lindex* aktuálně podporována je -1, což znamená, že celý pohled je zajímavé.

## <a name="ccomcontrolbasesetcontrolfocus"></a><a name="setcontrolfocus"></a>CComControlBase::SetControlFocus

Nastaví nebo odebere fokus klávesnice na ovládací prvek nebo z ovládacího prvku.

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>Parametry

*bChyť*<br/>
Pokud true, nastaví fokus klávesnice na ovládací prvek volání. Pokud false, odebere fokus klávesnice z ovládacího prvku volání, za předpokladu, že má fokus.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud se ovládacímu prvku úspěšně zosune fokus; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pro ovládací prvek s okny se volá funkce Rozhraní API systému Windows [SetFocus.](/windows/win32/api/winuser/nf-winuser-setfocus) Pro ovládací prvek bez oken [iOleInPlaceSiteSiteless::SetFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) se nazývá. Prostřednictvím tohoto volání ovládací prvek bez oken získá fokus klávesnice a může reagovat na zprávy okna.

## <a name="ccomcontrolbasesetdirty"></a><a name="setdirty"></a>CComControlBase::SetDirty

Nastaví datový `m_bRequiresSave` člen na hodnotu v *bDirty*.

```cpp
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*bDirty*<br/>
Hodnota datového člena [CComControlBase::m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Poznámky

`SetDirty(TRUE)`by měl být volán příznak, že ovládací prvek se změnil od posledního uložení. Hodnota `m_bRequiresSave` je načtena pomocí [CComControlBase::GetDirty](#getdirty).

## <a name="see-also"></a>Viz také

[Třída CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
