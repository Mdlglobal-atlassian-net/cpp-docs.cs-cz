---
title: Třída IDispEventSimpleImpl
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
ms.openlocfilehash: 779e143094760c7bd868ad33f590f7fd8f004762
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329734"
---
# <a name="idispeventsimpleimpl-class"></a>Třída IDispEventSimpleImpl

Tato třída poskytuje implementace `IDispatch` metod bez získání informací o typu z knihovny typů.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>Parametry

*Nid*<br/>
Jedinečný identifikátor zdrojového objektu. Pokud `IDispEventSimpleImpl` je základní třída pro složený ovládací prvek, použijte ID prostředku požadovaného obsaženého ovládacího prvku pro tento parametr. V ostatních případech použijte libovolné kladné celé číslo.

*T*<br/>
Třída uživatele, která je odvozena `IDispEventSimpleImpl`z .

*pdiid*<br/>
Ukazatel na IID dispinterface události implementované touto třídou.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IDispEventSimpleImpl::Poradit](#advise)|Naváže spojení s výchozím zdrojem událostí.|
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|Naváže spojení se zdrojem událostí.|
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|Přeruší spojení se zdrojem událostí.|
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|Vrátí E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Vrátí E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Vrátí E_NOTIMPL.|
|[IDispEventSimpleImpl::Vyvolat](#invoke)|Volá obslužné rutiny událostí uvedené v mapě jímky událostí.|
|[IDispEventSimpleImpl::Neporadit](#unadvise)|Přeruší připojení s výchozím zdrojem událostí.|

## <a name="remarks"></a>Poznámky

`IDispEventSimpleImpl`Poskytuje způsob implementace rozhraní dispinterface události bez nutnosti zadat kód implementace pro každou metodu nebo událost v tomto rozhraní. `IDispEventSimpleImpl`poskytuje implementace `IDispatch` metod. Potřebujete pouze zadat implementace pro události, které máte zájem o zpracování.

`IDispEventSimpleImpl`pracuje ve spojení s mapou jímky událostí ve vaší třídě směrovat události na příslušnou funkci obslužné rutiny. Chcete-li použít tuto třídu:

- Přidejte [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) makro do mapy jímky událostí pro každou událost u každého objektu, který chcete zpracovat.

- Zadejte informace o typu pro každou událost předáním ukazatele na [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) strukturu jako parametr pro každou položku. Na platformě x86 `_ATL_FUNC_INFO.cc` musí být hodnota CC_CDECL s metodou volání funkce zpětného volání __stdcall.

- Volání [DispEventAdvise](#dispeventadvise) navázat spojení mezi zdrojový objekt a základní třídy.

- Volání [DispEventUnadvise](#dispeventunadvise) přerušit připojení.

Musíte odvodit z `IDispEventSimpleImpl` (pomocí jedinečné hodnoty pro *nID*) pro každý objekt, pro který je třeba zpracovat události. Základní třídu můžete znovu použít tím, že uporadíte proti jednomu zdrojovému objektu a pak budete poskytovat poradenství proti jinému zdrojovému `IDispEventSimpleImpl` objektu, ale maximální počet zdrojových objektů, které mohou být zpracovány jedním objektem najednou, je omezen počtem základních tříd.

`IDispEventSimplImpl`poskytuje stejné funkce jako [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), s výjimkou nezíská informace o typu rozhraní z knihovny typů. Průvodci generují kód `IDispEventImpl`založený pouze `IDispEventSimpleImpl` na , ale můžete jej použít ručním přidáním. Použijte, `IDispEventSimpleImpl` pokud nemáte knihovnu typů popisující rozhraní událostí nebo chcete vyhnout režii spojené s používáním knihovny typů.

> [!NOTE]
> `IDispEventImpl`a `IDispEventSimpleImpl` poskytují vlastní `IUnknown::QueryInterface` implementaci `IDispEventImpl` umožňující `IDispEventSimpleImpl` každé nebo základní třídy fungovat jako samostatná identita COM a zároveň umožňuje přímý přístup ke členům třídy v hlavním objektu COM.

CE ATL implementace jímky událostí ActiveX podporuje pouze vrácené hodnoty typu HRESULT nebo void z metody obslužné rutiny události; všechny ostatní vrácená hodnota není podporována a její chování není definováno.

Další informace naleznete [v tématu Supporting IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="idispeventsimpleimpladvise"></a><a name="advise"></a>IDispEventSimpleImpl::Poradit

Volání této metody navázat spojení se zdrojem událostí reprezentované *pUnk*.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[v] Ukazatel na `IUnknown` rozhraní objektu zdroje události.

### <a name="return-value"></a>Návratová hodnota

S_OK nebo jakékoli selhání HRESULT.

### <a name="remarks"></a>Poznámky

Po navázání připojení budou události vypálené z *pUnk* směrovány na obslužné rutiny ve vaší třídě prostřednictvím mapy jímky událostí.

> [!NOTE]
> Pokud vaše třída pochází `IDispEventSimpleImpl` z více tříd, budete muset rozptýlit volání této metody vymezením volání s konkrétní základní třídy, která vás zajímá.

`Advise`naváže spojení s výchozím zdrojem událostí, získá IID výchozího zdroje událostí objektu určeného [rozhraním AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="idispeventsimpleimpldispeventadvise"></a><a name="dispeventadvise"></a>IDispEventSimpleImpl::DispEventAdvise

Volání této metody navázat spojení se zdrojem událostí reprezentované *pUnk*.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[v] Ukazatel na `IUnknown` rozhraní objektu zdroje události.

*piid*<br/>
Ukazatel na IID objektu zdroje události.

### <a name="return-value"></a>Návratová hodnota

S_OK nebo jakékoli selhání HRESULT.

### <a name="remarks"></a>Poznámky

Následně události vypalované z *pUnk* budou směrovány na obslužné rutiny ve vaší třídě prostřednictvím mapy jímky událostí.

> [!NOTE]
> Pokud vaše třída pochází `IDispEventSimpleImpl` z více tříd, budete muset rozptýlit volání této metody vymezením volání s konkrétní základní třídy, která vás zajímá.

`DispEventAdvise`naváže spojení se zdrojem `pdiid`událostí určeným v .

## <a name="idispeventsimpleimpldispeventunadvise"></a><a name="dispeventunadvise"></a>IDispEventSimpleImpl::DispEventUnadvise

Přeruší spojení se zdrojem událostí reprezentovaného *protokolem pUnk*.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[v] Ukazatel na `IUnknown` rozhraní objektu zdroje události.

*piid*<br/>
Ukazatel na IID objektu zdroje události.

### <a name="return-value"></a>Návratová hodnota

S_OK nebo jakékoli selhání HRESULT.

### <a name="remarks"></a>Poznámky

Jakmile je připojení přerušeno, události již nebudou směrovány na funkce obslužné rutiny uvedené v mapě jímky událostí.

> [!NOTE]
> Pokud vaše třída pochází `IDispEventSimpleImpl` z více tříd, budete muset rozptýlit volání této metody vymezením volání s konkrétní základní třídy, která vás zajímá.

`DispEventAdvise`Přeruší připojení, které bylo navázáno se zdrojem událostí určeným v . `pdiid`

## <a name="idispeventsimpleimplgetidsofnames"></a><a name="getidsofnames"></a>IDispEventSimpleImpl::GetIDsOfNames

Tato implementace `IDispatch::GetIDsOfNames` vrací E_NOTIMPL.

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>Poznámky

Viz [IDispatch::GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) v sadě Windows SDK.

## <a name="idispeventsimpleimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventSimpleImpl::GetTypeInfo

Tato implementace `IDispatch::GetTypeInfo` vrací E_NOTIMPL.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Poznámky

Viz [IDispatch::GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) v sadě Windows SDK.

## <a name="idispeventsimpleimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventSimpleImpl::GetTypeInfoCount

Tato implementace `IDispatch::GetTypeInfoCount` vrací E_NOTIMPL.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Poznámky

Viz [IDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) v sadě Windows SDK.

## <a name="idispeventsimpleimplinvoke"></a><a name="invoke"></a>IDispEventSimpleImpl::Vyvolat

Tato implementace `IDispatch::Invoke` volá obslužné rutiny událostí uvedené v mapě jímky událostí.

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

Viz [iDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

## <a name="idispeventsimpleimplunadvise"></a><a name="unadvise"></a>IDispEventSimpleImpl::Neporadit

Přeruší spojení se zdrojem událostí reprezentovaného *protokolem pUnk*.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[v] Ukazatel na `IUnknown` rozhraní objektu zdroje události.

### <a name="return-value"></a>Návratová hodnota

S_OK nebo jakékoli selhání HRESULT.

### <a name="remarks"></a>Poznámky

Jakmile je připojení přerušeno, události již nebudou směrovány na funkce obslužné rutiny uvedené v mapě jímky událostí.

> [!NOTE]
> Pokud vaše třída pochází `IDispEventSimpleImpl` z více tříd, budete muset rozptýlit volání této metody vymezením volání s konkrétní základní třídy, která vás zajímá.

`Unadvise`Přeruší připojení, které bylo navázáno `pdiid`s výchozím zdrojem událostí určeným v .

`Unavise`přeruší připojení s výchozím zdrojem událostí, získá IID výchozího zdroje událostí objektu určeného [rozhraním AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="see-also"></a>Viz také

[_ATL_FUNC_INFO struktura](../../atl/reference/atl-func-info-structure.md)<br/>
[Třída IDispatchimpl](../../atl/reference/idispatchimpl-class.md)<br/>
[Třída IDispEventImpl](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
