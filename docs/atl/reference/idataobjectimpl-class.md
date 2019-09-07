---
title: IDataObjectImpl – třída
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
ms.openlocfilehash: 80b5dfacd5f0c8b0deb8455a59d3f71b73a35ba0
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739561"
---
# <a name="idataobjectimpl-class"></a>IDataObjectImpl – třída

Tato třída poskytuje metody pro podporu jednotných Přenos dat a správu připojení.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IDataObjectImpl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IDataObjectImpl::D Advise](#dadvise)|Naváže spojení mezi datovým objektem a jímkou oznámení. To umožňuje, aby jímka Advise přijímala oznámení o změnách v objektu.|
|[IDataObjectImpl::DUnadvise](#dunadvise)|Ukončí připojení, které bylo dříve vytvořeno `DAdvise`prostřednictvím.|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Vytvoří enumerátor pro iteraci v rámci aktuálních poradenských připojení.|
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Vytvoří enumerátor pro iteraci skrze `FORMATETC` struktury podporované datovým objektem. Implementace ATL Vrátí E_NOTIMPL.|
|[IDataObjectImpl::FireDataChange](#firedatachange)|Pošle oznámení o změně do každé jímky v pokynech.|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Načte logicky ekvivalentní `FORMATETC` strukturu s objektem, který je složitější. Implementace ATL Vrátí E_NOTIMPL.|
|[IDataObjectImpl::GetData](#getdata)|Převede data z datového objektu na klienta. Data jsou popsána ve `FORMATETC` struktuře a přenesena `STGMEDIUM` prostřednictvím struktury.|
|[IDataObjectImpl::GetDataHere](#getdatahere)|Podobně jako `GetData`u, s výjimkou, že `STGMEDIUM` klient musí přidělit strukturu. Implementace ATL Vrátí E_NOTIMPL.|
|[IDataObjectImpl::QueryGetData](#querygetdata)|Určuje, zda datový objekt podporuje konkrétní `FORMATETC` strukturu pro přenos dat. Implementace ATL Vrátí E_NOTIMPL.|
|[IDataObjectImpl::SetData](#setdata)|Přenáší data z klienta na datový objekt. Implementace ATL Vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

Rozhraní [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) poskytuje metody pro podporu jednotného přenos dat. `IDataObject`používá ke čtení a ukládání dat standardní struktury formátu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) a [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) .

`IDataObject`také spravuje připojení ke zpracování oznámení o změně dat v pokynech pro upozorňování. Aby klient mohl přijímat oznámení o změnách dat z datového objektu, musí implementovat rozhraní [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) u objektu s názvem příjímka Advise. Když klient potom volá `IDataObject::DAdvise`, vytvoří se připojení mezi datovým objektem a jímkou oznámení.

Třída `IDataObjectImpl` poskytuje výchozí `IDataObject` implementaci a implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestaveních pro ladění.

**Související články** [Kurz ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="dadvise"></a>IDataObjectImpl::D Advise

Naváže spojení mezi datovým objektem a jímkou oznámení.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Poznámky

To umožňuje, aby jímka Advise přijímala oznámení o změnách v objektu.

Chcete-li ukončit připojení, zavolejte na [DUnadvise](#dunadvise).

Viz [IDataObject::D Advise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) v Windows SDK.

##  <a name="dunadvise"></a>IDataObjectImpl::D nedoporučujeme.

Ukončí připojení, které bylo dříve vytvořeno pomocí [DAdvise](#dadvise).

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>Poznámky

Přečtěte si téma [IDataObject::D Unadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) in Windows SDK.

##  <a name="enumdadvise"></a>IDataObjectImpl::EnumDAdvise

Vytvoří enumerátor pro iteraci v rámci aktuálních poradenských připojení.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Poznámky

Viz [IDataObject:: EnumDAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-enumdadvise) v Windows SDK.

##  <a name="enumformatetc"></a>IDataObjectImpl::EnumFormatEtc

Vytvoří enumerátor pro iteraci skrze `FORMATETC` struktury podporované datovým objektem.

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>Poznámky

Viz [IDataObject:: EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

##  <a name="firedatachange"></a>IDataObjectImpl::FireDataChange

Pošle oznámení o změně na každou jímku, která je právě spravovaná.

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="getcanonicalformatetc"></a>  IDataObjectImpl::GetCanonicalFormatEtc

Načte logicky ekvivalentní `FORMATETC` strukturu s objektem, který je složitější.

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IDataObject:: GetCanonicalFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) v Windows SDK.

##  <a name="getdata"></a>IDataObjectImpl:: GetData

Převede data z datového objektu na klienta.

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>Poznámky

Parametr *pformatetcIn* musí určovat střední typ úložiště TYMED_MFPICT.

Viz [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) v Windows SDK.

##  <a name="getdatahere"></a>IDataObjectImpl::GetDataHere

Podobně jako `GetData`u, s výjimkou, že `STGMEDIUM` klient musí přidělit strukturu.

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IDataObject:: GetDataHere](/windows/win32/api/objidl/nf-objidl-idataobject-getdatahere) v Windows SDK.

##  <a name="querygetdata"></a>  IDataObjectImpl::QueryGetData

Určuje, zda datový objekt podporuje konkrétní `FORMATETC` strukturu pro přenos dat.

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IDataObject:: QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) v Windows SDK.

##  <a name="setdata"></a>IDataObjectImpl:: SetData

Přenáší data z klienta na datový objekt.

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IDataObject:: SetData](/windows/win32/api/objidl/nf-objidl-idataobject-setdata) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
