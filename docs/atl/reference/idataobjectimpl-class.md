---
title: Idataobjectimpl – třída
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
ms.openlocfilehash: b73cfe83075b9595bc98ca05ab2ec2e1771a038d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275461"
---
# <a name="idataobjectimpl-class"></a>Idataobjectimpl – třída

Tato třída poskytuje metody pro podporu jednotného přenosu dat a Správa připojení.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IDataObjectImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IDataObjectImpl::DAdvise](#dadvise)|Naváže připojení mezi datový objekt a jímky doporučení. To umožňuje jímky doporučení k přijímání oznámení změn v objektu.|
|[IDataObjectImpl::DUnadvise](#dunadvise)|Ukončí připojení dříve vytvořené prostřednictvím `DAdvise`.|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Vytvoří čítač k iteraci v rámci aktuální advisory připojení.|
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Vytvoří čítač k iteraci v rámci `FORMATETC` struktury nepodporuje datový objekt. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IDataObjectImpl::FireDataChange](#firedatachange)|Odešle oznámení o změně zpět do jednotlivých doporučení jímky.|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Načte logicky ekvivalentní `FORMATETC` struktury, který je složitější. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IDataObjectImpl::GetData](#getdata)|Přenosu dat z datového objektu do klienta. Data je popsána v `FORMATETC` struktury a přenesených prostřednictvím `STGMEDIUM` struktury.|
|[IDataObjectImpl::GetDataHere](#getdatahere)|Podobně jako `GetData`s výjimkou případů, klient musí přidělit `STGMEDIUM` struktury. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IDataObjectImpl::QueryGetData](#querygetdata)|Určuje, zda datový objekt podporuje konkrétní `FORMATETC` strukturu pro přenos dat. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IDataObjectImpl::SetData](#setdata)|Přenosech dat z klienta do datového objektu. Implementace knihovny ATL vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) rozhraní poskytuje metody, které podporují jednotné datové přenosy. `IDataObject` využívá standardní formát struktury [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) a [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) k získávání a ukládání dat.

`IDataObject` také spravuje připojení radit zpracování oznámení o změnách dat jímky. Aby klient mohl přijmout oznámení o změnách dat z datového objektu musí implementovat klienta [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) rozhraní pro objekt volána jímky doporučení. Když klient pak volá `IDataObject::DAdvise`, vytvoří připojení mezi datového objektu a jímkou doporučení.

Třída `IDataObjectImpl` poskytuje výchozí implementaci třídy `IDataObject` a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.

**Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="dadvise"></a>  IDataObjectImpl::DAdvise

Naváže připojení mezi datový objekt a jímky doporučení.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Poznámky

To umožňuje jímky doporučení k přijímání oznámení změn v objektu.

Chcete-li ukončit připojení, zavolejte [DUnadvise](#dunadvise).

Zobrazit [IDataObject::DAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dadvise) ve Windows SDK.

##  <a name="dunadvise"></a>  IDataObjectImpl::DUnadvise

Ukončí připojení dříve vytvořené prostřednictvím [DAdvise](#dadvise).

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IDataObject::DUnadvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dunadvise) ve Windows SDK.

##  <a name="enumdadvise"></a>  IDataObjectImpl::EnumDAdvise

Vytvoří čítač k iteraci v rámci aktuální advisory připojení.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IDataObject::EnumDAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-enumdadvise) ve Windows SDK.

##  <a name="enumformatetc"></a>  IDataObjectImpl::EnumFormatEtc

Vytvoří čítač k iteraci v rámci `FORMATETC` struktury nepodporuje datový objekt.

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IDataObject::EnumFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-enumformatetc) ve Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

##  <a name="firedatachange"></a>  IDataObjectImpl::FireDataChange

Odešle oznámení o změně zpět do jednotlivých doporučení jímky, který je aktuálně spravován.

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="getcanonicalformatetc"></a>  IDataObjectImpl::GetCanonicalFormatEtc

Načte logicky ekvivalentní `FORMATETC` struktury, který je složitější.

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IDataObject::GetCanonicalFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) ve Windows SDK.

##  <a name="getdata"></a>  IDataObjectImpl::GetData

Přenosu dat z datového objektu do klienta.

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>Poznámky

*PformatetcIn* parametr musí určovat typ střední úložiště TYMED_MFPICT.

Zobrazit [IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) ve Windows SDK.

##  <a name="getdatahere"></a>  IDataObjectImpl::GetDataHere

Podobně jako `GetData`s výjimkou případů, klient musí přidělit `STGMEDIUM` struktury.

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IDataObject::GetDataHere](/windows/desktop/api/objidl/nf-objidl-idataobject-getdatahere) ve Windows SDK.

##  <a name="querygetdata"></a>  IDataObjectImpl::QueryGetData

Určuje, zda datový objekt podporuje konkrétní `FORMATETC` strukturu pro přenos dat.

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IDataObject::QueryGetData](/windows/desktop/api/objidl/nf-objidl-idataobject-querygetdata) ve Windows SDK.

##  <a name="setdata"></a>  IDataObjectImpl::SetData

Přenosech dat z klienta do datového objektu.

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IDataObject::SetData](/windows/desktop/api/objidl/nf-objidl-idataobject-setdata) ve Windows SDK.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
