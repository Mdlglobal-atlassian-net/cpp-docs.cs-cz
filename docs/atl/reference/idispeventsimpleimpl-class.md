---
title: IDispEventSimpleImpl – třída
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
ms.openlocfilehash: 3ceb436e4f20a17ecd086fb68f9c1cfdcbe0be3e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495900"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl – třída

Tato třída poskytuje implementace `IDispatch` metod bez získání informací o typu z knihovny typů.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>Parametry

*nID*<br/>
Jedinečný identifikátor zdrojového objektu. Když `IDispEventSimpleImpl` je základní třídou pro složený ovládací prvek, použijte ID prostředku požadovaného ovládacího prvku pro tento parametr. V jiných případech použijte libovolné kladné celé číslo.

*T*<br/>
Třída uživatele, která je odvozena z `IDispEventSimpleImpl`.

*pdiid*<br/>
Ukazatel na IID odesílajícího rozhraní události implementované touto třídou.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IDispEventSimpleImpl:: Advise](#advise)|Naváže připojení k výchozímu zdroji událostí.|
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|Naváže spojení se zdrojem událostí.|
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|Ukončí připojení ke zdroji událostí.|
|[IDispEventSimpleImpl:: GetIDsOfNames](#getidsofnames)|Vrátí E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Vrátí E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Vrátí E_NOTIMPL.|
|[IDispEventSimpleImpl:: Invoke](#invoke)|Volá obslužné rutiny události uvedené v mapě jímky událostí.|
|[IDispEventSimpleImpl::Unadvise](#unadvise)|Ukončí připojení k výchozímu zdroji událostí.|

## <a name="remarks"></a>Poznámky

`IDispEventSimpleImpl`poskytuje způsob implementace odesílajícího protokolu událostí bez nutnosti zadávat implementační kód pro každou metodu nebo událost na daném rozhraní. `IDispEventSimpleImpl`poskytuje implementace `IDispatch` metod. Stačí pouze dodat implementace pro události, které zajímáte o zpracování.

`IDispEventSimpleImpl`pracuje ve spojení s mapou jímky událostí ve vaší třídě pro směrování událostí do příslušné funkce obslužné rutiny. Chcete-li použít tuto třídu:

- Přidejte makro [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) do mapy jímky událostí pro každou událost u každého objektu, který chcete zpracovat.

- Poskytněte informace o typu každé události předáním ukazatele do struktury [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) jako parametru pro každou položku. Na platformě `_ATL_FUNC_INFO.cc` x86 musí být hodnota CC_CDECL pomocí funkce zpětného volání metody __stdcall.

- Zavolejte [DispEventAdvise](#dispeventadvise) k navázání spojení mezi zdrojovým objektem a základní třídou.

- Zavolejte [DispEventUnadvise](#dispeventunadvise) k přerušení připojení.

Musíte odvozovat od `IDispEventSimpleImpl` (pomocí jedinečné hodnoty pro *NID*) pro každý objekt, pro který potřebujete zpracovávat události. Základní třídu lze znovu použít tím, že využijete proti jednomu zdrojovému objektu a potom pro něj budete doporučit jiný zdrojový objekt, ale maximální počet zdrojových objektů, které mohou být zpracovány jediným objektem v jednom okamžiku, je omezen počtem `IDispEventSimpleImpl` základních tříd.

`IDispEventSimplImpl`poskytuje stejné funkce jako [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), s výjimkou, že nezískává informace o typu rozhraní z knihovny typů. Průvodci generují pouze kód, který je `IDispEventImpl`založen pouze na, ale `IDispEventSimpleImpl` můžete použít přidáním kódu ručně. Použijte `IDispEventSimpleImpl` , pokud nemáte knihovnu typů popisující rozhraní události nebo chcete zabránit režii spojené s používáním knihovny typů.

> [!NOTE]
> `IDispEventImpl`a `IDispEventSimpleImpl` poskytněte svou vlastní `IUnknown::QueryInterface` implementaci pro povolení každé `IDispEventImpl` nebo `IDispEventSimpleImpl` základní třídy, aby sloužila jako samostatná identita modelu COM, a současně umožňuje přímý přístup ke členům třídy v hlavním objektu com.

Implementace CE ATL jímka událostí ActiveX podporuje pouze návratové hodnoty typu HRESULT nebo void z metod obslužné rutiny události; jakákoli jiná návratová hodnota není podporována a chování není definováno.

Další informace najdete v tématu [Podpora IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="advise"></a>IDispEventSimpleImpl:: Advise

Zavolejte tuto metodu pro navázání spojení se zdrojem události reprezentovaným *punk*.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
pro Ukazatel na `IUnknown` rozhraní objektu zdroje událostí.

### <a name="return-value"></a>Návratová hodnota

Hodnota S_OK nebo jakákoli neúspěšná hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Po navázání spojení budou události vyvolané z *punk* směrovány do obslužných rutin ve vaší třídě pomocí mapy jímky událostí.

> [!NOTE]
>  Pokud je vaše třída odvozena z `IDispEventSimpleImpl` více tříd, bude nutné nejednoznačnost volání této metody pomocí oboru volání konkrétní základní třídy, kterou vás zajímá.

`Advise`naváže spojení s výchozím zdrojem událostí, získá IID výchozího zdroje události objektu, který určuje [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

##  <a name="dispeventadvise"></a>IDispEventSimpleImpl::D ispEventAdvise

Zavolejte tuto metodu pro navázání spojení se zdrojem události reprezentovaným *punk*.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
pro Ukazatel na `IUnknown` rozhraní objektu zdroje událostí.

*piid*<br/>
Ukazatel na IID zdrojového objektu události.

### <a name="return-value"></a>Návratová hodnota

Hodnota S_OK nebo jakákoli neúspěšná hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Následně se události vyvolané z *punk* budou směrovat do obslužných rutin ve vaší třídě pomocí mapy jímky událostí.

> [!NOTE]
>  Pokud je vaše třída odvozena z `IDispEventSimpleImpl` více tříd, bude nutné nejednoznačnost volání této metody pomocí oboru volání konkrétní základní třídy, kterou vás zajímá.

`DispEventAdvise`naváže spojení se zdrojem události zadaným v `pdiid`.

##  <a name="dispeventunadvise"></a>IDispEventSimpleImpl::D ispEventUnadvise

Ukončí připojení ke zdroji události reprezentovanému pomocí *punk*.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
pro Ukazatel na `IUnknown` rozhraní objektu zdroje událostí.

*piid*<br/>
Ukazatel na IID zdrojového objektu události.

### <a name="return-value"></a>Návratová hodnota

Hodnota S_OK nebo jakákoli neúspěšná hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Po přerušení připojení již události nebudou směrovány do funkcí obslužných rutin uvedených v mapě jímky událostí.

> [!NOTE]
>  Pokud je vaše třída odvozena z `IDispEventSimpleImpl` více tříd, bude nutné nejednoznačnost volání této metody pomocí oboru volání konkrétní základní třídy, kterou vás zajímá.

`DispEventAdvise`zruší připojení, které bylo vytvořeno se zdrojem události zadaným v `pdiid`.

##  <a name="getidsofnames"></a>IDispEventSimpleImpl:: GetIDsOfNames

Tato implementace `IDispatch::GetIDsOfNames` Vrátí E_NOTIMPL.

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>Poznámky

Viz [IDispatch:: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) ve Windows SDK.

##  <a name="gettypeinfo"></a>  IDispEventSimpleImpl::GetTypeInfo

Tato implementace `IDispatch::GetTypeInfo` Vrátí E_NOTIMPL.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Poznámky

Viz [IDispatch:: GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) ve Windows SDK.

##  <a name="gettypeinfocount"></a>  IDispEventSimpleImpl::GetTypeInfoCount

Tato implementace `IDispatch::GetTypeInfoCount` Vrátí E_NOTIMPL.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Poznámky

Viz [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) ve Windows SDK.

##  <a name="invoke"></a>IDispEventSimpleImpl:: Invoke

Tato implementace `IDispatch::Invoke` volá obslužné rutiny události uvedené v mapě jímky událostí.

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

Viz [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

##  <a name="unadvise"></a>IDispEventSimpleImpl:: Unadvise

Ukončí připojení ke zdroji události reprezentovanému pomocí *punk*.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
pro Ukazatel na `IUnknown` rozhraní objektu zdroje událostí.

### <a name="return-value"></a>Návratová hodnota

Hodnota S_OK nebo jakákoli neúspěšná hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Po přerušení připojení již události nebudou směrovány do funkcí obslužných rutin uvedených v mapě jímky událostí.

> [!NOTE]
>  Pokud je vaše třída odvozena z `IDispEventSimpleImpl` více tříd, bude nutné nejednoznačnost volání této metody pomocí oboru volání konkrétní základní třídy, kterou vás zajímá.

`Unadvise`zruší připojení, které bylo vytvořeno s výchozím zdrojem události zadaným v `pdiid`.

`Unavise`zruší připojení s výchozím zdrojem událostí, získá IID výchozího zdroje události objektu, který určuje [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="see-also"></a>Viz také:

[_ATL_FUNC_INFO – struktura](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl – třída](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl – třída](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
