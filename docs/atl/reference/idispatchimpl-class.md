---
title: Idispatchimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f457f47cc04791bc46aaa531d787f4d3f7044e1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055356"
---
# <a name="idispatchimpl-class"></a>Idispatchimpl – třída

Poskytuje výchozí implementaci pro `IDispatch` součástí duální rozhraní.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T,
        const IID* piid= &__uuidof(T),
        const GUID* plibid = &CAtlModule::m_libid,
        WORD wMajor = 1,
        WORD wMinor = 0,
        class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IDispatchImpl : public T
```

#### <a name="parameters"></a>Parametry

*T*<br/>
[in] Duální rozhraní.

*piid*<br/>
[in] Ukazatel na IID *T*.

*plibid*<br/>
[in] Ukazatel na LIBID knihovnu typů, který obsahuje informace o rozhraní. Ve výchozím nastavení je předán typ na úrovni serveru knihovny.

*wMajor*<br/>
[in] Hlavní verze knihovny typů. Výchozí hodnota je 1.

*wMinor*<br/>
[in] Dílčí verze knihovny typů. Výchozí hodnota je 0.

*tihclass*<br/>
[in] Třída, která slouží ke správě informace o typu *T*. Výchozí hodnota je `CComTypeInfoHolder`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|Konstruktor Volání `AddRef` proměnné chráněný člen, který spravuje informace o typu pro duální rozhraní. Volání destruktoru `Release`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Mapuje sadu názvů na odpovídající sadu identifikátorů pro rozesílání.|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Načte informace o typu pro duální rozhraní.|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Určuje, zda je k dispozici pro duální rozhraní informací o typu.|
|[IDispatchImpl::Invoke](#invoke)|Poskytuje přístup k metodám a vlastnostem vystavené duální rozhraní.|

## <a name="remarks"></a>Poznámky

`IDispatchImpl` poskytuje výchozí implementaci pro `IDispatch` součástí žádné duální rozhraní pro objekt. Duální rozhraní je odvozena z `IDispatch` a používá jenom typy kompatibilní služby Automation. Podobně jako dispinterface duální rozhraní podporuje časná vazba a pozdní vazby; duální rozhraní však podporuje také vtable vazby.

Následující příklad ukazuje obvyklá implementace metody `IDispatchImpl`.

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

Ve výchozím nastavení `IDispatchImpl` třídy vyhledá informace o typu *T* v registru. K implementaci rozhraní zrušit, můžete použít `IDispatchImpl` třídy bez přístupu k registru pomocí předdefinovaných číslo_verze. Pokud vytvoříte `IDispatchImpl` objekt, který má hodnotu 0xFFFF *wMajor* a 0xFFFF hodnotu *wMinor*, `IDispatchImpl` třídy načte knihovnu typů ze souboru .dll namísto registru.

`IDispatchImpl` obsahuje statický člen typu `CComTypeInfoHolder` , který spravuje informace o typu pro duální rozhraní. Pokud máte více objektů, které implementují stejné duální rozhraní, pouze jedna instance `CComTypeInfoHolder` se používá.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`T`

`IDispatchImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="getidsofnames"></a>  IDispatchImpl::GetIDsOfNames

Mapuje sadu názvů na odpovídající sadu identifikátorů pro rozesílání.

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

##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo

Načte informace o typu pro duální rozhraní.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IDispatch::GetTypeInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfo) ve Windows SDK.

##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount

Určuje, zda je k dispozici pro duální rozhraní informací o typu.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Poznámky

Zobrazit `IDispatch::GetTypeInfoCount` ve Windows SDK.

##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl

Konstruktor Volání `AddRef` proměnné chráněný člen, který spravuje informace o typu pro duální rozhraní. Volání destruktoru `Release`.

```
IDispatchImpl();
```

##  <a name="invoke"></a>  IDispatchImpl::Invoke

Poskytuje přístup k metodám a vlastnostem vystavené duální rozhraní.

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* pexcepinfo,
    UINT* puArgErr);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IDispatch::Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) ve Windows SDK.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
