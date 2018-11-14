---
title: Idispeventsimpleimpl – třída
ms.date: 11/04/2016
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
ms.openlocfilehash: b78edf44a200f31a6455c0783e90fb65f5d9af38
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51525324"
---
# <a name="idispeventsimpleimpl-class"></a>Idispeventsimpleimpl – třída

Tato třída obsahuje implementaci `IDispatch` metody bez získání informací o typu z knihovny typů.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>Parametry

*nID*<br/>
Jedinečný identifikátor pro zdrojový objekt. Když `IDispEventSimpleImpl` je základní třídou pro složeného ovládacího prvku, použijte ID prostředku požadované obsažený ovládací prvek pro tento parametr. V ostatních případech použijte libovolné kladné celé číslo.

*T*<br/>
Třída uživatele, která je odvozena od `IDispEventSimpleImpl`.

*pdiid*<br/>
Ukazatel na IID dispinterface události touto třídou implementována.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IDispEventSimpleImpl::Advise](#advise)|Naváže připojení se výchozí zdroj události.|
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|Naváže připojení se zdroji události.|
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|Zruší připojení ke zdroji události.|
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|Vrátí E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Vrátí E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Vrátí E_NOTIMPL.|
|[IDispEventSimpleImpl::Invoke](#invoke)|Volání obslužných rutin událostí uvedené události mapy jímky.|
|[IDispEventSimpleImpl::Unadvise](#unadvise)|Zruší připojení ke zdroji události výchozí.|

## <a name="remarks"></a>Poznámky

`IDispEventSimpleImpl` poskytuje způsob implementace dispinterface události bez nutnosti poskytnout implementaci kód pro každé metody/události tohoto rozhraní. `IDispEventSimpleImpl` poskytuje implementaci `IDispatch` metody. Stačí zadat implementace, že máte zájem o zpracování událostí.

`IDispEventSimpleImpl` funguje ve spojení s mapou jímky událostí ve své třídě pro směrování událostí na odpovídající obslužné rutiny. Chcete-li použít tuto třídu:

- Přidat [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) makra mapy událostí jímky pro každou jednotlivou událost pro každý objekt, který chcete zpracovat.

- Zadejte informace o typu pro každou jednotlivou událost předáním ukazatel [_atl_func_info –](../../atl/reference/atl-func-info-structure.md) strukturu jako parametr pro každou položku. Na x86 platformy, `_ATL_FUNC_INFO.cc` hodnota musí být CC_CDECL pomocí funkce zpětného volání při volání metody __stdcall.

- Volání [DispEventAdvise](#dispeventadvise) k navázání připojení mezi zdrojovým objektem a základní třídy.

- Volání [DispEventUnadvise](#dispeventunadvise) přerušit připojení.

Musí být odvozen od `IDispEventSimpleImpl` (pomocí jedinečnou hodnotu pro *nID*) pro každý objekt, pro kterou je potřeba zpracovat události. Základní třídy lze znovu použít, unadvising proti jeden zdrojový objekt pak informacemi pro objekt jiného zdroje, ale maximální počet zdrojové objekty, které mohou být zpracovány jeden objekt v jednom okamžiku je omezený počet `IDispEventSimpleImpl` základních tříd.

`IDispEventSimplImpl` nabízí stejné funkce jako [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), s výjimkou nezíská typ informace o rozhraní z knihovny typů. Průvodci k vygenerování kódu založeném na pouze `IDispEventImpl`, ale můžete použít `IDispEventSimpleImpl` přidáním kódu ručně. Použití `IDispEventSimpleImpl` když nemáte knihovnu typů popisující rozhraní událostí nebo chcete vyhnout režii spojenou s použitím knihovny typů.

> [!NOTE]
> `IDispEventImpl` a `IDispEventSimpleImpl` poskytnout vlastní implementaci `IUnknown::QueryInterface` povolení jednotlivých `IDispEventImpl` nebo `IDispEventSimpleImpl` základní třídy tak, aby fungoval jako samostatné modelu COM identitu zároveň umožní přímý přístup ke členům třídy v váš hlavní objekt modelu COM.

Provádění CE ATL ActiveX událostí jímky pouze podporuje návratové hodnoty typu HRESULT nebo void z vaší obslužné rutiny události; jakákoli jiná návratová hodnota není podporována a její chování není definováno.

Další informace najdete v tématu [podpora IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="advise"></a>  IDispEventSimpleImpl::Advise

Voláním této metody lze navázat připojení ke zdroji události, která je reprezentována *pUnk*.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Ukazatel `IUnknown` rozhraní objektu zdroje událostí.

### <a name="return-value"></a>Návratová hodnota

Jakékoli neúspěchy hodnotu HRESULT nebo S_OK.

### <a name="remarks"></a>Poznámky

Jakmile se naváže připojení, události vyvolané z *pUnk* budou směrovány do obslužné rutiny ve své třídě, mimo jiné na mapě událostí jímky.

> [!NOTE]
>  Pokud vaše třída odvozena z více `IDispEventSimpleImpl` třídy, musíte pro odstranění dvojznačnosti při volání této metody pomocí oborů volání s určité základní třídy se zajímáte.

`Advise` naváže připojení ke zdroji události výchozí získá identifikátor IID výchozí zdroj události objektu podle [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

##  <a name="dispeventadvise"></a>  IDispEventSimpleImpl::DispEventAdvise

Voláním této metody lze navázat připojení ke zdroji události, která je reprezentována *pUnk*.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Ukazatel `IUnknown` rozhraní objektu zdroje událostí.

*piid*<br/>
Ukazatel na IID objektu zdroje událostí.

### <a name="return-value"></a>Návratová hodnota

Jakékoli neúspěchy hodnotu HRESULT nebo S_OK.

### <a name="remarks"></a>Poznámky

Později, vyvolání událostí z *pUnk* budou směrovány do obslužné rutiny ve své třídě, mimo jiné na mapě událostí jímky.

> [!NOTE]
>  Pokud vaše třída odvozena z více `IDispEventSimpleImpl` třídy, musíte pro odstranění dvojznačnosti při volání této metody pomocí oborů volání s určité základní třídy se zajímáte.

`DispEventAdvise` naváže připojení ke zdroji události podle `pdiid`.

##  <a name="dispeventunadvise"></a>  IDispEventSimpleImpl::DispEventUnadvise

Zruší připojení ke zdroji události, která je reprezentována *pUnk*.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Ukazatel `IUnknown` rozhraní objektu zdroje událostí.

*piid*<br/>
Ukazatel na IID objektu zdroje událostí.

### <a name="return-value"></a>Návratová hodnota

Jakékoli neúspěchy hodnotu HRESULT nebo S_OK.

### <a name="remarks"></a>Poznámky

Po připojení bylo přerušeno, události již nebudou směrovány k funkcím obslužných rutin uvedených v mapě událostí jímky.

> [!NOTE]
>  Pokud vaše třída odvozena z více `IDispEventSimpleImpl` třídy, musíte pro odstranění dvojznačnosti při volání této metody pomocí oborů volání s určité základní třídy se zajímáte.

`DispEventAdvise` přestane fungovat připojení, které bylo vytvořeno podle zdroje události `pdiid`.

##  <a name="getidsofnames"></a>  IDispEventSimpleImpl::GetIDsOfNames

Tato implementace `IDispatch::GetIDsOfNames` vrátí E_NOTIMPL.

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IDispatch::GetIDsOfNames](/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) ve Windows SDK.

##  <a name="gettypeinfo"></a>  IDispEventSimpleImpl::GetTypeInfo

Tato implementace `IDispatch::GetTypeInfo` vrátí E_NOTIMPL.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IDispatch::GetTypeInfo](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfo) ve Windows SDK.

##  <a name="gettypeinfocount"></a>  IDispEventSimpleImpl::GetTypeInfoCount

Tato implementace `IDispatch::GetTypeInfoCount` vrátí E_NOTIMPL.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IDispatch::GetTypeInfoCount](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) ve Windows SDK.

##  <a name="invoke"></a>  IDispEventSimpleImpl::Invoke

Tato implementace `IDispatch::Invoke` volání obslužné rutiny událostí uvedený v případě mapy jímky.

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IDispatch::Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke).

##  <a name="unadvise"></a>  IDispEventSimpleImpl::Unadvise

Zruší připojení ke zdroji události, která je reprezentována *pUnk*.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Ukazatel `IUnknown` rozhraní objektu zdroje událostí.

### <a name="return-value"></a>Návratová hodnota

Jakékoli neúspěchy hodnotu HRESULT nebo S_OK.

### <a name="remarks"></a>Poznámky

Po připojení bylo přerušeno, události již nebudou směrovány k funkcím obslužných rutin uvedených v mapě událostí jímky.

> [!NOTE]
>  Pokud vaše třída odvozena z více `IDispEventSimpleImpl` třídy, musíte pro odstranění dvojznačnosti při volání této metody pomocí oborů volání s určité základní třídy se zajímáte.

`Unadvise` zruší připojení, které bylo vytvořeno výchozí zdroj událostí podle `pdiid`.

`Unavise` zalomení a připojení ke zdroji události výchozí získá identifikátor IID výchozí zdroj události objektu podle [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="see-also"></a>Viz také

[_ATL_FUNC_INFO – struktura](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl – třída](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl – třída](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
