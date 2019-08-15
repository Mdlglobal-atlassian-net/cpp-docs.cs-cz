---
title: IDispatchImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
ms.openlocfilehash: 7e9cb903742cdc31c1d9bba2c4aabbb0472407c1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495948"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl – třída

Poskytuje výchozí implementaci pro `IDispatch` část duálního rozhraní.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

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
pro Duální rozhraní.

*piid*<br/>
pro Ukazatel na identifikátor IID *T*.

*plibid*<br/>
pro Ukazatel na LIBID knihovny typů, která obsahuje informace o rozhraní. Ve výchozím nastavení je předána knihovna typů na úrovni serveru.

*wMajor*<br/>
pro Hlavní verze knihovny typů. Ve výchozím nastavení je hodnota 1.

*wMinor*<br/>
pro Vedlejší verze knihovny typů. Ve výchozím nastavení je hodnota 0.

*tihclass*<br/>
pro Třída, která slouží ke správě informací o typu pro *T*. Ve výchozím nastavení je `CComTypeInfoHolder`tato hodnota.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|Konstruktor Volá `AddRef` chráněnou členskou proměnnou, která spravuje informace o typu pro duální rozhraní. Destruktor volá `Release`.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IDispatchImpl:: GetIDsOfNames](#getidsofnames)|Mapuje sadu názvů na odpovídající sadu identifikátorů pro rozesílání.|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Načte informace o typu pro duální rozhraní.|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Určuje, zda jsou pro duální rozhraní k dispozici informace o typu.|
|[IDispatchImpl::Invoke](#invoke)|Poskytuje přístup k metodám a vlastnostem zveřejněným pomocí duálního rozhraní.|

## <a name="remarks"></a>Poznámky

`IDispatchImpl`poskytuje výchozí implementaci pro `IDispatch` část libovolného duálního rozhraní objektu. Duální rozhraní je odvozeno z `IDispatch` a používá pouze typy kompatibilní s automatizací. Podobně jako odesílající rozhraní podporuje duální rozhraní počáteční vazby a pozdní vazby; Nicméně duální rozhraní podporuje také vazbu vtable.

Následující příklad ukazuje typickou implementaci `IDispatchImpl`nástroje.

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

Ve výchozím nastavení `IDispatchImpl` třída vyhledává informace o typu *T* v registru. K implementaci neregistrovaného rozhraní můžete použít `IDispatchImpl` třídu bez přístupu k registru pomocí předdefinovaného čísla verze. Pokud vytvoříte `IDispatchImpl` objekt, který má hodnotu 0xFFFF jako hodnotu pro *wMajor* a 0xFFFF jako hodnotu `IDispatchImpl` pro *wMinor*, třída načte knihovnu typů ze souboru. dll namísto registru.

`IDispatchImpl`obsahuje statického člena typu `CComTypeInfoHolder` , který spravuje informace o typu pro duální rozhraní. Máte-li více objektů, které implementují stejné duální rozhraní, `CComTypeInfoHolder` je použita pouze jedna instance.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`T`

`IDispatchImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="getidsofnames"></a>IDispatchImpl:: GetIDsOfNames

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

Viz [IDispatch:: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) ve Windows SDK.

##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo

Načte informace o typu pro duální rozhraní.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Poznámky

Viz [IDispatch:: GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) ve Windows SDK.

##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount

Určuje, zda jsou pro duální rozhraní k dispozici informace o typu.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Poznámky

Viz `IDispatch::GetTypeInfoCount` v Windows SDK.

##  <a name="idispatchimpl"></a>IDispatchImpl::IDispatchImpl

Konstruktor Volá `AddRef` chráněnou členskou proměnnou, která spravuje informace o typu pro duální rozhraní. Destruktor volá `Release`.

```
IDispatchImpl();
```

##  <a name="invoke"></a>IDispatchImpl:: Invoke

Poskytuje přístup k metodám a vlastnostem zveřejněným pomocí duálního rozhraní.

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

Viz [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) ve Windows SDK.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
