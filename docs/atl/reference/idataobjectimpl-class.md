---
title: Třída iDataObjectimpl
ms.date: 11/04/2016
f1_keywords:
- IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl::DAdvise
- ATLCTL/ATL::IDataObjectImpl::DUnadvise
- ATLCTL/ATL::IDataObjectImpl::EnumDAdvise
- ATLCTL/ATL::IDataObjectImpl::EnumFormatEtc
- ATLCTL/ATL::IDataObjectImpl::FireDataChange
- ATLCTL/ATL::IDataObjectImpl::GetCanonicalFormatEtc
- ATLCTL/ATL::IDataObjectImpl::GetData
- ATLCTL/ATL::IDataObjectImpl::GetDataHere
- ATLCTL/ATL::IDataObjectImpl::QueryGetData
- ATLCTL/ATL::IDataObjectImpl::SetData
helpviewer_keywords:
- data transfer [C++]
- data transfer [C++], Uniform Data Transfer
- IDataObjectImpl class
- IDataObject, ATL implementation
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
ms.openlocfilehash: 618f8248a03297120ae2504bcb30ba8f080b184d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329840"
---
# <a name="idataobjectimpl-class"></a>Třída iDataObjectimpl

Tato třída poskytuje metody pro podporu jednotného přenosu dat a správy připojení.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IDataObjectImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IDataObjectImpl::DAdvise](#dadvise)|Naváže spojení mezi datovým objektem a jímkou doporučení. To umožňuje doporučit jímky přijímat oznámení o změnách v objektu.|
|[IDataObjectImpl::DUnadvise](#dunadvise)|Ukončí připojení dříve navázána prostřednictvím `DAdvise`.|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Vytvoří čítač enumeratator iterate prostřednictvím aktuální poradní připojení.|
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Vytvoří čítač enumeratator `FORMATETC` iterate prostřednictvím struktur podporovaných datový objekt. Implementace ATL vrátí E_NOTIMPL.|
|[iDataObjectImpl::FireDataChange](#firedatachange)|Odešle oznámení o změně zpět do každého jímky poradit.|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Načte logicky `FORMATETC` ekvivalentní strukturu, která je složitější. Implementace ATL vrátí E_NOTIMPL.|
|[iDataObjectImpl::GetData](#getdata)|Přenáší data z datového objektu do klienta. Data jsou popsána `FORMATETC` ve struktuře a `STGMEDIUM` jsou přenášena prostřednictvím struktury.|
|[iDataObjectImpl::GetDataHere](#getdatahere)|Podobně `GetData`jako v , s `STGMEDIUM` výjimkou klientmusí přidělit strukturu. Implementace ATL vrátí E_NOTIMPL.|
|[iDataObjectImpl::QueryGetData](#querygetdata)|Určuje, zda datový objekt `FORMATETC` podporuje určitou strukturu pro přenos dat. Implementace ATL vrátí E_NOTIMPL.|
|[iDataObjectImpl::SetData](#setdata)|Přenáší data z klienta do datového objektu. Implementace ATL vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

Rozhraní [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) poskytuje metody pro podporu jednotného přenosu dat. `IDataObject`používá standardní formát struktury [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) a [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) k načtení a ukládání dat.

`IDataObject`také spravuje připojení poradit jímky pro zpracování oznámení o změně dat. Aby klient mohl přijímat oznámení o změně dat z datového objektu, musí implementovat rozhraní [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) na objekt u objektu nazývaného jímka advise. Když klient pak `IDataObject::DAdvise`volá , je navázáno připojení mezi datový objekt a jímka advise.

Třída `IDataObjectImpl` poskytuje výchozí `IDataObject` implementaci a `IUnknown` implementuje odesláním informací do zařízení s výpisem stavu paměti v sestavení ladění.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="idataobjectimpldadvise"></a><a name="dadvise"></a>IDataObjectImpl::DAdvise

Naváže spojení mezi datovým objektem a jímkou doporučení.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Poznámky

To umožňuje doporučit jímky přijímat oznámení o změnách v objektu.

Chcete-li ukončit připojení, volejte [DUnadvise](#dunadvise).

Viz [IDataObject::DAdvisey](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) v sadě Windows SDK.

## <a name="idataobjectimpldunadvise"></a><a name="dunadvise"></a>IDataObjectImpl::DUnadvise

Ukončí připojení dříve navázána prostřednictvím [DAdvise](#dadvise).

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>Poznámky

Viz [IDataObject::DUnadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) v sadě Windows SDK.

## <a name="idataobjectimplenumdadvise"></a><a name="enumdadvise"></a>IDataObjectImpl::EnumDAdvise

Vytvoří čítač enumeratator iterate prostřednictvím aktuální poradní připojení.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Poznámky

Viz [IDataObject::EnumDAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-enumdadvise) v sadě Windows SDK.

## <a name="idataobjectimplenumformatetc"></a><a name="enumformatetc"></a>IDataObjectImpl::EnumFormatEtc

Vytvoří čítač enumeratator `FORMATETC` iterate prostřednictvím struktur podporovaných datový objekt.

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>Poznámky

Viz [IDataObject::EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

## <a name="idataobjectimplfiredatachange"></a><a name="firedatachange"></a>iDataObjectImpl::FireDataChange

Odešle oznámení o změně zpět do každého jímky advise, který je aktuálně spravován.

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="idataobjectimplgetcanonicalformatetc"></a><a name="getcanonicalformatetc"></a>IDataObjectImpl::GetCanonicalFormatEtc

Načte logicky `FORMATETC` ekvivalentní strukturu, která je složitější.

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [iDataObject::GetCanonicalFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) v sadě Windows SDK.

## <a name="idataobjectimplgetdata"></a><a name="getdata"></a>iDataObjectImpl::GetData

Přenáší data z datového objektu do klienta.

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>Poznámky

Parametr *pformatetcIn* musí určit typ paměťového média TYMED_MFPICT.

Viz [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) v sadě Windows SDK.

## <a name="idataobjectimplgetdatahere"></a><a name="getdatahere"></a>iDataObjectImpl::GetDataHere

Podobně `GetData`jako v , s `STGMEDIUM` výjimkou klientmusí přidělit strukturu.

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IDataObject::GetDataHere](/windows/win32/api/objidl/nf-objidl-idataobject-getdatahere) v sadě Windows SDK.

## <a name="idataobjectimplquerygetdata"></a><a name="querygetdata"></a>iDataObjectImpl::QueryGetData

Určuje, zda datový objekt `FORMATETC` podporuje určitou strukturu pro přenos dat.

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IDataObject::QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) v sadě Windows SDK.

## <a name="idataobjectimplsetdata"></a><a name="setdata"></a>iDataObjectImpl::SetData

Přenáší data z klienta do datového objektu.

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IDataObject::SetData](/windows/win32/api/objidl/nf-objidl-idataobject-setdata) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
