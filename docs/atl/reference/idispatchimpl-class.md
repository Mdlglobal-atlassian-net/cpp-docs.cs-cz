---
title: Třída IDispatchimpl
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
ms.openlocfilehash: 3b3899a0c4a49aa7fb1bd82af330f5f1cc7329c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329798"
---
# <a name="idispatchimpl-class"></a>Třída IDispatchimpl

Poskytuje výchozí implementaci `IDispatch` pro část duálního rozhraní.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

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
[v] Duální rozhraní.

*piid*<br/>
[v] Ukazatel na IID *T*.

*plibid*<br/>
[v] Ukazatel na LIBID knihovny typů, která obsahuje informace o rozhraní. Ve výchozím nastavení je předána knihovna typů na úrovni serveru.

*wMajor*<br/>
[v] Hlavní verze knihovny typů. Ve výchozím nastavení je hodnota 1.

*wMenší*<br/>
[v] Dílčí verze knihovny typů. Ve výchozím nastavení je hodnota 0.

*tihclass*<br/>
[v] Třída slouží ke správě informací o typu pro *T*. Ve výchozím nastavení `CComTypeInfoHolder`je hodnota .

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[IDispatchimpl::IDispatchimpl](#idispatchimpl)|Konstruktor Volá `AddRef` chráněnou členovou proměnnou, která spravuje informace o typu pro duální rozhraní. Destruktor `Release`volá .|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Mapuje sadu názvů na odpovídající sadu identifikátorů pro rozesílání.|
|[IDispatchimpl::GetTypeInfo](#gettypeinfo)|Načte informace o typu pro duální rozhraní.|
|[iDispatchimpl::GetTypeInfoCount](#gettypeinfocount)|Určuje, zda jsou pro duální rozhraní k dispozici informace o typu.|
|[IDispatchimpl::Vyvolat](#invoke)|Poskytuje přístup k metodám a vlastnostem vystaveným duálním rozhraním.|

## <a name="remarks"></a>Poznámky

`IDispatchImpl`poskytuje výchozí implementaci `IDispatch` pro část libovolného duálního rozhraní na objektu. Duální rozhraní `IDispatch` je odvozeno a používá pouze typy kompatibilní s automatizací. Stejně jako dispinterface, duální rozhraní podporuje včasné vazby a pozdní vazby; však duální rozhraní také podporuje vtable vazby.

Následující příklad ukazuje typické `IDispatchImpl`implementace .

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

Ve výchozím `IDispatchImpl` nastavení třída vyhledá informace o typu *T* v registru. Chcete-li implementovat neregistrované rozhraní, můžete použít třídu `IDispatchImpl` bez přístupu k registru pomocí předdefinovaného čísla verze. Pokud vytvoříte `IDispatchImpl` objekt, který má 0xFFFF jako hodnotu *wMajor* a 0xFFFF jako hodnotu pro *wMinor*, `IDispatchImpl` třída načte knihovnu typů ze souboru DLL namísto registru.

`IDispatchImpl`obsahuje statický člen `CComTypeInfoHolder` typu, který spravuje informace o typu pro duální rozhraní. Pokud máte více objektů, které implementují stejné `CComTypeInfoHolder` duální rozhraní, použije se pouze jedna instance.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`T`

`IDispatchImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="idispatchimplgetidsofnames"></a><a name="getidsofnames"></a>IDispatchImpl::GetIDsOfNames

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

Viz [IDispatch::GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) v sadě Windows SDK.

## <a name="idispatchimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispatchimpl::GetTypeInfo

Načte informace o typu pro duální rozhraní.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Poznámky

Viz [IDispatch::GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) v sadě Windows SDK.

## <a name="idispatchimplgettypeinfocount"></a><a name="gettypeinfocount"></a>iDispatchimpl::GetTypeInfoCount

Určuje, zda jsou pro duální rozhraní k dispozici informace o typu.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Poznámky

Viz `IDispatch::GetTypeInfoCount` sada Windows SDK.

## <a name="idispatchimplidispatchimpl"></a><a name="idispatchimpl"></a>IDispatchimpl::IDispatchimpl

Konstruktor Volá `AddRef` chráněnou členovou proměnnou, která spravuje informace o typu pro duální rozhraní. Destruktor `Release`volá .

```
IDispatchImpl();
```

## <a name="idispatchimplinvoke"></a><a name="invoke"></a>IDispatchimpl::Vyvolat

Poskytuje přístup k metodám a vlastnostem vystaveným duálním rozhraním.

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

Viz [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
