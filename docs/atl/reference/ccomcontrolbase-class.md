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
ms.openlocfilehash: def8334cf0ed9b6b2ee821e1e0f1a717d90f2163
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694579"
---
# <a name="ccomcontrolbase-class"></a>CComControlBase – třída

Tato třída poskytuje metody pro vytváření a správu ATL – ovládací prvky.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|Přepsat, pokud vaše `m_nAppearance` uloženou vlastnost není typu **krátký**.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|Konstruktor|
|[CComControlBase –:: ~ CComControlBase –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Kontroluje, zda *iVerb* parametr používané `IOleObjectImpl::DoVerb` buď aktivuje ovládacího prvku uživatelského rozhraní (*iVerb* OLEIVERB_UIACTIVATE rovná se), definuje akce provedená v případě, že uživatel dvakrát klikne ovládací prvek (*iVerb* OLEIVERB_PRIMARY rovná se), zobrazí ovládací prvek (*iVerb* OLEIVERB_SHOW rovná se), nebo aktivuje ovládací prvek (*iVerb* rovná OLEIVERB _INPLACEACTIVATE).|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Kontroluje, zda *iVerb* parametr používané `IOleObjectImpl::DoVerb` způsobí, že ovládacího prvku uživatelského rozhraní k aktivaci a vrátí hodnotu TRUE.|
|[CComControlBase::DoVerbProperties](#doverbproperties)|Zobrazí stránky vlastností ovládacího prvku.|
|[CComControlBase::FireViewChange](#fireviewchange)|Volání této metody pro překreslení ovládacího prvku kontejneru, nebo upozornit jímky registrované doporučení, které došlo ke změně zobrazení ovládacího prvku.|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|Načte DISPID_AMBIENT_APPEARANCE, aktuální nastavení pro ovládací prvek vzhled: 0 pro paušální a 1 pro 3D.|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Načte DISPID_AMBIENT_AUTOCLIP příznak označující, zda kontejner podporuje automatické výstřižek oblasti ovládacího prvku zobrazení.|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Načte DISPID_AMBIENT_BACKCOLOR, barva okolí pozadí pro všechny ovládací prvky určené kontejneru.|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Načte DISPID_AMBIENT_CHARSET okolí znakovou sadu pro všechny ovládací prvky určené kontejneru.|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Načte DISPID_AMBIENT_CODEPAGE okolí znakovou sadu pro všechny ovládací prvky určené kontejneru.|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Načte DISPID_AMBIENT_DISPLAYASDEFAULT příznak, který je TRUE, pokud označil kontejneru ovládacího prvku na tento web bude výchozí tlačítko, a proto ovládací prvek tlačítko vykreslovat samotného objektu silnější Frame.|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Načte DISPID_AMBIENT_DISPLAYNAME, název, který má zadaný kontejner do ovládacího prvku.|
|[CComControlBase::GetAmbientFont](#getambientfont)|Načte ukazatel na kontejneru v okolí `IFont` rozhraní.|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Načte ukazatel na kontejneru v okolí `IFontDisp` rozhraní odbavení.|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Načte DISPID_AMBIENT_FORECOLOR barvu popředí okolí pro všechny ovládací prvky určené kontejneru.|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Načte DISPID_AMBIENT_LOCALEID identifikátor jazyk používaný kontejnerem.|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Načte DISPID_AMBIENT_MESSAGEREFLECT příznak označující, jestli konkrétní kontejner potřebuje pro příjem zpráv oken (například WM_DRAWITEM) jako události.|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Načte DISPID_AMBIENT_PALETTE, používá pro přístup k HPALETTE kontejneru.|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Získá kontejner vlastnost určenou *id*.|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|Načte DISPID_AMBIENT_RIGHTTOLEFT, směr, ve kterém se zobrazí obsah kontejnerem.|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Načte DISPID_AMBIENT_SCALEUNITS kontejneru okolí jednotky (například palce nebo cm) pro popisování zobrazí.|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Načte DISPID_AMBIENT_SHOWGRABHANDLES příznak označující, zda kontejner umožňuje ovládací prvek pro zobrazení zobrazily úchyty sama za sebe, pokud je aktivní.|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Načte DISPID_AMBIENT_SHOWHATCHING příznak označující, zda kontejner umožňuje ovládacího prvku zobrazení samotného šrafované vzorem při aktivním uživatelského rozhraní.|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Načte DISPID_AMBIENT_SUPPORTSMNEMONICS příznak označující, zda kontejner podporuje klávesové zkratky klávesnice.|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Načte DISPID_AMBIENT_TEXTALIGN, preferují kontejneru zarovnání textu: 0 pro obecné zarovnání (vlevo textu zprava, čísla), 1 pro zarovnání doleva, pro zarovnání na střed 2 a 3 pro zarovnání doprava.|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Načte DISPID_AMBIENT_TOPTOBOTTOM, směr, ve kterém se zobrazí obsah kontejnerem.|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|Načte DISPID_AMBIENT_UIDEAD příznak označující, jestli konkrétní kontejner potřebuje ovládací prvek reagovat na akce uživatelského rozhraní.|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Načte DISPID_AMBIENT_USERMODE příznak označující, jestli je kontejner v režimu běhu (pravda) nebo v režimu návrhu (FALSE).|
|[CComControlBase::GetDirty](#getdirty)|Vrací hodnotu datového členu `m_bRequiresSave`.|
|[CComControlBase::GetZoomInfo](#getzoominfo)|Načte x a y hodnoty čitatelem a jmenovatelem na faktor zvětšování pro ovládací prvek aktivuje pro místní úpravy.|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|Způsobí, že ovládací prvek na přechod ze stavu aktivní na cokoli, co stav operací v *iVerb* označuje.|
|[CComControlBase::InternalGetSite](#internalgetsite)|Volejte tuto metodu za účelem zjištění serveru ovládací prvek pro ukazatel rozhraní identifikovaný.|
|[CComControlBase::OnDraw](#ondraw)|Potlačí tuto metodu za účelem vykreslení ovládacího prvku.|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|Výchozí hodnota `OnDrawAdvanced` připraví normalizovaný kontext zařízení pro kreslení a pak volá třídy vašeho ovládacího prvku `OnDraw` metody.|
|[CComControlBase::OnKillFocus](#onkillfocus)|Ověří, že ovládací prvek je aktivní místní a má platný ovládací prvek a potom kontejneru informuje, že ovládací prvek ztratil fokus.|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Kontroluje, zda je v uživatelském režimu uživatelského rozhraní, a aktivuje ovládací prvek.|
|[CComControlBase::OnPaint](#onpaint)|Připraví kontejner pro kreslení, získá klientské oblasti ovládacího prvku a pak volá třídy ovládacího prvku `OnDraw` metody.|
|[CComControlBase::OnSetFocus](#onsetfocus)|Kontroluje, že ovládací prvek je aktivní místní a má platný ovládací prvek a potom informuje kontejneru ovládacího prvku získal fokus.|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Přepsáním této metody můžete zadat vlastní klávesnice obslužné rutiny akcelerátoru.|
|[CComControlBase::SendOnClose](#sendonclose)|Oznámí všechny advisory jímky zaregistrovaného doporučení držitele, že ovládací prvek byla uzavřena.|
|[CComControlBase::SendOnDataChange](#sendondatachange)|Oznámí všechny advisory zaregistrovaného držitel doporučení, které se změnily ovládací prvek dat jímky.|
|[CComControlBase::SendOnRename](#sendonrename)|Oznámí všechny advisory jímky zaregistrovaného doporučení držitele, že je ovládací prvek monikeru nové.|
|[CComControlBase::SendOnSave](#sendonsave)|Oznámí všechny advisory jímky zaregistrovaného držitel doporučení, která byla uložena ovládacího prvku.|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Upozorní, že všechny registrované advisory jímky, které došlo ke změně zobrazení ovládacího prvku.|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Nastaví nebo odebere fokusu klávesnice do nebo z ovládacího prvku.|
|[CComControlBase::SetDirty](#setdirty)|Nastaví datový člen `m_bRequiresSave` s hodnotou v *bDirty*.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|Příznak označující, že ovládací prvek nemůže být libovolné velikosti.|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Příznak označující, že `IDataObjectImpl::GetData` a `CComControlBase::GetZoomInfo` by měl nastavit velikost ovládacího prvku z `m_sizeNatural` spíše než z `m_sizeExtent`.|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Příznak označující, že `IDataObjectImpl::GetData` by měl používat v jednotkách HIMETRIC a ne pixelů při kreslení.|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Příznak označující, že ovládací prvek je na místě aktivní.|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Příznak označující, které podporuje kontejneru `IOleInPlaceSiteEx` rozhraní a OCX96 řídí funkce, jako je například ovládací prvky bez oken a blikání.|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Příznak označující, zda má ovládací prvek vyjedná s kontejnerem týkající se podpory funkce řízení OCX96 (jako je například ovládací prvky bez blikání a bez oken) a určuje, zda je ovládací prvek oddílové nebo bez oken.|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Příznak označující, že chce, aby se ovládací prvek Chcete-li jeho prezentaci při změně velikosti zobrazení ovládacího prvku kontejneru.|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Příznak označující, že ovládací prvek změnila od posledního uložení.|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Příznak označující, ke změně velikosti jeho fyzické rozsah (jeho bez měřítka fyzická velikost) chce, aby ovládací prvek při změně velikosti zobrazení ovládacího prvku kontejneru.|
|[CComControlBase::m_bUIActive](#m_buiactive)|Příznak označující, ovládacího prvku uživatelského rozhraní, jako je například nabídek a panelů nástrojů, je aktivní.|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Příznak označující, že ovládací prvek používá oblast okna zadaný kontejner.|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Příznak označující, ovládací prvek bez oken, se ale může nebo nemusí být nyní bez oken.|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|Příznak označující, že ovládací prvek by měl být oddílové, i v případě, že kontejner podporuje ovládací prvky bez oken.|
|[CComControlBase::m_bWndLess](#m_bwndless)|Příznak označující, že je ovládací prvek bez oken.|
|[CComControlBase::m_hWndCD](#m_hwndcd)|Obsahuje odkaz na popisovač okna přidružený k ovládacímu prvku.|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Počet, kolikrát kontejneru je zmrazen události (odmítl akceptovat události) bez použité odblokovat událostí (přijetí události).|
|[CComControlBase::m_rcPos](#m_rcpos)|Pozice ovládacího prvku, vyjádřená v souřadnicích kontejneru v pixelech.|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|Rozsah ovládacího prvku v jednotkách HIMETRIC (každá jednotka je 0,01 milimetrech) pro konkrétní zobrazení.|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|Fyzická velikost ovládacího prvku v jednotkách HIMETRIC (každá jednotka je 0,01 milimetrech).|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Přímý ukazatel na poradce připojení ke kontejneru (kontejneru [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)).|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|A `CComDispatchDriver` objekt, který umožňuje načtení a nastavení vlastností kontejneru prostřednictvím `IDispatch` ukazatele.|
|[CComControlBase::m_spClientSite](#m_spclientsite)|Ukazatel na lokality klienta ovládacího prvku v rámci kontejneru.|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Poskytuje že standardní znamená, že pro uložení advisory připojení mezi datovými objekty dokáží jímky.|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Ukazatel na kontejneru [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex), nebo [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless) ukazatel rozhraní.|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Poskytuje standardní implementace způsob uložení advisory připojení.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro vytváření a správu ATL – ovládací prvky. [Ccomcontrol – třída](../../atl/reference/ccomcontrol-class.md) je odvozena z `CComControlBase`. Když vytvoříte standardního ovládacího prvku nebo DHTML ovládacího prvku pomocí Průvodce ovládacími prvky ATL, průvodce automaticky odvodit třídu z `CComControlBase`.

Další informace o vytvoření ovládacího prvku, naleznete v tématu [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md). Další informace o Průvodce projektem ATL naleznete v článku [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="appearancetype"></a>  CComControlBase::AppearanceType

Přepsat, pokud vaše `m_nAppearance` uloženou vlastnost není typu **krátký**.

```
typedef short AppearanceType;
```

### <a name="remarks"></a>Poznámky

Průvodce ovládacími prvky ATL přidá `m_nAppearance` vlastnost typu short zásobníku. Přepsat `AppearanceType` Pokud použijete jiný datový typ.

##  <a name="ccomcontrolbase"></a>  CComControlBase::CComControlBase

Konstruktor

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Popisovač okna přidružený k ovládacímu prvku.

### <a name="remarks"></a>Poznámky

Inicializuje velikost ovládacího prvku na 5080 X 5080 jednotkách HIMETRIC (2 "X 2") a inicializuje `CComControlBase` hodnoty datových členů na hodnotu NULL nebo FALSE.

##  <a name="dtor"></a>  CComControlBase –:: ~ CComControlBase –

Destruktor.

```
~CComControlBase();
```

### <a name="remarks"></a>Poznámky

Pokud je ovládací prvek oddílové, `~CComControlBase` zničí voláním [destroywindow –](/windows/desktop/api/winuser/nf-winuser-destroywindow).

##  <a name="controlqueryinterface"></a>  CComControlBase::ControlQueryInterface

Načte ukazatel na požadované rozhraní.

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>Parametry

*identifikátor IID*<br/>
Identifikátor GUID se požadované rozhraní.

*ppv*<br/>
Ukazatel na ukazatel rozhraní, který je identifikován *iid*, nebo hodnota NULL, pokud se nenajde rozhraní.

### <a name="remarks"></a>Poznámky

zpracovává pouze v tabulce mapy modelu COM rozhraní.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

##  <a name="doesverbactivate"></a>  CComControlBase::DoesVerbActivate

Kontroluje, zda *iVerb* parametr používané `IOleObjectImpl::DoVerb` buď aktivuje ovládacího prvku uživatelského rozhraní (*iVerb* OLEIVERB_UIACTIVATE rovná se), definuje akce provedená v případě, že uživatel dvakrát klikne ovládací prvek (*iVerb* OLEIVERB_PRIMARY rovná se), zobrazí ovládací prvek (*iVerb* OLEIVERB_SHOW rovná se), nebo aktivuje ovládací prvek (*iVerb* rovná OLEIVERB _INPLACEACTIVATE).

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Hodnota udává akci prováděnou `DoVerb`.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud *iVerb* rovná OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW nebo OLEIVERB_INPLACEACTIVATE; v opačném případě vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Můžete přepsat tuto metodu za účelem definování vlastní příkaz aktivace.

##  <a name="doesverbuiactivate"></a>  CComControlBase::DoesVerbUIActivate

Kontroluje, zda *iVerb* parametr používané `IOleObjectImpl::DoVerb` způsobí, že ovládacího prvku uživatelského rozhraní k aktivaci a vrátí hodnotu TRUE.

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Hodnota udává akci prováděnou `DoVerb`.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud *iVerb* rovná OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW nebo OLEIVERB_INPLACEACTIVATE. Jinak metoda vrátí hodnotu FALSE.

##  <a name="doverbproperties"></a>  CComControlBase::DoVerbProperties

Zobrazí stránky vlastností ovládacího prvku.

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
Vyhrazená.

*hwndParent*<br/>
Popisovač okna obsahující ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

##  <a name="fireviewchange"></a>  CComControlBase::FireViewChange

Volání této metody pro překreslení ovládacího prvku kontejneru, nebo upozornit jímky registrované doporučení, které došlo ke změně zobrazení ovládacího prvku.

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je aktivní ovládací prvek (datový člen třídy ovládacího prvku [CComControlBase::m_bInPlaceActive](#m_binplaceactive) je TRUE), upozorní kontejneru, že chcete ho překreslit celý ovládací prvek. Pokud ovládací prvek je neaktivní, upozorní ovládací prvek zaregistrované dokáží jímky (prostřednictvím datový člen třídy ovládacího prvku [CComControlBase::m_spAdviseSink](#m_spadvisesink)), ke které došlo ke změně zobrazení ovládacího prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

##  <a name="getambientappearance"></a>  CComControlBase::GetAmbientAppearance

Načte DISPID_AMBIENT_APPEARANCE, aktuální nastavení pro ovládací prvek vzhled: 0 pro paušální a 1 pro 3D.

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>Parametry

*nAppearance*<br/>
Vlastnost DISPID_AMBIENT_APPEARANCE.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

##  <a name="getambientautoclip"></a>  CComControlBase::GetAmbientAutoClip

Načte DISPID_AMBIENT_AUTOCLIP příznak označující, zda kontejner podporuje automatické výstřižek oblasti ovládacího prvku zobrazení.

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>Parametry

*bAutoClip*<br/>
Vlastnost DISPID_AMBIENT_AUTOCLIP.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="getambientbackcolor"></a>  CComControlBase::GetAmbientBackColor

Načte DISPID_AMBIENT_BACKCOLOR, barva okolí pozadí pro všechny ovládací prvky určené kontejneru.

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>Parametry

*Barva pozadí*<br/>
Vlastnost DISPID_AMBIENT_BACKCOLOR.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="getambientcharset"></a>  CComControlBase::GetAmbientCharSet

Načte DISPID_AMBIENT_CHARSET okolí znakovou sadu pro všechny ovládací prvky určené kontejneru.

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>Parametry

*bstrCharSet*<br/>
Vlastnost DISPID_AMBIENT_CHARSET.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="getambientcodepage"></a>  CComControlBase::GetAmbientCodePage

Načte DISPID_AMBIENT_CODEPAGE okolí znakovou stránku pro všechny ovládací prvky určené kontejneru.

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>Parametry

*ulCodePage*<br/>
Vlastnost DISPID_AMBIENT_CODEPAGE.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="getambientdisplayasdefault"></a>  CComControlBase::GetAmbientDisplayAsDefault

Načte DISPID_AMBIENT_DISPLAYASDEFAULT příznak, který je TRUE, pokud označil kontejneru ovládacího prvku na tento web bude výchozí tlačítko, a proto ovládací prvek tlačítko vykreslovat samotného objektu silnější Frame.

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*bDisplayAsDefault*<br/>
Vlastnost DISPID_AMBIENT_DISPLAYASDEFAULT.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="getambientdisplayname"></a>  CComControlBase::GetAmbientDisplayName

Načte DISPID_AMBIENT_DISPLAYNAME, název, který má zadaný kontejner do ovládacího prvku.

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>Parametry

*bstrDisplayName*<br/>
Vlastnost DISPID_AMBIENT_DISPLAYNAME.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="getambientfont"></a>  CComControlBase::GetAmbientFont

Načte ukazatel na kontejneru v okolí `IFont` rozhraní.

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont*<br/>
Ukazatele do kontejneru v okolí [IFont](/windows/desktop/api/ocidl/nn-ocidl-ifont) rozhraní.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je vlastnost nastavena na hodnotu NULL, je ukazatel NULL. Pokud ukazatel není NULL, volající musí uvolnit ukazatel.

##  <a name="getambientfontdisp"></a>  CComControlBase::GetAmbientFontDisp

Načte ukazatel na kontejneru v okolí `IFontDisp` rozhraní odbavení.

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont*<br/>
Ukazatele do kontejneru v okolí [IFontDisp](https://msdn.microsoft.com/library/windows/desktop/ms692695) rozhraní odbavení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Pokud je vlastnost nastavena na hodnotu NULL, je ukazatel NULL. Pokud ukazatel není NULL, volající musí uvolnit ukazatel.

##  <a name="getambientforecolor"></a>  CComControlBase::GetAmbientForeColor

Načte DISPID_AMBIENT_FORECOLOR barvu popředí okolí pro všechny ovládací prvky určené kontejneru.

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>Parametry

*Barva popředí*<br/>
Vlastnost DISPID_AMBIENT_FORECOLOR.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="getambientlocaleid"></a>  CComControlBase::GetAmbientLocaleID

Načte DISPID_AMBIENT_LOCALEID identifikátor jazyk používaný kontejnerem.

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>Parametry

*lcid*<br/>
Vlastnost DISPID_AMBIENT_LOCALEID.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Ovládací prvek můžete používat tento identifikátor pro přizpůsobení uživatelského rozhraní pro různé jazyky.

##  <a name="getambientmessagereflect"></a>  CComControlBase::GetAmbientMessageReflect

Načte DISPID_AMBIENT_MESSAGEREFLECT příznak označující, jestli konkrétní kontejner potřebuje pro příjem zpráv oken (například `WM_DRAWITEM`) jako události.

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>Parametry

*bMessageReflect*<br/>
Vlastnost DISPID_AMBIENT_MESSAGEREFLECT.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="getambientpalette"></a>  CComControlBase::GetAmbientPalette

Načte DISPID_AMBIENT_PALETTE, používá pro přístup k HPALETTE kontejneru.

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>Parametry

*hPalette*<br/>
Vlastnost DISPID_AMBIENT_PALETTE.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="getambientproperty"></a>  CComControlBase::GetAmbientProperty

Získá kontejner vlastnost určenou *dispid*.

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>Parametry

*identifikátor DISPID*<br/>
Identifikátor vlastnosti kontejneru se má načíst.

*var*<br/>
Proměnné k získání vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Knihovna ATL poskytuje sadu pomocných funkcí pro načtení určité vlastnosti, například [CComControlBase::GetAmbientBackColor](#getambientbackcolor). Pokud není k dispozici žádná vhodná metoda, pomocí `GetAmbientProperty`.

##  <a name="getambientrighttoleft"></a>  CComControlBase::GetAmbientRightToLeft

Načte DISPID_AMBIENT_RIGHTTOLEFT, směr, ve kterém se zobrazí obsah kontejnerem.

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>Parametry

*bRightToLeft*<br/>
Vlastnost DISPID_AMBIENT_RIGHTTOLEFT. Nastavte na hodnotu TRUE, pokud obsah se zobrazí zprava doleva, FALSE, pokud se zobrazí zleva doprava.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="getambientscaleunits"></a>  CComControlBase::GetAmbientScaleUnits

Načte DISPID_AMBIENT_SCALEUNITS kontejneru okolí jednotky (například palce nebo cm) pro popisování zobrazí.

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>Parametry

*bstrScaleUnits*<br/>
Vlastnost DISPID_AMBIENT_SCALEUNITS.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="getambientshowgrabhandles"></a>  CComControlBase::GetAmbientShowGrabHandles

Načte DISPID_AMBIENT_SHOWGRABHANDLES příznak označující, zda kontejner umožňuje ovládací prvek pro zobrazení zobrazily úchyty sama za sebe, pokud je aktivní.

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>Parametry

*bShowGrabHandles*<br/>
Vlastnost DISPID_AMBIENT_SHOWGRABHANDLES.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="getambientshowhatching"></a>  CComControlBase::GetAmbientShowHatching

Načte DISPID_AMBIENT_SHOWHATCHING příznak označující, zda kontejner umožňuje ovládacího prvku zobrazení samotného šrafované vzorem při aktivním ovládacího prvku uživatelského rozhraní.

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>Parametry

*bShowHatching*<br/>
Vlastnost DISPID_AMBIENT_SHOWHATCHING.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="getambientsupportsmnemonics"></a>  CComControlBase::GetAmbientSupportsMnemonics

Načte DISPID_AMBIENT_SUPPORTSMNEMONICS příznak označující, zda kontejner podporuje klávesové zkratky klávesnice.

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>Parametry

*bSupportsMnemonics*<br/>
Vlastnost DISPID_AMBIENT_SUPPORTSMNEMONICS.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="getambienttextalign"></a>  CComControlBase::GetAmbientTextAlign

Načte DISPID_AMBIENT_TEXTALIGN, preferují kontejneru zarovnání textu: 0 pro obecné zarovnání (vlevo textu zprava, čísla), 1 pro zarovnání doleva, pro zarovnání na střed 2 a 3 pro zarovnání doprava.

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>Parametry

*nTextAlign*<br/>
Vlastnost DISPID_AMBIENT_TEXTALIGN.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="getambienttoptobottom"></a>  CComControlBase::GetAmbientTopToBottom

Načte DISPID_AMBIENT_TOPTOBOTTOM, směr, ve kterém se zobrazí obsah kontejnerem.

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>Parametry

*bTopToBottom*<br/>
Vlastnost DISPID_AMBIENT_TOPTOBOTTOM. Nastavte na hodnotu TRUE, pokud se zobrazí text shora dolů, dolní FALSE, pokud se zobrazí nahoru.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="getambientuidead"></a>  CComControlBase::GetAmbientUIDead

Načte DISPID_AMBIENT_UIDEAD příznak označující, jestli konkrétní kontejner potřebuje ovládací prvek reagovat na akce uživatelského rozhraní.

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>Parametry

*bUIDead*<br/>
Vlastnost DISPID_AMBIENT_UIDEAD.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Při hodnotě TRUE by neměl odpovědět ovládacího prvku. Tento příznak platí bez ohledu na to DISPID_AMBIENT_USERMODE příznak. Zobrazit [CComControlBase::GetAmbientUserMode](#getambientusermode).

##  <a name="getambientusermode"></a>  CComControlBase::GetAmbientUserMode

Načte DISPID_AMBIENT_USERMODE příznak označující, jestli je kontejner v režimu běhu (pravda) nebo v režimu návrhu (FALSE).

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>Parametry

*bUserMode*<br/>
Vlastnost DISPID_AMBIENT_USERMODE.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="getdirty"></a>  CComControlBase::GetDirty

Vrací hodnotu datového členu `m_bRequiresSave`.

```
BOOL GetDirty();
```

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu datového členu [m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Poznámky

Tato hodnota se nastavuje pomocí [CComControlBase::SetDirty](#setdirty).

##  <a name="getzoominfo"></a>  CComControlBase::GetZoomInfo

Načte x a y hodnoty čitatelem a jmenovatelem na faktor zvětšování pro ovládací prvek aktivuje pro místní úpravy.

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*di*<br/>
Struktura, která bude obsahovat čitatelem a jmenovatelem na faktor zvětšování. Další informace najdete v tématu [atl_drawinfo –](../../atl/reference/atl-drawinfo-structure.md).

### <a name="remarks"></a>Poznámky

Na faktor zvětšování je část ovládacího prvku fyzická velikost jeho aktuálního rozsahu.

##  <a name="inplaceactivate"></a>  CComControlBase::InPlaceActivate

Způsobí, že ovládací prvek na přechod ze stavu aktivní na cokoli, co stav operací v *iVerb* označuje.

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Hodnotu, která akce, která má být provedena [IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb).

*prcPosRect*<br/>
Ukazatel pozice ovládacího prvku na místě.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Před aktivací tato metoda zkontroluje, že ovládací prvek má lokality klienta, kontroluje, jak velká část ovládacího prvku viditelný a získá umístění ovládacího prvku v nadřazené okno. Po aktivaci ovládacího prvku, tato metoda aktivuje ovládacího prvku uživatelského rozhraní a říká Zviditelněte ovládací prvek kontejneru.

Tato metoda také obnoví `IOleInPlaceSite`, `IOleInPlaceSiteEx`, nebo `IOleInPlaceSiteWindowless` ukazatel rozhraní pro ovládací prvek a uloží jej v třídě ovládacího prvku datový člen [CComControlBase::m_spInPlaceSite](#m_spinplacesite). Datové členy třídy ovládacího prvku [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase::m_bWndLess](#m_bwndless), [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)a [ CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) jsou nastaveny na hodnotu true, podle potřeby.

##  <a name="internalgetsite"></a>  CComControlBase::InternalGetSite

Volejte tuto metodu za účelem zjištění serveru ovládací prvek pro ukazatel rozhraní identifikovaný.

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identifikátor IID rozhraní ukazatel, který má být vrácen v *ppUnkSite*.

*ppUnkSite*<br/>
Adresa proměnné ukazatele, která přijímá ukazatel rozhraní požadované *riid*.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Pokud lokalita podporuje požadované v rozhraní *riid*, ukazatel je vrácený pomocí zprávy *ppUnkSite*. V opačném případě *ppUnkSite* nastaven na hodnotu NULL.

##  <a name="m_bautosize"></a>  CComControlBase::m_bAutoSize

Příznak označující, že ovládací prvek nemůže být libovolné velikosti.

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>Poznámky

Tento příznak je vráceno uživatelem `IOleObjectImpl::SetExtent` a pokud je hodnota TRUE, způsobí, že funkce vrátit E_FAIL.

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Pokud chcete přidat **Automatická velikost** možnost [uložené vlastnosti](../../atl/reference/stock-properties-atl-control-wizard.md) kartu Průvodce ovládacími prvky ATL, průvodce automaticky vytvoří tomuto datovému členu ve své třídě ovládacího prvku, vytvoří put a metody pro vlastnost get a podporuje [ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) automatické zaslání oznámení kontejneru při změně vlastnosti.

##  <a name="m_bdrawfromnatural"></a>  CComControlBase::m_bDrawFromNatural

Příznak označující, že `IDataObjectImpl::GetData` a `CComControlBase::GetZoomInfo` by měl nastavit velikost ovládacího prvku z `m_sizeNatural` spíše než z `m_sizeExtent`.

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_bdrawgetdatainhimetric"></a>  CComControlBase::m_bDrawGetDataInHimetric

Příznak označující, že `IDataObjectImpl::GetData` by měl používat v jednotkách HIMETRIC a ne pixelů při kreslení.

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>Poznámky

Jednotlivých logických jednotek HIMETRIC je 0,01 milimetru.

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_binplaceactive"></a>  CComControlBase::m_bInPlaceActive

Příznak označující, že ovládací prvek je na místě aktivní.

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>Poznámky

To znamená, že je ovládací prvek viditelný a jeho, pokud existuje, je okno viditelné, ale jeho nabídek a panelů nástrojů, nemusí být aktivní. `m_bUIActive` Příznak značí ovládacího prvku uživatelského rozhraní, jako jsou nabídky, je také aktivní.

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_binplacesiteex"></a>  CComControlBase::m_bInPlaceSiteEx

Příznak označující, které podporuje kontejneru `IOleInPlaceSiteEx` rozhraní a OCX96 řídí funkce, jako je například ovládací prvky bez oken a blikání.

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Datový člen `m_spInPlaceSite` odkazuje na [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex), nebo [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless) rozhraní závisí na hodnotě `m_bWndLess` a `m_bInPlaceSiteEx` příznaky. (Datový člen `m_bNegotiatedWnd` musí být nastavena na PRAVDA pro `m_spInPlaceSite` ukazatel na platný.)

Pokud `m_bWndLess` hodnotu FALSE a `m_bInPlaceSiteEx` má hodnotu TRUE, `m_spInPlaceSite` je `IOleInPlaceSiteEx` ukazatel rozhraní. Zobrazit [m_spInPlaceSite](#m_spinplacesite) tabulka znázorňující vztah mezi tyto tři datové členy.

##  <a name="m_bnegotiatedwnd"></a>  CComControlBase::m_bNegotiatedWnd

Příznak označující, zda má ovládací prvek vyjedná s kontejnerem týkající se podpory funkce řízení OCX96 (jako je například ovládací prvky bez blikání a bez oken) a určuje, zda je ovládací prvek oddílové nebo bez oken.

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

`m_bNegotiatedWnd` Příznak musí být nastavena na PRAVDA pro `m_spInPlaceSite` ukazatel na platný.

##  <a name="m_brecomposeonresize"></a>  CComControlBase::m_bRecomposeOnResize

Příznak označující, že chce, aby se ovládací prvek Chcete-li jeho prezentaci při změně velikosti zobrazení ovládacího prvku kontejneru.

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Tento příznak je vráceno uživatelem [IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) a pokud je hodnota TRUE, `SetExtent` upozorní kontejner zobrazení změn. Pokud je tento příznak nastaven, OLEMISC_RECOMPOSEONRESIZE bit ve [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) výčtu by měla být také nastavena.

##  <a name="m_brequiressave"></a>  CComControlBase::m_bRequiresSave

Příznak označující, že ovládací prvek změnila od posledního uložení.

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>Poznámky

Hodnota `m_bRequiresSave` lze nastavit pomocí [CComControlBase::SetDirty](#setdirty) a načtena pomocí [CComControlBase::GetDirty](#getdirty).

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_bresizenatural"></a>  CComControlBase::m_bResizeNatural

Příznak označující, ke změně velikosti jeho fyzické rozsah (jeho bez měřítka fyzická velikost) chce, aby ovládací prvek při změně velikosti zobrazení ovládacího prvku kontejneru.

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>Poznámky

Tento příznak je vráceno uživatelem `IOleObjectImpl::SetExtent` a pokud je hodnota TRUE, velikost předány do `SetExtent` přiřazen `m_sizeNatural`.

Velikost předána do `SetExtent` se vždycky přiřazuje `m_sizeExtent`bez ohledu hodnotu `m_bResizeNatural`.

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_buiactive"></a>  CComControlBase::m_bUIActive

Příznak označující, ovládacího prvku uživatelského rozhraní, jako je například nabídek a panelů nástrojů, je aktivní.

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>Poznámky

`m_bInPlaceActive` Příznak určuje, že je aktivní, ale není to jeho uživatelské rozhraní je aktivní.

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_busingwindowrgn"></a>  CComControlBase::m_bUsingWindowRgn

Příznak označující, že ovládací prvek používá oblast okna zadaný kontejner.

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_bwasoncewindowless"></a>  CComControlBase::m_bWasOnceWindowless

Příznak označující, ovládací prvek bez oken, se ale může nebo nemusí být nyní bez oken.

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_bwindowonly"></a>  CComControlBase::m_bWindowOnly

Příznak označující, že ovládací prvek by měl být oddílové, i v případě, že kontejner podporuje ovládací prvky bez oken.

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_bwndless"></a>  CComControlBase::m_bWndLess

Příznak označující, že je ovládací prvek bez oken.

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Datový člen `m_spInPlaceSite` odkazuje na [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex), nebo [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless) rozhraní závisí na hodnotě `m_bWndLess` a [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex) příznaky. (Datový člen [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) musí být nastavena na PRAVDA pro [CComControlBase::m_spInPlaceSite](#m_spinplacesite) ukazatel na platný.)

Pokud `m_bWndLess` má hodnotu TRUE, `m_spInPlaceSite` je `IOleInPlaceSiteWindowless` ukazatel rozhraní. Zobrazit [CComControlBase::m_spInPlaceSite](#m_spinplacesite) tabulka znázorňující dokončení vztah mezi tyto datové členy.

##  <a name="m_hwndcd"></a>  CComControlBase::m_hWndCD

Obsahuje odkaz na popisovač okna přidružený k ovládacímu prvku.

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_nfreezeevents"></a>  CComControlBase::m_nFreezeEvents

Počet, kolikrát kontejneru je zmrazen události (odmítl akceptovat události) bez použité odblokovat událostí (přijetí události).

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_rcpos"></a>  CComControlBase::m_rcPos

Pozice ovládacího prvku, vyjádřená v souřadnicích kontejneru v pixelech.

```
RECT m_rcPos;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_sizeextent"></a>  CComControlBase::m_sizeExtent

Rozsah ovládacího prvku v jednotkách HIMETRIC (každá jednotka je 0,01 milimetrech) pro konkrétní zobrazení.

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Tato velikost se škálovat podle zobrazení. Fyzická velikost ovládacího prvku je zadán v `m_sizeNatural` datový člen a je pevná.

Velikost můžete převést na pixelech se globální funkce [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

##  <a name="m_sizenatural"></a>  CComControlBase::m_sizeNatural

Fyzická velikost ovládacího prvku v jednotkách HIMETRIC (každá jednotka je 0,01 milimetrech).

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Tato velikost je pevně daná, při velikosti v `m_sizeExtent` měřítko zobrazení.

Velikost můžete převést na pixelech se globální funkce [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

##  <a name="m_spadvisesink"></a>  CComControlBase::m_spAdviseSink

Přímý ukazatel na poradce připojení ke kontejneru (kontejneru [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)).

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_spambientdispatch"></a>  CComControlBase::m_spAmbientDispatch

A `CComDispatchDriver` objekt, který umožňuje načtení a nastavení vlastností objektu prostřednictvím `IDispatch` ukazatele.

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_spclientsite"></a>  CComControlBase::m_spClientSite

Ukazatel na lokality klienta ovládacího prvku v rámci kontejneru.

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

##  <a name="m_spdataadviseholder"></a>  CComControlBase::m_spDataAdviseHolder

Poskytuje že standardní znamená, že pro uložení advisory připojení mezi datovými objekty dokáží jímky.

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Datový objekt je ovládací prvek, který se můžou přenášet data a, který implementuje [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject), jejíž metody zadejte střední formátu a přenos dat.

Rozhraní `m_spDataAdviseHolder` implementuje [IDataObject::DAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dadvise) a [IDataObject::DUnadvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dunadvise) metody pro vytvoření a odstranění advisory připojení ke kontejneru. Kontejneru ovládacího prvku musí implementovat jímky doporučení díky podpoře [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) rozhraní.

##  <a name="m_spinplacesite"></a>  CComControlBase::m_spInPlaceSite

Ukazatel na kontejneru [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex), nebo [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless) ukazatel rozhraní.

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

`m_spInPlaceSite` Ukazatel je platný pouze tehdy, pokud [m_bNegotiatedWnd](#m_bnegotiatedwnd) příznak je TRUE.

Následující tabulka ukazuje jak `m_spInPlaceSite` typ ukazatele závisí [m_bWndLess](#m_bwndless) a [m_bInPlaceSiteEx](#m_binplacesiteex) datový člen příznaky:

|m_spInPlaceSite typu|m_bWndLess hodnotu|m_bInPlaceSiteEx hodnotu|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|HODNOTA TRUE|TRUE nebo FALSE|
|`IOleInPlaceSiteEx`|FALSE|HODNOTA TRUE|
|`IOleInPlaceSite`|FALSE|FALSE|

##  <a name="m_spoleadviseholder"></a>  CComControlBase::m_spOleAdviseHolder

Poskytuje standardní implementace způsob uložení advisory připojení.

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Pokud chcete použít tento datový člen v rámci třídy vašeho ovládacího prvku, je třeba deklarovat jako datový člen ve třídě ovládacího prvku. Třídy vašeho ovládacího prvku nebude dědit tomuto datovému členu ze základní třídy, protože je deklarována v rámci sjednocení v základní třídě.

Rozhraní `m_spOleAdviseHolder` implementuje [IOleObject::Advise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-advise) a [IOleObject::Unadvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-unadvise) metody pro vytvoření a odstranění advisory připojení ke kontejneru. Kontejneru ovládacího prvku musí implementovat jímky doporučení díky podpoře [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) rozhraní.

##  <a name="ondraw"></a>  CComControlBase::OnDraw

Potlačí tuto metodu za účelem vykreslení ovládacího prvku.

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*di*<br/>
Odkaz na [atl_drawinfo –](../../atl/reference/atl-drawinfo-structure.md) strukturu, která obsahuje výkresu informace, jako je aspekt kreslení, hranice ovládacího prvku a určuje, zda je výkresu optimalizovaná nebo ne.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Výchozí hodnota `OnDraw` odstraní nebo obnoví kontextu zařízení nebo nemá žádný účinek, v závislosti na nastavení příznaků v [CComControlBase::OnDrawAdvanced](#ondrawadvanced).

`OnDraw` Metoda je automaticky přidán do třídy vašeho ovládacího prvku při vytváření ovládacího prvku pomocí Průvodce ovládacími prvky ATL. Průvodce výchozí `OnDraw` kreslení obdélníku s popiskem "ATL 8.0".

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CComControlBase::GetAmbientAppearance](#getambientappearance).

##  <a name="ondrawadvanced"></a>  CComControlBase::OnDrawAdvanced

Výchozí hodnota `OnDrawAdvanced` připraví normalizovaný kontext zařízení pro kreslení a pak volá třídy vašeho ovládacího prvku `OnDraw` metody.

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parametry

*di*<br/>
Odkaz na [atl_drawinfo –](../../atl/reference/atl-drawinfo-structure.md) strukturu, která obsahuje výkresu informace, jako je aspekt kreslení, hranice ovládacího prvku a určuje, zda je výkresu optimalizovaná nebo ne.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu, pokud chcete přijmout kontext zařízení předaný kontejnerem, aniž byste ho normalizovali.

Zobrazit [CComControlBase::OnDraw](#ondraw) další podrobnosti.

##  <a name="onkillfocus"></a>  CComControlBase::OnKillFocus

Ověří, že ovládací prvek je aktivní místní a má platný ovládací prvek a potom kontejneru informuje, že ovládací prvek ztratil fokus.

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Vyhrazená.

*wParam*<br/>
Vyhrazená.

*lParam*<br/>
Vyhrazená.

*bHandled*<br/>
Příznak, který označuje, zda byla úspěšně zpracována zprávy okna. Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu 1.

##  <a name="onmouseactivate"></a>  CComControlBase::OnMouseActivate

Kontroluje, zda je v uživatelském režimu uživatelského rozhraní, a aktivuje ovládací prvek.

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Vyhrazená.

*wParam*<br/>
Vyhrazená.

*lParam*<br/>
Vyhrazená.

*bHandled*<br/>
Příznak, který označuje, zda byla úspěšně zpracována zprávy okna. Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu 1.

##  <a name="onpaint"></a>  CComControlBase::OnPaint

Připraví kontejner pro kreslení, získá klientské oblasti ovládacího prvku a pak volá třídy ovládacího prvku `OnDrawAdvanced` metody.

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Vyhrazená.

*wParam*<br/>
Existující HDC.

*lParam*<br/>
Vyhrazená.

*lResult*<br/>
Vyhrazená.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu 0.

### <a name="remarks"></a>Poznámky

Pokud *wParam* nemá hodnotu NULL, `OnPaint` předpokládá obsahuje platné HDC a používá místo něj [CComControlBase::m_hWndCD](#m_hwndcd).

##  <a name="onsetfocus"></a>  CComControlBase::OnSetFocus

Kontroluje, že ovládací prvek je aktivní místní a má platný ovládací prvek a potom informuje kontejneru ovládacího prvku získal fokus.

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*nMsg*<br/>
Vyhrazená.

*wParam*<br/>
Vyhrazená.

*lParam*<br/>
Vyhrazená.

*bHandled*<br/>
Příznak, který označuje, zda byla úspěšně zpracována zprávy okna. Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu 1.

### <a name="remarks"></a>Poznámky

Odešle oznámení do kontejneru, že ovládací prvek přijal fokus.

##  <a name="pretranslateaccelerator"></a>  CComControlBase::PreTranslateAccelerator

Přepsáním této metody můžete zadat vlastní klávesnice obslužné rutiny akcelerátoru.

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Vyhrazená.

*hRet*<br/>
Vyhrazená.

### <a name="return-value"></a>Návratová hodnota

Ve výchozím nastavení vrátí hodnotu FALSE.

##  <a name="sendonclose"></a>  CComControlBase::SendOnClose

Oznámí všechny advisory jímky zaregistrovaného doporučení držitele, že ovládací prvek byla uzavřena.

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Odešle oznámení, že ovládací prvek byl uzavřen jeho advisory jímky.

##  <a name="sendondatachange"></a>  CComControlBase::SendOnDataChange

Oznámí všechny advisory zaregistrovaného držitel doporučení, které se změnily ovládací prvek dat jímky.

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>Parametry

*advf*<br/>
Pomocné příznaky, které určují, jak volání [IAdviseSink::OnDataChange](/windows/desktop/api/objidl/nf-objidl-iadvisesink-ondatachange) tvoří. Hodnoty jsou od [ADVF](/windows/desktop/api/objidl/ne-objidl-tagadvf) výčtu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="sendonrename"></a>  CComControlBase::SendOnRename

Oznámí všechny advisory jímky zaregistrovaného doporučení držitele, že je ovládací prvek monikeru nové.

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>Parametry

*životnosti klíče PMK*<br/>
Ukazatel na novou zástupný název ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Odešle oznámení, že došlo ke změně zástupný pro ovládací prvek.

##  <a name="sendonsave"></a>  CComControlBase::SendOnSave

Oznámí všechny advisory jímky zaregistrovaného držitel doporučení, která byla uložena ovládacího prvku.

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Odešle oznámení, že ovládací prvek právě uchránila svá data.

##  <a name="sendonviewchange"></a>  CComControlBase::SendOnViewChange

Upozorní, že všechny registrované advisory jímky, které došlo ke změně zobrazení ovládacího prvku.

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>Parametry

*dwAspect*<br/>
Aspekt nebo zobrazení ovládacího prvku.

*index*<br/>
Část zobrazení, které se změnily. Je platný pouze hodnotu -1.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

`SendOnViewChange` volání [IAdviseSink::OnViewChange](/windows/desktop/api/objidl/nf-objidl-iadvisesink-onviewchange). Pouze hodnota *index* aktuálně podporovány se -1, což znamená, že celé zobrazení je relevantní.

##  <a name="setcontrolfocus"></a>  CComControlBase::SetControlFocus

Nastaví nebo odebere fokusu klávesnice do nebo z ovládacího prvku.

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>Parametry

*bGrab*<br/>
Při hodnotě TRUE se nastaví fokus klávesnice na ovládacím prvku volání. Pokud má hodnotu FALSE, zruší fokus klávesnice volání ovládacího prvku, pokud má fokus.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud ovládací prvek úspěšně získá fokus; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

U ovládacího prvku v okně, funkce rozhraní Windows API [SetFocus](/windows/desktop/api/winuser/nf-winuser-setfocus) je volána. Pro ovládací prvek bez oken [IOleInPlaceSiteWindowless::SetFocus](/windows/desktop/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) je volána. Prostřednictvím tohoto volání bez oken ovládací prvek získá fokus klávesnice a můžou reagovat na zprávy okna.

##  <a name="setdirty"></a>  CComControlBase::SetDirty

Nastaví datový člen `m_bRequiresSave` s hodnotou v *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*bDirty*<br/>
Hodnota datový člen [CComControlBase::m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Poznámky

`SetDirty(TRUE)` by měla být volána k nastavení příznaku, ovládací prvek se změnila od posledního uložení. Hodnota `m_bRequiresSave` získáte pomocí [CComControlBase::GetDirty](#getdirty).

## <a name="see-also"></a>Viz také

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
