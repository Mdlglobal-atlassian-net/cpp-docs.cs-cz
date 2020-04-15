---
title: Třída IOleObjectImpl
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
ms.openlocfilehash: 86d82aea2e92eb99903284abe4ac03478369616c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326529"
---
# <a name="ioleobjectimpl-class"></a>Třída IOleObjectImpl

Tato třída `IUnknown` implementuje a je hlavní rozhraní, jehož prostřednictvím kontejner komunikuje s ovládacím prvkem.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IOleObjectImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[iOleObjectimpl::Poradit](#advise)|Naváže poradní připojení s ovládacím prvkem.|
|[iOleObjectImpl::Zavřít](#close)|Změní stav ovládacího prvku z spuštěného na načtený.|
|[IOleObjectImpl::DoVerb](#doverb)|Říká ovládacímu prvku provést jednu z jeho výčtu akce.|
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Říká ovládacímu prvku, aby zrušil všechny stavy, které udržuje.|
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Říká ovládacímu prvku odebrat jeho uživatelské rozhraní ze zobrazení.|
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Spustí ovládací prvek a nainstaluje jeho okno, ale nenainstaluje uživatelské rozhraní ovládacího prvku.|
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|Způsobí, že ovládací prvek bude open-edited v samostatném okně.|
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|Provede zadanou akci, když uživatel poklekne na ovládací prvek. Ovládací prvek definuje akci, obvykle k aktivaci ovládacího prvku na místě.|
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Zobrazí nově vložený ovládací prvek uživateli.|
|[IOleObjectImpl::DoVerbUIAktivovat](#doverbuiactivate)|Aktivuje ovládací prvek na místě a zobrazuje uživatelské rozhraní ovládacího prvku, například nabídky a panely nástrojů.|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Vyjmenovává poradní připojení ovládacího prvku.|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Vyjmenovává akce pro ovládací prvek.|
|[iOleObjectimpl::GetClientSite](#getclientsite)|Načte klientskou lokalitu ovládacího prvku.|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Načte data ze schránky. Implementace ATL vrátí E_NOTIMPL.|
|[iOleObjectimpl::GetExtent](#getextent)|Načte rozsah oblasti zobrazení ovládacího prvku.|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Načte stav ovládacího prvku.|
|[IOleObjectImpl::GetMoniker](#getmoniker)|Načte zástupné spoje ovládacího prvku. Implementace ATL vrátí E_NOTIMPL.|
|[iOleObjectimpl::GetUserClassID](#getuserclassid)|Načte identifikátor třídy ovládacího prvku.|
|[iOleObjectimpl::GetUserType](#getusertype)|Načte název uživatelského typu ovládacího prvku.|
|[IOleObjectImpl::InitFromData](#initfromdata)|Inicializuje ovládací prvek z vybraných dat. Implementace ATL vrátí E_NOTIMPL.|
|[iOleObjectimpl::Aktuální](#isuptodate)|Zkontroluje, zda je ovládací prvek aktuální. Implementace ATL vrátí S_OK.|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Volána [DoVerbDiscardUndo](#doverbdiscardundo) po zahození stavu vrátit.|
|[iOleObjectimpl::OnPostVerbHide](#onpostverbhide)|Volána [DoVerbHide](#doverbhide) po ovládacíprvek je skrytý.|
|[iOleObjectimpl::onpostverbinplaceActivate](#onpostverbinplaceactivate)|Volat [DoVerbInPlaceAktivovat](#doverbinplaceactivate) po aktivaci ovládacího prvku na místě.|
|[iOleObjectimpl::OnpostverbOpen](#onpostverbopen)|Volána [DoVerbOpen](#doverbopen) po otevření ovládacího prvku pro úpravy v samostatném okně.|
|[iOleObjectimpl::OnpostverbShow](#onpostverbshow)|Volána [DoVerbShow](#doverbshow) po zviditelnění ovládacího prvku.|
|[iOleObjectimpl::onpostverbuiActivate](#onpostverbuiactivate)|Volána [DoVerbUIActivate](#doverbuiactivate) po aktivaci uživatelského rozhraní ovládacího prvku.|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Volána [DoVerbDiscardUndo](#doverbdiscardundo) před zahození stavu vrátit.|
|[iOleObjectimpl::OnPreVerbHide](#onpreverbhide)|Volána [DoVerbHide](#doverbhide) před ovládací prvek je skrytý.|
|[iOleObjectimpl::onpreverbinplaceActivate](#onpreverbinplaceactivate)|Volat [DoVerbInPlaceActivate](#doverbinplaceactivate) před ovládací prvek je aktivován na místě.|
|[iOleObjectimpl::onpreverbopen](#onpreverbopen)|Volána [DoVerbOpen](#doverbopen) před otevřením ovládacího prvku pro úpravy v samostatném okně.|
|[iOleObjectimpl::onpreverbshow](#onpreverbshow)|Volána [DoVerbShow](#doverbshow) před ovládací prvek byl zviditelněn.|
|[iOleObjectimpl::onpreverbuiActivate](#onpreverbuiactivate)|Volána [DoVerbUIActivate](#doverbuiactivate) před aktivací uživatelského rozhraní ovládacího prvku.|
|[iOleObjectImpl::SetClientSite](#setclientsite)|Informuje o ovládacím prvku o jeho klientské lokality v kontejneru.|
|[iOleObjectimpl::Setcolorscheme](#setcolorscheme)|Doporučuje barevné schéma pro aplikaci ovládacího prvku, pokud existuje. Implementace ATL vrátí E_NOTIMPL.|
|[iOleObjectimpl:SetExtent](#setextent)|Nastaví rozsah oblasti zobrazení ovládacího prvku.|
|[iOleObjectimpl::SetHostNames](#sethostnames)|Říká ovládacímu prvku názvy kontejneru aplikace a kontejneru dokumentu.|
|[IOleObjectImpl::SetMoniker](#setmoniker)|Říká ovládacímu prvku, co je jeho zástupná skupina. Implementace ATL vrátí E_NOTIMPL.|
|[IOleObjectImpl::Nerada](#unadvise)|Odstraní poradní připojení s ovládacím prvkem.|
|[iOleObjectImpl::Aktualizovat](#update)|Aktualizuje ovládací prvek. Implementace ATL vrátí S_OK.|

## <a name="remarks"></a>Poznámky

[Rozhraní IOleObject](/windows/win32/api/oleidl/nn-oleidl-ioleobject) je hlavní rozhraní, jehož prostřednictvím kontejner komunikuje s ovládacím prvkem. Třída `IOleObjectImpl` poskytuje výchozí implementaci tohoto rozhraní `IUnknown` a implementuje odesláním informací do zařízení s výpisem stavu paměti v sestavení ladění.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="ioleobjectimpladvise"></a><a name="advise"></a>iOleObjectimpl::Poradit

Naváže poradní připojení s ovládacím prvkem.

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Poznámky

Viz [IOleObject::Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) v sadě Windows SDK.

## <a name="ioleobjectimplclose"></a><a name="close"></a>iOleObjectImpl::Zavřít

Změní stav ovládacího prvku z spuštěného na načtený.

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>Poznámky

Deaktivuje ovládací prvek a zničí okno ovládacího prvku, pokud existuje. Pokud je datový člen třídy ovládacího prvku [CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) TRUE a parametr *dwSaveOption* je OLECLOSE_SAVEIFDIRTY nebo OLECLOSE_PROMPTSAVE, vlastnosti ovládacího prvku se před zavřením uloží.

Ukazatele uchovávané v datových členech třídy ovládacího prvku [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) a [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) jsou uvolněny a datové členy [CComControlBase:::m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)a [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) jsou nastaveny na HODNOTU FALSE.

Viz [IOleObject::Close](/windows/win32/api/oleidl/nf-oleidl-ioleobject-close) v sadě Windows SDK.

## <a name="ioleobjectimpldoverb"></a><a name="doverb"></a>IOleObjectImpl::DoVerb

Říká ovládacímu prvku provést jednu z jeho výčtu akce.

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

V závislosti na `iVerb`hodnotě aplikace `DoVerb` se nazývá jedna z pomocných funkcí atl takto:

|*iSponož* Hodnotu|DoVerb pomocná funkce s názvem|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUnod](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoverbinplaceAktivovat](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimární](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoverbuiAktivovat](#doverbuiactivate)|

Viz [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) v sadě Windows SDK.

## <a name="ioleobjectimpldoverbdiscardundo"></a><a name="doverbdiscardundo"></a>IOleObjectImpl::DoVerbDiscardUndo

Říká ovládacímu prvku, aby zrušil všechny stavy, které udržuje.

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*č. PosRec*<br/>
[v] Ukazatel na obdélník kontejneru chce ovládací prvek čerpat do.

*hwndParent*<br/>
[v] Popisovač okna obsahující ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

## <a name="ioleobjectimpldoverbhide"></a><a name="doverbhide"></a>IOleObjectImpl::DoVerbHide

Deaktivuje a odebere uživatelské rozhraní ovládacího prvku a skryje ovládací prvek.

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*č. PosRec*<br/>
[v] Ukazatel na obdélník kontejneru chce ovládací prvek čerpat do.

*hwndParent*<br/>
[v] Popisovač okna obsahující ovládací prvek. Nepoužívá se v implementaci ATL.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

## <a name="ioleobjectimpldoverbinplaceactivate"></a><a name="doverbinplaceactivate"></a>IOleObjectImpl::DoVerbInPlaceActivate

Spustí ovládací prvek a nainstaluje jeho okno, ale nenainstaluje uživatelské rozhraní ovládacího prvku.

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*č. PosRec*<br/>
[v] Ukazatel na obdélník kontejneru chce ovládací prvek čerpat do.

*hwndParent*<br/>
[v] Popisovač okna obsahující ovládací prvek. Nepoužívá se v implementaci ATL.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Aktivuje ovládací prvek na místě voláním [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). Pokud datový člen `m_bWindowOnly` třídy ovládacího `DoVerbInPlaceActivate` prvku není TRUE, nejprve se pokusí aktivovat ovládací prvek jako ovládací prvek bez oken (možné pouze v případě, že kontejner podporuje [IOleInPlaceSiteWindowless).](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) Pokud se to nezdaří, funkce se pokusí aktivovat ovládací prvek s rozšířenými funkcemi (možné pouze v případě, že kontejner podporuje [IOleInPlaceSiteEx).](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex) Pokud se to nezdaří, funkce se pokusí aktivovat ovládací prvek bez rozšířených funkcí (možné pouze v případě, že kontejner podporuje [IOleInPlaceSite).](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite) Pokud aktivace proběhne úspěšně, funkce upozorní kontejner, že byl aktivován ovládací prvek.

## <a name="ioleobjectimpldoverbopen"></a><a name="doverbopen"></a>IOleObjectImpl::DoVerbOpen

Způsobí, že ovládací prvek bude open-edited v samostatném okně.

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*č. PosRec*<br/>
[v] Ukazatel na obdélník kontejneru chce ovládací prvek čerpat do.

*hwndParent*<br/>
[v] Popisovač okna obsahující ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

## <a name="ioleobjectimpldoverbprimary"></a><a name="doverbprimary"></a>IOleObjectImpl::DoVerbPrimary

Definuje akci přijatou při poklepání uživatele na ovládací prvek.

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>Parametry

*č. PosRec*<br/>
[v] Ukazatel na obdélník kontejneru chce ovládací prvek čerpat do.

*hwndParent*<br/>
[v] Popisovač okna obsahující ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení nastavte zobrazení stránek vlastností. Můžete přepsat ve třídě ovládacího prvku vyvolat jiné chování při poklepání; můžete například přehrát video nebo přejít na místo aktivní.

## <a name="ioleobjectimpldoverbshow"></a><a name="doverbshow"></a>IOleObjectImpl::DoVerbShow

Říká kontejneru, aby ovládací prvek viditelný.

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*č. PosRec*<br/>
[v] Ukazatel na obdélník kontejneru chce ovládací prvek čerpat do.

*hwndParent*<br/>
[v] Popisovač okna obsahující ovládací prvek. Nepoužívá se v implementaci ATL.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ioleobjectimpldoverbuiactivate"></a><a name="doverbuiactivate"></a>IOleObjectImpl::DoVerbUIAktivovat

Aktivuje uživatelské rozhraní ovládacího prvku a upozorní kontejner, že jeho nabídky jsou nahrazovány složenými nabídkami.

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parametry

*č. PosRec*<br/>
[v] Ukazatel na obdélník kontejneru chce ovládací prvek čerpat do.

*hwndParent*<br/>
[v] Popisovač okna obsahující ovládací prvek. Nepoužívá se v implementaci ATL.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

## <a name="ioleobjectimplenumadvise"></a><a name="enumadvise"></a>IOleObjectImpl::EnumAdvise

Poskytuje výčet registrovaných poradní připojení pro tento ovládací prvek.

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>Poznámky

Viz [IOleObject::EnumAdvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumadvise) v sadě Windows SDK.

## <a name="ioleobjectimplenumverbs"></a><a name="enumverbs"></a>IOleObjectImpl::EnumVerbs

Poskytuje výčet registrovaných akcí (sloves) pro tento `OleRegEnumVerbs`ovládací prvek voláním .

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>Poznámky

Do souboru RGS projektu můžete přidat slovesa. Viz například CIRCCTL. RGS ve vzorku [CIRC.](../../overview/visual-cpp-samples.md)

Viz [IOleObject::EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs) v sadě Windows SDK.

## <a name="ioleobjectimplgetclientsite"></a><a name="getclientsite"></a>iOleObjectimpl::GetClientSite

Vloží ukazatel v datovém členu třídy ovládacího prvku [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) do *ppClientSite* a nastaví počet odkazů na ukazatel.

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>Poznámky

Viz [IOleObject::GetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclientsite) v sadě Windows SDK.

## <a name="ioleobjectimplgetclipboarddata"></a><a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData

Načte data ze schránky.

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IOleObject::GetClipboardData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) v sadě Windows SDK.

## <a name="ioleobjectimplgetextent"></a><a name="getextent"></a>iOleObjectimpl::GetExtent

Načte velikost zobrazení běžícího ovládacího prvku v jednotkách HIMETRIC (0,01 milimetru na jednotku).

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Poznámky

Velikost je uložena v datovém členu třídy ovládacího prvku [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

Viz [IOleObject::GetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getextent) v sadě Windows SDK.

## <a name="ioleobjectimplgetmiscstatus"></a><a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus

Vrátí ukazatel na registrované informace o `OleRegGetMiscStatus`stavu ovládacího prvku voláním .

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>Poznámky

Informace o stavu zahrnují chování podporované daty ovládacího prvku a prezentace. Do souboru RGS projektu můžete přidat informace o stavu.

Viz [IOleObject::GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) v sadě Windows SDK.

## <a name="ioleobjectimplgetmoniker"></a><a name="getmoniker"></a>IOleObjectImpl::GetMoniker

Načte zástupné spoje ovládacího prvku.

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IOleObject::GetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmoniker) v sadě Windows SDK.

## <a name="ioleobjectimplgetuserclassid"></a><a name="getuserclassid"></a>iOleObjectimpl::GetUserClassID

Vrátí identifikátor třídy ovládacího prvku.

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>Poznámky

Viz [IOleObject::GetUserClassID](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getuserclassid) v sadě Windows SDK.

## <a name="ioleobjectimplgetusertype"></a><a name="getusertype"></a>iOleObjectimpl::GetUserType

Vrátí název uživatelského typu ovládacího `OleRegGetUserType`prvku voláním .

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>Poznámky

Název uživatelského typu se používá pro zobrazení v elementech uživatelských rozhraní, jako jsou nabídky a dialogová okna. Název typu uživatele můžete změnit v souboru RGS projektu.

Viz [IOleObject::GetUserType](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getusertype) v sadě Windows SDK.

## <a name="ioleobjectimplinitfromdata"></a><a name="initfromdata"></a>IOleObjectImpl::InitFromData

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

Viz [IOleObject::InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) v sadě Windows SDK.

## <a name="ioleobjectimplisuptodate"></a><a name="isuptodate"></a>iOleObjectimpl::Aktuální

Zkontroluje, zda je ovládací prvek aktuální.

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleObject::IsUpToDate](/windows/win32/api/oleidl/nf-oleidl-ioleobject-isuptodate) v sadě Windows SDK.

## <a name="ioleobjectimplonpostverbdiscardundo"></a><a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo

Volána [DoVerbDiscardUndo](#doverbdiscardundo) po zahození stavu vrátit.

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu s kódem, který chcete spustit po zahození stavu vrátit.

## <a name="ioleobjectimplonpostverbhide"></a><a name="onpostverbhide"></a>iOleObjectimpl::OnPostVerbHide

Volána [DoVerbHide](#doverbhide) po ovládacíprvek je skrytý.

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu s kódem, který chcete spustit po ovládací prvek je skrytý.

## <a name="ioleobjectimplonpostverbinplaceactivate"></a><a name="onpostverbinplaceactivate"></a>iOleObjectimpl::onpostverbinplaceActivate

Volat [DoVerbInPlaceAktivovat](#doverbinplaceactivate) po aktivaci ovládacího prvku na místě.

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu s kódem, který chcete spustit po aktivaci ovládacího prvku na místě.

## <a name="ioleobjectimplonpostverbopen"></a><a name="onpostverbopen"></a>iOleObjectimpl::OnpostverbOpen

Volána [DoVerbOpen](#doverbopen) po otevření ovládacího prvku pro úpravy v samostatném okně.

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu s kódem, který chcete spustit po otevření ovládacího prvku pro úpravy v samostatném okně.

## <a name="ioleobjectimplonpostverbshow"></a><a name="onpostverbshow"></a>iOleObjectimpl::OnpostverbShow

Volána [DoVerbShow](#doverbshow) po zviditelnění ovládacího prvku.

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu s kódem, který chcete spustit po ovládacíprvek byl zviditelněn.

## <a name="ioleobjectimplonpostverbuiactivate"></a><a name="onpostverbuiactivate"></a>iOleObjectimpl::onpostverbuiActivate

Volána [DoVerbUIActivate](#doverbuiactivate) po aktivaci uživatelského rozhraní ovládacího prvku.

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu s kódem, který chcete spustit po aktivaci uživatelského rozhraní ovládacího prvku.

## <a name="ioleobjectimplonpreverbdiscardundo"></a><a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo

Volána [DoVerbDiscardUndo](#doverbdiscardundo) před zahození stavu vrátit.

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Chcete-li zabránit zahození stavu zpět, přepište tuto metodu a vraťte chybu HRESULT.

## <a name="ioleobjectimplonpreverbhide"></a><a name="onpreverbhide"></a>iOleObjectimpl::OnPreVerbHide

Volána [DoVerbHide](#doverbhide) před ovládací prvek je skrytý.

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Chcete-li zabránit skryté ovládací prvek, přepsat tuto metodu vrátit chybu HRESULT.

## <a name="ioleobjectimplonpreverbinplaceactivate"></a><a name="onpreverbinplaceactivate"></a>iOleObjectimpl::onpreverbinplaceActivate

Volat [DoVerbInPlaceActivate](#doverbinplaceactivate) před ovládací prvek je aktivován na místě.

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Chcete-li zabránit aktivaci ovládacího prvku na místě, přepište tuto metodu a vraťte chybu HRESULT.

## <a name="ioleobjectimplonpreverbopen"></a><a name="onpreverbopen"></a>iOleObjectimpl::onpreverbopen

Volána [DoVerbOpen](#doverbopen) před otevřením ovládacího prvku pro úpravy v samostatném okně.

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Chcete-li zabránit otevření ovládacího prvku pro úpravy v samostatném okně, přepište tuto metodu a vraťte chybu HRESULT.

## <a name="ioleobjectimplonpreverbshow"></a><a name="onpreverbshow"></a>iOleObjectimpl::onpreverbshow

Volána [DoVerbShow](#doverbshow) před ovládací prvek byl zviditelněn.

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Chcete-li zabránit zobrazení ovládacího prvku, přepište tuto metodu a vraťte chybu HRESULT.

## <a name="ioleobjectimplonpreverbuiactivate"></a><a name="onpreverbuiactivate"></a>iOleObjectimpl::onpreverbuiActivate

Volána [DoVerbUIActivate](#doverbuiactivate) před aktivací uživatelského rozhraní ovládacího prvku.

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Chcete-li zabránit aktivaci uživatelského rozhraní ovládacího prvku, přepište tuto metodu a vraťte chybu HRESULT.

## <a name="ioleobjectimplsetclientsite"></a><a name="setclientsite"></a>iOleObjectImpl::SetClientSite

Informuje o ovládacím prvku o jeho klientské lokality v kontejneru.

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>Poznámky

Metoda pak vrátí S_OK.

Viz [IOleObject::SetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setclientsite) v sadě Windows SDK.

## <a name="ioleobjectimplsetcolorscheme"></a><a name="setcolorscheme"></a>iOleObjectimpl::Setcolorscheme

Doporučuje barevné schéma pro aplikaci ovládacího prvku, pokud existuje.

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IOleObject::SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) v sadě Windows SDK.

## <a name="ioleobjectimplsetextent"></a><a name="setextent"></a>iOleObjectimpl:SetExtent

Nastaví rozsah oblasti zobrazení ovládacího prvku.

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Poznámky

V `SetExtent` opačném případě uloží `psizel` hodnotu, na kterou poukazuje v datovém členu třídy ovládacího prvku [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Tato hodnota je v jednotkách HIMETRIC (0,01 milimetru na jednotku).

Pokud je datový člen třídy ovládacího prvku `SetExtent` [CComControlBase:::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) TRUE, uloží také hodnotu, na kterou upozorňujete v datovém `psizel` členu třídy ovládacího prvku [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).

Pokud je datový člen třídy ovládacího prvku `SetExtent` [CComControlBase:::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) TRUE, volá `SendOnDataChange` a `SendOnViewChange` upozorní všechny poradní jímky registrované u držitele advise, že se změnila velikost ovládacího prvku.

Viz [IOleObject::SetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setextent) v sadě Windows SDK.

## <a name="ioleobjectimplsethostnames"></a><a name="sethostnames"></a>iOleObjectimpl::SetHostNames

Říká ovládacímu prvku názvy kontejneru aplikace a kontejneru dokumentu.

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleObject::SetHostNames](/windows/win32/api/oleidl/nf-oleidl-ioleobject-sethostnames) v sadě Windows SDK.

## <a name="ioleobjectimplsetmoniker"></a><a name="setmoniker"></a>IOleObjectImpl::SetMoniker

Říká ovládacímu prvku, co je jeho zástupná skupina.

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IOleObject::SetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setmoniker) v sadě Windows SDK.

## <a name="ioleobjectimplunadvise"></a><a name="unadvise"></a>IOleObjectImpl::Nerada

Odstraní poradní připojení uložené v datovém `m_spOleAdviseHolder` členu třídy ovládacího prvku.

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>Poznámky

Viz [IOleObject::Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) v sadě Windows SDK.

## <a name="ioleobjectimplupdate"></a><a name="update"></a>iOleObjectImpl::Aktualizovat

Aktualizuje ovládací prvek.

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleObject::Update](/windows/win32/api/oleidl/nf-oleidl-ioleobject-update) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Třída CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Rozhraní ovládacích prvků ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
