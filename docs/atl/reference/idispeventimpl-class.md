---
title: Idispeventimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 815a276cb07a91da73acb68a32cceef4b2138325
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093834"
---
# <a name="idispeventimpl-class"></a>Idispeventimpl – třída

Tato třída obsahuje implementaci `IDispatch` metody.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0, 
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```

#### <a name="parameters"></a>Parametry

*nID*<br/>
Jedinečný identifikátor pro zdrojový objekt. Když `IDispEventImpl` je základní třídou pro složeného ovládacího prvku, použijte ID prostředku požadované obsažený ovládací prvek pro tento parametr. V ostatních případech použijte libovolné kladné celé číslo.

*T*<br/>
Třída uživatele, která je odvozena od `IDispEventImpl`.

*pdiid*<br/>
Ukazatel na IID dispinterface události touto třídou implementována. Toto rozhraní musí být definován v knihovně typů, které jsou označeny *plibid*, *wMajor*, a *wMinor*.

*plibid*<br/>
Ukazatel na knihovnu typů, který definuje rozhraní odbavení odkazované *pdiid*. Pokud **& GUID_NULL**, knihovnu typů se načtou z objektu sourcing události.

*wMajor*<br/>
Hlavní verze knihovny typů. Výchozí hodnota je 0.

*wMinor*<br/>
Dílčí verze knihovny typů. Výchozí hodnota je 0.

*tihclass*<br/>
Třída, která slouží ke správě informace o typu *T*. Výchozí hodnota je typu třídy `CComTypeInfoHolder`; nicméně, tento parametr šablony můžete přepsat zadáním třídy typu jiného než `CComTypeInfoHolder`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|Třída používá ke správě informací o typu. Ve výchozím nastavení `CComTypeInfoHolder`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|Vyhledá index funkce pro odeslání zadaný identifikátor.|
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|Mapuje na odpovídající sadu celočíselné hodnoty dispID jednoho člena a volitelná sada názvy argumentů.|
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|Načte informace o typu objektu.|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Získá počet rozhraní typu informací.|
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|Získá základní typ uživatelem definovaného typu.|

## <a name="remarks"></a>Poznámky

`IDispEventImpl` poskytuje způsob implementace dispinterface události bez nutnosti poskytnout implementaci kód pro každé metody/události tohoto rozhraní. `IDispEventImpl` poskytuje implementaci `IDispatch` metody. Stačí zadat implementace, že máte zájem o zpracování událostí.

`IDispEventImpl` funguje ve spojení s mapou jímky událostí ve své třídě pro směrování událostí na odpovídající obslužné rutiny. Chcete-li použít tuto třídu:

Přidat [SINK_ENTRY](composite-control-macros.md#sink_entry) nebo [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) makra mapy událostí jímky pro každou jednotlivou událost pro každý objekt, který chcete zpracovat. Při použití `IDispEventImpl` jako základní třída složeného ovládacího prvku, lze volat [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) při navázání připojení se zdroji událostí pro všechny položky v případě jímky mapy. V ostatních případech, nebo pro větší kontrolu, volání [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) k navázání připojení mezi zdrojovým objektem a základní třídy. Volání [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) přerušit připojení.  

Musí být odvozen od `IDispEventImpl` (pomocí jedinečnou hodnotu pro *nID*) pro každý objekt, pro kterou je potřeba zpracovat události. Základní třídy lze znovu použít, unadvising proti jeden zdrojový objekt pak informacemi pro objekt jiného zdroje, ale maximální počet zdrojové objekty, které mohou být zpracovány jeden objekt v jednom okamžiku je omezený počet `IDispEventImpl` základních tříd.

`IDispEventImpl` nabízí stejné funkce jako [idispeventsimpleimpl –](../../atl/reference/idispeventsimpleimpl-class.md)s výjimkou případů, obdrží z knihovny typů namísto nutnosti uvedené jako ukazatel na typ informace o rozhraní [_atl_func_info –](../../atl/reference/atl-func-info-structure.md) Struktura. Použití `IDispEventSimpleImpl` při můžete nemají knihovnu typů popisující rozhraní událostí nebo chcete vyhnout režii spojenou s použitím knihovny typů.

> [!NOTE]
> `IDispEventImpl` a `IDispEventSimpleImpl` poskytnout vlastní implementaci `IUnknown::QueryInterface` povolení jednotlivých `IDispEventImpl` a `IDispEventSimpleImpl` základní třídy tak, aby fungoval jako samostatné modelu COM identitu zároveň umožní přímý přístup ke členům třídy v váš hlavní objekt modelu COM.

Provádění CE ATL ActiveX událostí jímky pouze podporuje návratové hodnoty typu HRESULT nebo void z vaší obslužné rutiny události; jakákoli jiná návratová hodnota není podporována a její chování není definováno.

Další informace najdete v tématu [podpora IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_IDispEvent`

`_IDispEventLocator`

[Idispeventsimpleimpl –](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="getfuncinfofromid"></a>  IDispEventImpl::GetFuncInfoFromId

Vyhledá index funkce pro odeslání zadaný identifikátor.

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>Parametry

*identifikátor IID*<br/>
[in] Odkaz na ID funkce.

*dispidMember*<br/>
[in] ID odbavení funkce.

*lcid*<br/>
[in] Kontext národního prostředí ID funkce.

*Informace o*<br/>
[in] Struktura označující, jak je funkce volána.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="getidsofnames"></a>  IDispEventImpl::GetIDsOfNames

Namapuje na odpovídající sadu celočíselné hodnoty dispID, které je možné použít v následných voláních na jednoho člena a volitelná sada názvy argumentů [IDispatch::Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke).

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IDispatch::GetIDsOfNames](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) ve Windows SDK.

##  <a name="gettypeinfo"></a>  IDispEventImpl::GetTypeInfo

Načte informace o typu objektu, který lze použít k získání informací o typu pro rozhraní.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Poznámky

##  <a name="gettypeinfocount"></a>  IDispEventImpl::GetTypeInfoCount

Získá počet rozhraní typu informací, které objekt poskytuje (0 nebo 1).

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IDispatch::GetTypeInfoCount](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) ve Windows SDK.

##  <a name="getuserdefinedtype"></a>  IDispEventImpl::GetUserDefinedType

Získá základní typ uživatelem definovaného typu.

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>Parametry

*pTI*<br/>
[in] Ukazatel [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) rozhraní obsahující uživatelem definovaného typu.

*hrt*<br/>
[in] Popisovač pro popis typu, který se má načíst.

### <a name="return-value"></a>Návratová hodnota

Typ variant.

### <a name="remarks"></a>Poznámky

Zobrazit [volání ITypeInfo::GetRefTypeInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo).

##  <a name="idispeventimpl"></a>  IDispEventImpl::IDispEventImpl

Konstruktor Ukládají hodnoty parametrů šablony třídy *plibid*, *pdiid*, *wMajor*, a *wMinor*.

```
IDispEventImpl();
```

##  <a name="tihclass"></a>  IDispEventImpl::tihclass

Tato definice typedef je instance parametru šablony třídy *tihclass*.

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, je třída `CComTypeInfoHolder`. `CComTypeInfoHolder` spravuje informace o typu pro třídu.

## <a name="see-also"></a>Viz také

[_ATL_FUNC_INFO – struktura](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl – třída](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventSimpleImpl – třída](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)