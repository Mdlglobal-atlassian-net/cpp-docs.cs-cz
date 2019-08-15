---
title: IDispEventImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
ms.openlocfilehash: e82a397b6d2abb66f773908c72a287c979e5ae1d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495922"
---
# <a name="idispeventimpl-class"></a>IDispEventImpl – třída

Tato třída poskytuje implementace `IDispatch` metod.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

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
Jedinečný identifikátor zdrojového objektu. Když `IDispEventImpl` je základní třídou pro složený ovládací prvek, použijte ID prostředku požadovaného ovládacího prvku pro tento parametr. V jiných případech použijte libovolné kladné celé číslo.

*T*<br/>
Třída uživatele, která je odvozena z `IDispEventImpl`.

*pdiid*<br/>
Ukazatel na IID odesílajícího rozhraní události implementované touto třídou. Toto rozhraní musí být definováno v knihovně typů, kterou označuje *plibid*, *wMajor*a *wMinor*.

*plibid*<br/>
Ukazatel na knihovnu typů, který definuje rozhraní Dispatch, na které odkazuje *pdiid*. Pokud **&AMP; GUID_NULL**, knihovna typů bude načtena z objektu, který generuje události.

*wMajor*<br/>
Hlavní verze knihovny typů. Výchozí hodnota je 0.

*wMinor*<br/>
Vedlejší verze knihovny typů. Výchozí hodnota je 0.

*tihclass*<br/>
Třída, která slouží ke správě informací o typu pro *T*. Výchozí hodnota je třída typu `CComTypeInfoHolder`. Tento parametr šablony však lze přepsat poskytnutím třídy jiného typu než. `CComTypeInfoHolder`

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Name|Popis|
|----------|-----------------|
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|Třída, která slouží ke správě informací o typu. Ve výchozím nastavení `CComTypeInfoHolder`je to.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[IDispEventImpl:: IDispEventImpl](#idispeventimpl)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|Vyhledá index funkce pro zadaný identifikátor odeslání.|
|[IDispEventImpl:: GetIDsOfNames](#getidsofnames)|Mapuje jednoho člena a volitelnou sadu názvů argumentů na odpovídající sadu celých čísel identifikátorů DISPID.|
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|Načte informace o typu pro objekt.|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Načte počet rozhraní s informacemi o typu.|
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|Načte základní typ uživatelsky definovaného typu.|

## <a name="remarks"></a>Poznámky

`IDispEventImpl`poskytuje způsob implementace odesílajícího protokolu událostí bez nutnosti zadávat implementační kód pro každou metodu nebo událost na daném rozhraní. `IDispEventImpl`poskytuje implementace `IDispatch` metod. Stačí pouze dodat implementace pro události, které zajímáte o zpracování.

`IDispEventImpl`pracuje ve spojení s mapou jímky událostí ve vaší třídě pro směrování událostí do příslušné funkce obslužné rutiny. Chcete-li použít tuto třídu:

Přidejte makro [SINK_ENTRY](composite-control-macros.md#sink_entry) nebo [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) do mapy jímky událostí pro každou událost u každého objektu, který chcete zpracovat. Při použití `IDispEventImpl` jako základní třídy složeného ovládacího prvku můžete volat [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) k navázání a přerušení připojení ke zdrojům událostí pro všechny položky v mapě jímky událostí. V jiných případech nebo pro větší kontrolu volejte [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) k navázání spojení mezi zdrojovým objektem a základní třídou. Zavolejte [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) k přerušení připojení.

Musíte odvozovat od `IDispEventImpl` (pomocí jedinečné hodnoty pro *NID*) pro každý objekt, pro který potřebujete zpracovávat události. Základní třídu lze znovu použít tím, že využijete proti jednomu zdrojovému objektu a potom pro něj budete doporučit jiný zdrojový objekt, ale maximální počet zdrojových objektů, které mohou být zpracovány jediným objektem v jednom okamžiku, je omezen počtem `IDispEventImpl` základních tříd.

`IDispEventImpl`poskytuje stejné funkce jako [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), s výjimkou, že z knihovny typů získává informace o typu rozhraní, a neposkytuje je jako ukazatel na strukturu [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) . Použijte `IDispEventSimpleImpl` , pokud nemáte knihovnu typů popisující rozhraní události nebo chcete zabránit režii spojené s používáním knihovny typů.

> [!NOTE]
> `IDispEventImpl`a `IDispEventSimpleImpl` poskytněte svou vlastní `IUnknown::QueryInterface` implementaci pro povolení každé `IDispEventImpl` a `IDispEventSimpleImpl` základní třídy, aby sloužila jako samostatná identita modelu COM, a současně umožňuje přímý přístup ke členům třídy v hlavním objektu com.

Implementace CE ATL jímka událostí ActiveX podporuje pouze návratové hodnoty typu HRESULT nebo void z metod obslužné rutiny události; jakákoli jiná návratová hodnota není podporována a chování není definováno.

Další informace najdete v tématu [Podpora IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="getfuncinfofromid"></a>  IDispEventImpl::GetFuncInfoFromId

Vyhledá index funkce pro zadaný identifikátor odeslání.

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Odkaz na ID funkce

*dispidMember*<br/>
pro ID odeslání funkce

*lcid*<br/>
pro Kontext národního prostředí ID funkce.

*info*<br/>
pro Struktura označující, jak je funkce volána.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="getidsofnames"></a>IDispEventImpl:: GetIDsOfNames

Provede mapování jednoho člena a volitelné sady názvů argumentů na odpovídající sadu celých čísel identifikátorů DISPID, které lze použít při následných voláních rozhraní [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Poznámky

Viz [IDispatch:: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) ve Windows SDK.

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

Viz [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) ve Windows SDK.

##  <a name="getuserdefinedtype"></a>  IDispEventImpl::GetUserDefinedType

Načte základní typ uživatelsky definovaného typu.

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>Parametry

*pTI*<br/>
pro Ukazatel na rozhraní [volání ITypeInfo](/windows/win32/api/oaidl/nn-oaidl-itypeinfo) obsahující uživatelsky definovaný typ.

*hrt*<br/>
pro Popisovač pro popis typu, který se má načíst.

### <a name="return-value"></a>Návratová hodnota

Typ variant.

### <a name="remarks"></a>Poznámky

Viz [volání ITypeInfo:: GetRefTypeInfo](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo).

##  <a name="idispeventimpl"></a>IDispEventImpl:: IDispEventImpl

Konstruktor Ukládá hodnoty parametrů šablony třídy *plibid*, *pdiid*, *wMajor*a *wMinor*.

```
IDispEventImpl();
```

##  <a name="tihclass"></a>IDispEventImpl:: tihclass

Tato definice typedef je instancí parametru šablony třídy *tihclass*.

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je `CComTypeInfoHolder`třída. `CComTypeInfoHolder`spravuje informace o typu pro třídu.

## <a name="see-also"></a>Viz také:

[_ATL_FUNC_INFO – struktura](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl – třída](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventSimpleImpl – třída](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
