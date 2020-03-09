---
title: IOleObjectImpl – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
ms.openlocfilehash: ded158b0ec862de5b0d0b23dd4b9edb50ad577ef
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862911"
---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl – třída

Tato třída implementuje `IUnknown` a je hlavní rozhraní, pomocí kterého kontejner komunikuje s ovládacím prvkem.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída odvozená od `IOleObjectImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IOleObjectImpl:: Advise](#advise)|Vytvoří poradní spojení s ovládacím prvkem.|
|[IOleObjectImpl:: Close](#close)|Změní stav ovládacího prvku ze spuštěno na načteno.|
|[IOleObjectImpl::D oVerb](#doverb)|Instruuje ovládací prvek, aby provedl jednu z jeho výčtových akcí.|
|[IOleObjectImpl::D oVerbDiscardUndo](#doverbdiscardundo)|Přikáže ovládacímu prvku, aby zahodí všechny změny, které se udržují.|
|[IOleObjectImpl::D oVerbHide](#doverbhide)|Oznamuje ovládacímu prvku, aby ze zobrazení odstranil jeho uživatelské rozhraní.|
|[IOleObjectImpl::D oVerbInPlaceActivate](#doverbinplaceactivate)|Spustí ovládací prvek a nainstaluje jeho okno, ale neinstaluje uživatelské rozhraní ovládacího prvku.|
|[IOleObjectImpl::D oVerbOpen](#doverbopen)|Způsobí, že ovládací prvek bude otevřen v samostatném okně.|
|[IOleObjectImpl::D oVerbPrimary](#doverbprimary)|Provede zadanou akci, když uživatel dvakrát klikne na ovládací prvek. Ovládací prvek definuje akci, obvykle pro aktivaci ovládacího prvku na místě.|
|[IOleObjectImpl::D oVerbShow](#doverbshow)|Zobrazí uživateli nově vložený ovládací prvek.|
|[IOleObjectImpl::D oVerbUIActivate](#doverbuiactivate)|Aktivuje ovládací prvek na místě a zobrazuje uživatelské rozhraní ovládacího prvku, jako jsou nabídky a panely nástrojů.|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Vytvoří výčet poradních připojení ovládacího prvku.|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Vytvoří výčet akcí pro ovládací prvek.|
|[IOleObjectImpl::GetClientSite](#getclientsite)|Načte klientský web ovládacího prvku.|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Načte data ze schránky. Implementace ATL vrací E_NOTIMPL.|
|[IOleObjectImpl:: getrozsah](#getextent)|Načte rozsah zobrazované oblasti ovládacího prvku.|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Načte stav ovládacího prvku.|
|[IOleObjectImpl:: GetMoniker](#getmoniker)|Načte moniker ovládacího prvku. Implementace ATL vrací E_NOTIMPL.|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Načte identifikátor třídy ovládacího prvku.|
|[IOleObjectImpl::GetUserType](#getusertype)|Načte název uživatelského typu ovládacího prvku.|
|[IOleObjectImpl::InitFromData](#initfromdata)|Inicializuje ovládací prvek z vybraných dat. Implementace ATL vrací E_NOTIMPL.|
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Kontroluje, zda je ovládací prvek aktuální. Implementace ATL vrací S_OK.|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Volá se [DoVerbDiscardUndo](#doverbdiscardundo) po zahození stavu vrácení zpět.|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Volá se [DoVerbHide](#doverbhide) po skrytí ovládacího prvku.|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Volá se [DoVerbInPlaceActivate](#doverbinplaceactivate) po aktivaci ovládacího prvku na místě.|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Volá se [DoVerbOpen](#doverbopen) po otevření ovládacího prvku pro úpravy v samostatném okně.|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Volá se [DoVerbShow](#doverbshow) po tom, co se ovládací prvek nastavil jako viditelný.|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Volá se [DoVerbUIActivate](#doverbuiactivate) po aktivaci uživatelského rozhraní ovládacího prvku.|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Volá se [DoVerbDiscardUndo](#doverbdiscardundo) před tím, než se zruší stav zrušení.|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Volá se [DoVerbHide](#doverbhide) před tím, než je ovládací prvek skrytý.|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Volá se [DoVerbInPlaceActivate](#doverbinplaceactivate) před aktivací ovládacího prvku na místě.|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Volá se [DoVerbOpen](#doverbopen) před otevřením ovládacího prvku pro úpravy v samostatném okně.|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Volá se [DoVerbShow](#doverbshow) před tím, než se ovládací prvek zviditelní.|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Volá se [DoVerbUIActivate](#doverbuiactivate) před aktivací uživatelského rozhraní ovládacího prvku.|
|[IOleObjectImpl::SetClientSite](#setclientsite)|Instruuje ovládací prvek o jeho klientské lokalitě v kontejneru.|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Doporučuje barevné schéma pro aplikaci ovládacího prvku, pokud existuje. Implementace ATL vrací E_NOTIMPL.|
|[IOleObjectImpl::SetExtent](#setextent)|Nastaví rozsah zobrazované oblasti ovládacího prvku.|
|[IOleObjectImpl::SetHostNames](#sethostnames)|Informuje ovládací prvek o názvech aplikace kontejneru a dokumentu kontejneru.|
|[IOleObjectImpl::SetMoniker](#setmoniker)|Oznamuje ovládacímu prvku, co je jeho moniker. Implementace ATL vrací E_NOTIMPL.|
|[IOleObjectImpl:: Unadvise](#unadvise)|Odstraní Poradní připojení k ovládacímu prvku.|
|[IOleObjectImpl:: Update](#update)|Aktualizuje ovládací prvek. Implementace ATL vrací S_OK.|

## <a name="remarks"></a>Poznámky

Rozhraní [IOleObject](/windows/win32/api/oleidl/nn-oleidl-ioleobject) je hlavní rozhraní, pomocí kterého kontejner komunikuje s ovládacím prvkem. Třída `IOleObjectImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestaveních pro ladění.

Kurz **související články** [ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="advise"></a>IOleObjectImpl:: Advise

Vytvoří poradní spojení s ovládacím prvkem.

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Poznámky

Viz [IOleObject:: Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) v Windows SDK.

##  <a name="close"></a>IOleObjectImpl:: Close

Změní stav ovládacího prvku ze spuštěno na načteno.

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>Poznámky

Deaktivuje ovládací prvek a odstraní okno ovládacího prvku, pokud existuje. Pokud je datový člen třídy ovládacího prvku [CComControlBase:: M_BREQUIRESSAVE](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) true a parametr *dwSaveOption* je buď OLECLOSE_SAVEIFDIRTY nebo OLECLOSE_PROMPTSAVE, vlastnosti ovládacího prvku jsou před zavřením uloženy.

Ukazatele uchovávané v datových členech třídy ovládacího prvku [CComControlBase:: m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) a [CComControlBase:: m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) jsou uvolněny a datové členy [CComControlBase:: m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase:: m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)a [CComControlBase:: m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) jsou nastaveny na hodnotu false.

Viz [IOleObject:: Close](/windows/win32/api/oleidl/nf-oleidl-ioleobject-close) v Windows SDK.

##  <a name="doverb"></a>IOleObjectImpl::D oVerb

Instruuje ovládací prvek, aby provedl jednu z jeho výčtových akcí.

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

V závislosti na hodnotě `iVerb`je jedna z pomocných funkcí ATL `DoVerb` volána následujícím způsobem:

|*iVerb* Osa|Pomocná funkce DoVerb se volala|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::D oVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|

Viz [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) v Windows SDK.

##  <a name="doverbdiscardundo"></a>IOleObjectImpl::D oVerbDiscardUndo

Přikáže ovládacímu prvku, aby zahodí všechny změny, které se udržují.

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
pro Ukazatel na obdélník, do kterého kontejner chce ovládací prvek nakreslit.

*hwndParent*<br/>
pro Popisovač okna obsahujícího ovládací prvek

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

##  <a name="doverbhide"></a>IOleObjectImpl::D oVerbHide

Deaktivuje a odebere uživatelské rozhraní ovládacího prvku a skryje ovládací prvek.

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
pro Ukazatel na obdélník, do kterého kontejner chce ovládací prvek nakreslit.

*hwndParent*<br/>
pro Popisovač okna obsahujícího ovládací prvek Nepoužívá se v implementaci ATL.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

##  <a name="doverbinplaceactivate"></a>IOleObjectImpl::D oVerbInPlaceActivate

Spustí ovládací prvek a nainstaluje jeho okno, ale neinstaluje uživatelské rozhraní ovládacího prvku.

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
pro Ukazatel na obdélník, do kterého kontejner chce ovládací prvek nakreslit.

*hwndParent*<br/>
pro Popisovač okna obsahujícího ovládací prvek Nepoužívá se v implementaci ATL.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Aktivuje ovládací prvek místo voláním [CComControlBase:: InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). Není-li datový člen třídy ovládacího prvku `m_bWindowOnly` TRUE, `DoVerbInPlaceActivate` nejprve proveden pokus o aktivaci ovládacího prvku jako řízení bez okna (možné pouze v případě, že kontejner podporuje [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)). Pokud se to nepovede, funkce se pokusí o aktivaci ovládacího prvku s rozšířenými funkcemi (možné pouze v případě, že kontejner podporuje [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)). Pokud se to nepovede, funkce se pokusí aktivovat ovládací prvek bez rozšířených funkcí (možné jenom v případě, že kontejner podporuje [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)). Pokud je aktivace úspěšná, funkce upozorní kontejner na aktivaci ovládacího prvku.

##  <a name="doverbopen"></a>IOleObjectImpl::D oVerbOpen

Způsobí, že ovládací prvek bude otevřen v samostatném okně.

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
pro Ukazatel na obdélník, do kterého kontejner chce ovládací prvek nakreslit.

*hwndParent*<br/>
pro Popisovač okna obsahujícího ovládací prvek

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

##  <a name="doverbprimary"></a>IOleObjectImpl::D oVerbPrimary

Definuje akci provedenou, když uživatel dvakrát klikne na ovládací prvek.

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
pro Ukazatel na obdélník, do kterého kontejner chce ovládací prvek nakreslit.

*hwndParent*<br/>
pro Popisovač okna obsahujícího ovládací prvek

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je nastaveno zobrazení stránek vlastností. Můžete ji přepsat ve vaší třídě ovládacího prvku a vyvolat tak jiné chování při poklikání. Můžete například přehrát video nebo přejít na místo na místě aktivní.

##  <a name="doverbshow"></a>IOleObjectImpl::D oVerbShow

Dá kontejneru pokyn, aby ovládací prvek byl viditelný.

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
pro Ukazatel na obdélník, do kterého kontejner chce ovládací prvek nakreslit.

*hwndParent*<br/>
pro Popisovač okna obsahujícího ovládací prvek Nepoužívá se v implementaci ATL.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="doverbuiactivate"></a>IOleObjectImpl::D oVerbUIActivate

Aktivuje uživatelské rozhraní ovládacího prvku a upozorní kontejner, že jeho nabídky se nahrazují složenými nabídkami.

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*prcPosRec*<br/>
pro Ukazatel na obdélník, do kterého kontejner chce ovládací prvek nakreslit.

*hwndParent*<br/>
pro Popisovač okna obsahujícího ovládací prvek Nepoužívá se v implementaci ATL.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

##  <a name="enumadvise"></a>IOleObjectImpl::EnumAdvise

Poskytuje výčet registrovaných poradenských připojení pro tento ovládací prvek.

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>Poznámky

Viz [IOleObject:: enumAdvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumadvise) v Windows SDK.

##  <a name="enumverbs"></a>IOleObjectImpl::EnumVerbs

Poskytuje výčet registrovaných akcí (operací) pro tento ovládací prvek voláním `OleRegEnumVerbs`.

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>Poznámky

Do souboru. rgs projektu můžete přidat operace. Například viz CIRCCTL. RGS v ukázce [str](../../overview/visual-cpp-samples.md) .

Viz [IOleObject:: EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs) v Windows SDK.

##  <a name="getclientsite"></a>IOleObjectImpl::GetClientSite

Vloží ukazatel do datového členu třídy ovládacího prvku [CComControlBase:: m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) do *ppClientSite* a zvýší počet odkazů na ukazatel.

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>Poznámky

Viz [IOleObject:: GetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclientsite) v Windows SDK.

##  <a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData

Načte data ze schránky.

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IOleObject:: GetClipboardData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) v Windows SDK.

##  <a name="getextent"></a>IOleObjectImpl:: getrozsah

Načte velikost zobrazení běžícího ovládacího prvku v jednotkách HIMETRIC (0,01 milimetru na jednotku).

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Poznámky

Velikost je uložena v datovém členu třídy ovládacího prvku [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

Viz [IOleObject:: getrozsah](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getextent) v Windows SDK.

##  <a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus

Vrátí ukazatel na zaregistrované informace o stavu ovládacího prvku voláním `OleRegGetMiscStatus`.

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>Poznámky

Informace o stavu zahrnují chování, které podporuje data ovládacího prvku a prezentace. Do souboru. rgs projektu můžete přidat informace o stavu.

Viz [IOleObject:: GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) v Windows SDK.

##  <a name="getmoniker"></a>IOleObjectImpl:: GetMoniker

Načte moniker ovládacího prvku.

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IOleObject:: GetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmoniker) v Windows SDK.

##  <a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID

Vrátí identifikátor třídy ovládacího prvku.

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>Poznámky

Viz [IOleObject:: GetUserClassID](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getuserclassid) v Windows SDK.

##  <a name="getusertype"></a>IOleObjectImpl::GetUserType

Vrátí název uživatelského typu ovládacího prvku voláním `OleRegGetUserType`.

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>Poznámky

Název uživatelského typu se používá k zobrazení v prvcích uživatelského rozhraní, jako jsou nabídky a dialogová okna. V souboru. rgs projektu můžete změnit název typu uživatele.

Viz [IOleObject:: GetUserType](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getusertype) v Windows SDK.

##  <a name="initfromdata"></a>IOleObjectImpl::InitFromData

Inicializuje ovládací prvek z vybraných dat.

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IOleObject:: InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) v Windows SDK.

##  <a name="isuptodate"></a>IOleObjectImpl::IsUpToDate

Kontroluje, zda je ovládací prvek aktuální.

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleObject:: IsUpToDate](/windows/win32/api/oleidl/nf-oleidl-ioleobject-isuptodate) v Windows SDK.

##  <a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo

Volá se [DoVerbDiscardUndo](#doverbdiscardundo) po zahození stavu vrácení zpět.

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete přepsat kódem, který má být proveden po zahození stavu vrácení zpět.

##  <a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide

Volá se [DoVerbHide](#doverbhide) po skrytí ovládacího prvku.

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete přepsat kódem, který chcete provést po skrytí ovládacího prvku.

##  <a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate

Volá se [DoVerbInPlaceActivate](#doverbinplaceactivate) po aktivaci ovládacího prvku na místě.

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete přepsat kódem, který chcete provést po aktivaci ovládacího prvku na místě.

##  <a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen

Volá se [DoVerbOpen](#doverbopen) po otevření ovládacího prvku pro úpravy v samostatném okně.

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište pomocí kódu, který má být proveden po otevření ovládacího prvku pro úpravy v samostatném okně.

##  <a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow

Volá se [DoVerbShow](#doverbshow) po tom, co se ovládací prvek nastavil jako viditelný.

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište pomocí kódu, který má být proveden poté, co byl ovládací prvek proveden jako viditelný.

##  <a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate

Volá se [DoVerbUIActivate](#doverbuiactivate) po aktivaci uživatelského rozhraní ovládacího prvku.

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište pomocí kódu, který má být proveden po aktivaci uživatelského rozhraní ovládacího prvku.

##  <a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo

Volá se [DoVerbDiscardUndo](#doverbdiscardundo) před tím, než se zruší stav zrušení.

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Chcete-li zabránit zahození stavu vrácení zpět, přepište tuto metodu, aby vracela chybu HRESULT.

##  <a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide

Volá se [DoVerbHide](#doverbhide) před tím, než je ovládací prvek skrytý.

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Chcete-li zabránit skrytí ovládacího prvku, přepište tuto metodu, aby vracela chybu HRESULT.

##  <a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate

Volá se [DoVerbInPlaceActivate](#doverbinplaceactivate) před aktivací ovládacího prvku na místě.

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Chcete-li zabránit aktivaci ovládacího prvku na místě, přepište tuto metodu, aby vracela chybu HRESULT.

##  <a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen

Volá se [DoVerbOpen](#doverbopen) před otevřením ovládacího prvku pro úpravy v samostatném okně.

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Chcete-li zabránit tomu, aby byl ovládací prvek otevřen pro úpravy v samostatném okně, přepište tuto metodu, aby vracela chybu HRESULT.

##  <a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow

Volá se [DoVerbShow](#doverbshow) před tím, než se ovládací prvek zviditelní.

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Chcete-li zabránit tomu, aby byl ovládací prvek viditelný, přepište tuto metodu, aby vracela chybu HRESULT.

##  <a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate

Volá se [DoVerbUIActivate](#doverbuiactivate) před aktivací uživatelského rozhraní ovládacího prvku.

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Chcete-li zabránit aktivaci uživatelského rozhraní ovládacího prvku, přepište tuto metodu, aby vracela chybu HRESULT.

##  <a name="setclientsite"></a>IOleObjectImpl::SetClientSite

Instruuje ovládací prvek o jeho klientské lokalitě v kontejneru.

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>Poznámky

Metoda pak vrátí S_OK.

Viz [IOleObject:: SetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setclientsite) v Windows SDK.

##  <a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme

Doporučuje barevné schéma pro aplikaci ovládacího prvku, pokud existuje.

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) v Windows SDK.

##  <a name="setextent"></a>IOleObjectImpl::SetExtent

Nastaví rozsah zobrazované oblasti ovládacího prvku.

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Poznámky

V opačném případě `SetExtent` ukládá hodnotu, na kterou odkazuje `psizel` v datovém členu třídy ovládacího prvku [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Tato hodnota je v jednotkách HIMETRIC (0,01 milimetr na jednotku).

Pokud má datový člen třídy ovládacího prvku [CComControlBase:: m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) hodnotu TRUE, `SetExtent` také ukládá hodnotu, na kterou odkazuje `psizel` v datovém členu třídy ovládacího prvku [CComControlBase:: m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).

Pokud má datový člen třídy ovládacího prvku [CComControlBase:: m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) hodnotu TRUE, `SetExtent` volání `SendOnDataChange` a `SendOnViewChange` pro oznámení všech poradenských umyvadel zaregistrovaných u držitele poradenství, že se změnila velikost ovládacího prvku.

Viz [IOleObject:: SetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setextent) v Windows SDK.

##  <a name="sethostnames"></a>IOleObjectImpl::SetHostNames

Informuje ovládací prvek o názvech aplikace kontejneru a dokumentu kontejneru.

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleObject:: SetHostNames](/windows/win32/api/oleidl/nf-oleidl-ioleobject-sethostnames) v Windows SDK.

##  <a name="setmoniker"></a>IOleObjectImpl::SetMoniker

Oznamuje ovládacímu prvku, co je jeho moniker.

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IOleObject:: SetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setmoniker) v Windows SDK.

##  <a name="unadvise"></a>IOleObjectImpl:: Unadvise

Odstraní Poradní připojení uložené v datovém členu `m_spOleAdviseHolder` třídy ovládacího prvku.

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>Poznámky

Viz [IOleObject:: Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) v Windows SDK.

##  <a name="update"></a>IOleObjectImpl:: Update

Aktualizuje ovládací prvek.

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleObject:: Update](/windows/win32/api/oleidl/nf-oleidl-ioleobject-update) ve Windows SDK.

## <a name="see-also"></a>Viz také

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Rozhraní ovládacích prvků ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
