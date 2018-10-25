---
title: Ioleobjectimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl::Advise
- ATLCTL/ATL::IOleObjectImpl::Close
- ATLCTL/ATL::IOleObjectImpl::DoVerb
- ATLCTL/ATL::IOleObjectImpl::DoVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::DoVerbHide
- ATLCTL/ATL::IOleObjectImpl::DoVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::DoVerbOpen
- ATLCTL/ATL::IOleObjectImpl::DoVerbPrimary
- ATLCTL/ATL::IOleObjectImpl::DoVerbShow
- ATLCTL/ATL::IOleObjectImpl::DoVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::EnumAdvise
- ATLCTL/ATL::IOleObjectImpl::EnumVerbs
- ATLCTL/ATL::IOleObjectImpl::GetClientSite
- ATLCTL/ATL::IOleObjectImpl::GetClipboardData
- ATLCTL/ATL::IOleObjectImpl::GetExtent
- ATLCTL/ATL::IOleObjectImpl::GetMiscStatus
- ATLCTL/ATL::IOleObjectImpl::GetMoniker
- ATLCTL/ATL::IOleObjectImpl::GetUserClassID
- ATLCTL/ATL::IOleObjectImpl::GetUserType
- ATLCTL/ATL::IOleObjectImpl::InitFromData
- ATLCTL/ATL::IOleObjectImpl::IsUpToDate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::SetClientSite
- ATLCTL/ATL::IOleObjectImpl::SetColorScheme
- ATLCTL/ATL::IOleObjectImpl::SetExtent
- ATLCTL/ATL::IOleObjectImpl::SetHostNames
- ATLCTL/ATL::IOleObjectImpl::SetMoniker
- ATLCTL/ATL::IOleObjectImpl::Unadvise
- ATLCTL/ATL::IOleObjectImpl::Update
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0595b98d26b401a93545b96a719a7c0af3440fea
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054188"
---
# <a name="ioleobjectimpl-class"></a>Ioleobjectimpl – třída

Tato třída implementuje `IUnknown` a je hlavní rozhraní, přes který kontejner komunikuje s ovládacím prvkem.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IOleObjectImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IOleObjectImpl::Advise](#advise)|Naváže připojení k advisory pomocí ovládacího prvku.|
|[IOleObjectImpl::Close](#close)|Změní stav ovládacího prvku ve spuštění načíst.|
|[IOleObjectImpl::DoVerb](#doverb)|Určuje ovládací prvek pro jeden z jeho výčet akce.|
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Určuje ovládací prvek zahodíte všechny zpět stavu, ve kterém se udržuje.|
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Určuje ovládací prvek chcete odebrat ze zobrazení uživatelského rozhraní.|
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Ovládací prvek spustí a nainstaluje její okno, ale není možné nainstalovat ovládacího prvku uživatelského rozhraní.|
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|Způsobí, že ovládací prvek bude upravovat otevřené v samostatném okně.|
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|Provede zadanou akci, když uživatel dvakrát klikne ovládací prvek. Ovládací prvek definuje akce, obvykle k aktivaci ovládacího prvku na místě.|
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Zobrazuje nově vložený prvek uživateli.|
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|Aktivuje ovládací prvek na místě a ukazuje ovládacího prvku uživatelského rozhraní, jako je například nabídek a panelů nástrojů.|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Vytvoří výčet advisory připojení ovládacího prvku.|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Vytvoří výčet akce pro ovládací prvek.|
|[IOleObjectImpl::GetClientSite](#getclientsite)|Načte ovládacího prvku lokality klienta.|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Načte data ze schránky. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IOleObjectImpl::GetExtent](#getextent)|Načte rozsah oblasti ovládacího prvku zobrazení.|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Načte stav ovládacího prvku.|
|[IOleObjectImpl::GetMoniker](#getmoniker)|Načte zástupný název ovládacího prvku. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Načte identifikátor třídy ovládacího prvku.|
|[IOleObjectImpl::GetUserType](#getusertype)|Načte název uživatele – typ ovládacího prvku.|
|[IOleObjectImpl::InitFromData](#initfromdata)|Inicializuje ovládací prvek z vybraného data. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Zkontroluje, zda ovládací prvek je aktuální. Implementace knihovny ATL vrátí hodnotu S_OK.|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Volané [DoVerbDiscardUndo](#doverbdiscardundo) po stav vracení zpět se zahodí.|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Volané [DoVerbHide](#doverbhide) po skrytý ovládací prvek.|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Volané [DoVerbInPlaceActivate](#doverbinplaceactivate) po aktivaci ovládacího prvku na místě.|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Volané [DoVerbOpen](#doverbopen) po otevření ovládacího prvku pro úpravy v samostatném okně.|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Volané [DoVerbShow](#doverbshow) po ovládací prvek viditelný.|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Volané [DoVerbUIActivate](#doverbuiactivate) po aktivaci ovládacího prvku uživatelského rozhraní.|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Volané [DoVerbDiscardUndo](#doverbdiscardundo) před zpět stav zahozeny.|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Volané [DoVerbHide](#doverbhide) předtím, než je skrytý ovládací prvek.|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Volané [DoVerbInPlaceActivate](#doverbinplaceactivate) předtím, než se ovládací prvek aktivuje v místě.|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Volané [DoVerbOpen](#doverbopen) před ovládací prvek byl otevřen pro úpravy v samostatném okně.|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Volané [DoVerbShow](#doverbshow) předtím, než se neprovedl ovládací prvek viditelný.|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Volané [DoVerbUIActivate](#doverbuiactivate) před ovládacího prvku uživatelského rozhraní se aktivovala.|
|[IOleObjectImpl::SetClientSite](#setclientsite)|Informuje o jeho lokality klienta v kontejneru ovládacího prvku.|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Doporučuje barevné schéma do ovládacího prvku aplikace, pokud existuje. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IOleObjectImpl::SetExtent](#setextent)|Nastaví rozsah, oblasti ovládacího prvku zobrazení.|
|[IOleObjectImpl::SetHostNames](#sethostnames)|Určuje ovládací prvek názvy aplikace typu kontejner a kontejner dokumentů.|
|[IOleObjectImpl::SetMoniker](#setmoniker)|Co je jeho moniker říká ovládací prvek. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IOleObjectImpl::Unadvise](#unadvise)|Odstraní advisory připojení pomocí ovládacího prvku.|
|[IOleObjectImpl::Update](#update)|Aktualizuje ovládacího prvku. Implementace knihovny ATL vrátí hodnotu S_OK.|

## <a name="remarks"></a>Poznámky

[IOleObject](/windows/desktop/api/oleidl/nn-oleidl-ioleobject) rozhraní je hlavní rozhraní, přes který kontejner komunikuje s ovládacím prvkem. Třída `IOleObjectImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.

**Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="advise"></a>  IOleObjectImpl::Advise

Naváže připojení k advisory pomocí ovládacího prvku.

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IOleObject::Advise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-advise) ve Windows SDK.

##  <a name="close"></a>  IOleObjectImpl::Close

Změní stav ovládacího prvku ve spuštění načíst.

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>Poznámky

Ovládací prvek deaktivuje a odstraní okno ovládacího prvku, pokud existuje. Pokud ovládací prvek třídy datový člen [CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) má hodnotu TRUE a *dwSaveOption* parametr OLECLOSE_SAVEIFDIRTY nebo OLECLOSE_PROMPTSAVE, jsou vlastnosti ovládacích prvků uložit před zavřením.

Ukazatelů uchovávat v datovém typu datové členy třídy ovládacího prvku [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) a [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) jsou všeobecně dostupné a datové členy [CComControlBase –:: m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless), a [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) jsou nastaveny na hodnotu FALSE.

Zobrazit [IOleObject::Close](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-close) ve Windows SDK.

##  <a name="doverb"></a>  IOleObjectImpl::DoVerb

Určuje ovládací prvek pro jeden z jeho výčet akce.

```
STDMETHOD(DoVerb)(
    LONG iVerb,
    LPMSG /* pMsg */,
    IOleClientSite* pActiveSite,
    LONG /* lindex */,
    HWND hwndParent,
    LPCRECT lprcPosRect);
```

### <a name="remarks"></a>Poznámky

V závislosti na hodnotě z `iVerb`, jeden z knihovny ATL `DoVerb` pomocné funkce se nazývá následujícím způsobem:

|*iVerb* hodnota|Volá se funkce DoVerb pomocné funkce|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|

Zobrazit [Funkce IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) ve Windows SDK.

##  <a name="doverbdiscardundo"></a>  IOleObjectImpl::DoVerbDiscardUndo

Určuje ovládací prvek zahodíte všechny zpět stavu, ve kterém se udržuje.

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
[in] Ukazatel na obdélník kontejneru chce, aby se k vykreslení do ovládacího prvku.

*hwndParent*<br/>
[in] Popisovač okna obsahující ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

##  <a name="doverbhide"></a>  IOleObjectImpl::DoVerbHide

Deaktivuje a odebere ovládacího prvku uživatelského rozhraní a skryje ovládacího prvku.

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
[in] Ukazatel na obdélník kontejneru chce, aby se k vykreslení do ovládacího prvku.

*hwndParent*<br/>
[in] Popisovač okna obsahující ovládací prvek. Není použitý v implementaci ATL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

##  <a name="doverbinplaceactivate"></a>  IOleObjectImpl::DoVerbInPlaceActivate

Ovládací prvek spustí a nainstaluje její okno, ale není možné nainstalovat ovládacího prvku uživatelského rozhraní.

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
[in] Ukazatel na obdélník kontejneru chce, aby se k vykreslení do ovládacího prvku.

*hwndParent*<br/>
[in] Popisovač okna obsahující ovládací prvek. Není použitý v implementaci ATL.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Aktivuje ovládací prvek na místě voláním [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). Není-li datový člen třídy ovládacího prvku `m_bWindowOnly` má hodnotu TRUE, `DoVerbInPlaceActivate` poprvé pokusí aktivovat ovládací prvek jako ovládací prvek bez oken (možný jenom v případě, že kontejner podporuje [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)). Pokud se to nepodaří, funkce se pokusí aktivovat ovládacího prvku pomocí rozšířených funkcí (možný jenom v případě, že kontejner podporuje [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)). Pokud se to nepodaří, funkce se pokusí aktivovat ovládací prvek s žádné rozšířené funkce (možný jenom v případě, že kontejner podporuje [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)). Pokud je aktivace úspěšná, funkce oznámí kontejneru, že ovládací prvek se aktivoval.

##  <a name="doverbopen"></a>  IOleObjectImpl::DoVerbOpen

Způsobí, že ovládací prvek bude upravovat otevřené v samostatném okně.

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
[in] Ukazatel na obdélník kontejneru chce, aby se k vykreslení do ovládacího prvku.

*hwndParent*<br/>
[in] Popisovač okna obsahující ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

##  <a name="doverbprimary"></a>  IOleObjectImpl::DoVerbPrimary

Definuje akce provedená v případě, že uživatel dvakrát klikne ovládací prvek.

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
[in] Ukazatel na obdélník kontejneru chce, aby se k vykreslení do ovládacího prvku.

*hwndParent*<br/>
[in] Popisovač okna obsahující ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení zobrazení stránky vlastností. Toto můžete přepsat v třídy vašeho ovládacího prvku, který má být vyvolán různé chování při poklepání; například přehrávání videa nebo přejděte na místě aktivní.

##  <a name="doverbshow"></a>  IOleObjectImpl::DoVerbShow

Určuje kontejner, aby Zviditelněte ovládací prvek.

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
[in] Ukazatel na obdélník kontejneru chce, aby se k vykreslení do ovládacího prvku.

*hwndParent*<br/>
[in] Popisovač okna obsahující ovládací prvek. Není použitý v implementaci ATL.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="doverbuiactivate"></a>  IOleObjectImpl::DoVerbUIActivate

Aktivuje ovládacího prvku uživatelského rozhraní a upozorní kontejneru, že jeho nabídky se nahrazují složené nabídky.

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
[in] Ukazatel na obdélník kontejneru chce, aby se k vykreslení do ovládacího prvku.

*hwndParent*<br/>
[in] Popisovač okna obsahující ovládací prvek. Není použitý v implementaci ATL.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

##  <a name="enumadvise"></a>  IOleObjectImpl::EnumAdvise

Poskytuje výčet připojeních poradenství pro tento ovládací prvek.

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IOleObject::EnumAdvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumadvise) ve Windows SDK.

##  <a name="enumverbs"></a>  IOleObjectImpl::EnumVerbs

Poskytuje výčet registrované akce (akce) pro tento ovládací prvek voláním `OleRegEnumVerbs`.

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>Poznámky

Příkazy můžete přidat do souboru .rgs vašeho projektu. Podívejte se například CIRCCTL. RGS v [KR](../../visual-cpp-samples.md) vzorku.

Zobrazit [IOleObject::EnumVerbs](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumverbs) ve Windows SDK.

##  <a name="getclientsite"></a>  IOleObjectImpl::GetClientSite

Umístí ukazatel ovládací prvek – datový člen třídy [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) do *ppClientSite* a zvýší počet odkazů na ukazatel.

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IOleObject::GetClientSite](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getclientsite) ve Windows SDK.

##  <a name="getclipboarddata"></a>  IOleObjectImpl::GetClipboardData

Načte data ze schránky.

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleObject::GetClipboardData](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) ve Windows SDK.

##  <a name="getextent"></a>  IOleObjectImpl::GetExtent

Získá velikost zobrazení ovládacího prvku spuštěné v jednotkách HIMETRIC (za jednotku 0,01 milimetru).

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Poznámky

Velikost uložená v datovém členovi třídy ovládacího prvku [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

Zobrazit [IOleObject::GetExtent](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getextent) ve Windows SDK.

##  <a name="getmiscstatus"></a>  IOleObjectImpl::GetMiscStatus

Vrací ukazatel na informace o registrovaných stavu ovládacího prvku voláním `OleRegGetMiscStatus`.

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>Poznámky

Informace o stavu zahrnuje chování ovládacího prvku a prezentace dat podporuje. Informace o stavu můžete přidat do souboru .rgs vašeho projektu.

Zobrazit [IOleObject::GetMiscStatus](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) ve Windows SDK.

##  <a name="getmoniker"></a>  IOleObjectImpl::GetMoniker

Načte zástupný název ovládacího prvku.

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleObject::GetMoniker](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmoniker) ve Windows SDK.

##  <a name="getuserclassid"></a>  IOleObjectImpl::GetUserClassID

Vrátí identifikátor třídy ovládacího prvku.

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IOleObject::GetUserClassID](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getuserclassid) ve Windows SDK.

##  <a name="getusertype"></a>  IOleObjectImpl::GetUserType

Vrátí název ovládacího prvku typ uživatele voláním `OleRegGetUserType`.

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>Poznámky

Název Typ uživatele se používá pro zobrazení v prvky uživatelského rozhraní, jako jsou nabídky a dialogových oknech. Můžete změnit název typ uživatele v souboru .rgs vašeho projektu.

Zobrazit [IOleObject::GetUserType](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getusertype) ve Windows SDK.

##  <a name="initfromdata"></a>  IOleObjectImpl::InitFromData

Inicializuje ovládací prvek z vybraného data.

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleObject::InitFromData](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-initfromdata) ve Windows SDK.

##  <a name="isuptodate"></a>  IOleObjectImpl::IsUpToDate

Zkontroluje, zda ovládací prvek je aktuální.

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleObject::IsUpToDate](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-isuptodate) ve Windows SDK.

##  <a name="onpostverbdiscardundo"></a>  IOleObjectImpl::OnPostVerbDiscardUndo

Volané [DoVerbDiscardUndo](#doverbdiscardundo) po stav vracení zpět se zahodí.

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu s kódem, který chcete spustit po stav vracení zpět se zahodí.

##  <a name="onpostverbhide"></a>  IOleObjectImpl::OnPostVerbHide

Volané [DoVerbHide](#doverbhide) po skrytý ovládací prvek.

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu s kódem, který chcete spustit po skrytý ovládací prvek.

##  <a name="onpostverbinplaceactivate"></a>  IOleObjectImpl::OnPostVerbInPlaceActivate

Volané [DoVerbInPlaceActivate](#doverbinplaceactivate) po aktivaci ovládacího prvku na místě.

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu s kódem, který chcete spustit po aktivaci ovládacího prvku na místě.

##  <a name="onpostverbopen"></a>  IOleObjectImpl::OnPostVerbOpen

Volané [DoVerbOpen](#doverbopen) po otevření ovládacího prvku pro úpravy v samostatném okně.

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu s kódem, který chcete spustit po otevření ovládacího prvku pro úpravy v samostatném okně.

##  <a name="onpostverbshow"></a>  IOleObjectImpl::OnPostVerbShow

Volané [DoVerbShow](#doverbshow) po ovládací prvek viditelný.

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu s kódem, který chcete spustit po ovládací prvek viditelný.

##  <a name="onpostverbuiactivate"></a>  IOleObjectImpl::OnPostVerbUIActivate

Volané [DoVerbUIActivate](#doverbuiactivate) po aktivaci ovládacího prvku uživatelského rozhraní.

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu s kódem, který chcete spustit po aktivaci ovládacího prvku uživatelského rozhraní.

##  <a name="onpreverbdiscardundo"></a>  IOleObjectImpl::OnPreVerbDiscardUndo

Volané [DoVerbDiscardUndo](#doverbdiscardundo) před zpět stav zahozeny.

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Pokud chcete zakázat stav vracení zpět se zahodí, přepište tuto metodu za účelem vrátí chybu HRESULT.

##  <a name="onpreverbhide"></a>  IOleObjectImpl::OnPreVerbHide

Volané [DoVerbHide](#doverbhide) předtím, než je skrytý ovládací prvek.

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Abyste zabránili skryté ovládacího prvku, přepište tuto metodu za účelem vrátí chybu HRESULT.

##  <a name="onpreverbinplaceactivate"></a>  IOleObjectImpl::OnPreVerbInPlaceActivate

Volané [DoVerbInPlaceActivate](#doverbinplaceactivate) předtím, než se ovládací prvek aktivuje v místě.

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Pokud chcete zakázat ovládací prvek aktivuje v místě, přepište tuto metodu za účelem vrátí chybu HRESULT.

##  <a name="onpreverbopen"></a>  IOleObjectImpl::OnPreVerbOpen

Volané [DoVerbOpen](#doverbopen) před ovládací prvek byl otevřen pro úpravy v samostatném okně.

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Pokud chcete zakázat ovládací prvek se po otevření k úpravám v samostatném okně, přepište tuto metodu za účelem vrátí chybu HRESULT.

##  <a name="onpreverbshow"></a>  IOleObjectImpl::OnPreVerbShow

Volané [DoVerbShow](#doverbshow) předtím, než se neprovedl ovládací prvek viditelný.

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Abyste zabránili prováděné viditelné ovládací prvek, přepište tuto metodu za účelem vrátí chybu HRESULT.

##  <a name="onpreverbuiactivate"></a>  IOleObjectImpl::OnPreVerbUIActivate

Volané [DoVerbUIActivate](#doverbuiactivate) před ovládacího prvku uživatelského rozhraní se aktivovala.

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Aby se zabránilo ovládacího prvku uživatelského rozhraní při aktivaci, přepište tuto metodu za účelem vrátí chybu HRESULT.

##  <a name="setclientsite"></a>  IOleObjectImpl::SetClientSite

Informuje o jeho lokality klienta v kontejneru ovládacího prvku.

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>Poznámky

Metoda pak vrátí hodnotu S_OK.

Zobrazit [IOleObject::SetClientSite](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setclientsite) ve Windows SDK.

##  <a name="setcolorscheme"></a>  IOleObjectImpl::SetColorScheme

Doporučuje barevné schéma do ovládacího prvku aplikace, pokud existuje.

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleObject::SetColorScheme](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) ve Windows SDK.

##  <a name="setextent"></a>  IOleObjectImpl::SetExtent

Nastaví rozsah, oblasti ovládacího prvku zobrazení.

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Poznámky

V opačném případě `SetExtent` uloží hodnotu, na které odkazuje `psizel` v datovém členovi třídy ovládacího prvku [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Tato hodnota je v jednotkách HIMETRIC (za jednotku 0,01 milimetru).

Pokud ovládací prvek třídy datový člen [CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) má hodnotu TRUE, `SetExtent` také ukládá hodnotu, na které odkazuje `psizel` v datovém členovi třídy ovládacího prvku [CComControlBase::m_sizeNatural ](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).

Pokud ovládací prvek třídy datový člen [CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) má hodnotu TRUE, `SetExtent` volání `SendOnDataChange` a `SendOnViewChange` upozornit všechny advisory jímky zaregistrovaného držitel doporučení, která má velikost ovládacího prvku změnit.

Zobrazit [IOleObject::SetExtent](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setextent) ve Windows SDK.

##  <a name="sethostnames"></a>  IOleObjectImpl::SetHostNames

Určuje ovládací prvek názvy aplikace typu kontejner a kontejner dokumentů.

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleObject::SetHostNames](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-sethostnames) ve Windows SDK.

##  <a name="setmoniker"></a>  IOleObjectImpl::SetMoniker

Co je jeho moniker říká ovládací prvek.

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleObject::SetMoniker](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setmoniker) ve Windows SDK.

##  <a name="unadvise"></a>  IOleObjectImpl::Unadvise

Odstraní advisory připojení uložené ve třídě ovládacího prvku `m_spOleAdviseHolder` datový člen.

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IOleObject::Unadvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-unadvise) ve Windows SDK.

##  <a name="update"></a>  IOleObjectImpl::Update

Aktualizuje ovládacího prvku.

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleObject::Update](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-update) ve Windows SDK.

## <a name="see-also"></a>Viz také

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Rozhraní – ovládací prvky ActiveX](/windows/desktop/com/activex-controls-interfaces)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
