---
title: Třída iProvideClassInfo2impl
ms.date: 11/04/2016
f1_keywords:
- IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::GetClassInfo
- ATLCOM/ATL::IProvideClassInfo2Impl::GetGUID
- ATLCOM/ATL::IProvideClassInfo2Impl::_tih
helpviewer_keywords:
- IProvideClassInfo2Impl class
- IProvideClassInfo2 ATL implementation
- class information, ATL
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
ms.openlocfilehash: 0d1ee9acc1cfabc71ecf33fcb5919d826899c671
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329561"
---
# <a name="iprovideclassinfo2impl-class"></a>Třída iProvideClassInfo2impl

Tato třída poskytuje výchozí implementaci metod [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) a [IProvideClassInfo2.](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2)

## <a name="syntax"></a>Syntaxe

```
template <const CLSID* pcoclsid,
    const IID* psrcid,
    const GUID* plibid = &CAtlModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IProvideClassInfo2Impl : public IProvideClassInfo2
```

#### <a name="parameters"></a>Parametry

*pcoclsid (Pcoclsid)*<br/>
Ukazatel na identifikátor coclass.

*psrcid*<br/>
Ukazatel na identifikátor výchozího odchozího rozhraní odchozího odchozího rozhraní coclass.

*plibid*<br/>
Ukazatel na LIBID knihovny typů, která obsahuje informace o rozhraní. Ve výchozím nastavení je předána knihovna typů na úrovni serveru.

*wMajor*<br/>
Hlavní verze knihovny typů. Výchozí hodnota je 1.

*wMenší*<br/>
Dílčí verze knihovny typů. Výchozí hodnota je 0.

*tihclass*<br/>
Třída slouží ke správě informací o typu coclass. Výchozí hodnota je `CComTypeInfoHolder`.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[IProvideClassInfo2impl::iProvideClassInfo2impl](#iprovideclassinfo2impl)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IProvideClassInfo2impl::GetClassInfo](#getclassinfo)|Načte `ITypeInfo` ukazatel na informace o typu coclass.|
|[iProvideClassInfo2impl::GetGUID](#getguid)|Načte identifikátor GUID pro odchozí depinterface objektu.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[IProvideClassInfo2Impl::_tih](#_tih)|Spravuje informace o typu pro coclass.|

## <a name="remarks"></a>Poznámky

Rozhraní [IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) rozšiřuje [iProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) přidáním `GetGUID` metody. Tato metoda umožňuje klientovi načíst id odchozího rozhraní objektu pro jeho výchozí sadu událostí. Třída `IProvideClassInfo2Impl` poskytuje výchozí implementaci `IProvideClassInfo` `IProvideClassInfo2` metody a.

`IProvideClassInfo2Impl`obsahuje statický člen `CComTypeInfoHolder` typu, který spravuje informace o typu pro coclass.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="iprovideclassinfo2implgetclassinfo"></a><a name="getclassinfo"></a>IProvideClassInfo2impl::GetClassInfo

Načte `ITypeInfo` ukazatel na informace o typu coclass.

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Poznámky

Viz [IProvideClassInfo::GetClassInfo](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) v sadě Windows SDK.

## <a name="iprovideclassinfo2implgetguid"></a><a name="getguid"></a>iProvideClassInfo2impl::GetGUID

Načte identifikátor GUID pro odchozí depinterface objektu.

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>Poznámky

Viz [IProvideClassInfo2::GetGUID](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) v sadě Windows SDK.

## <a name="iprovideclassinfo2impliprovideclassinfo2impl"></a><a name="iprovideclassinfo2impl"></a>IProvideClassInfo2impl::iProvideClassInfo2impl

Konstruktor

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>Poznámky

Vyzývá `AddRef` [_tih](#_tih) člena. Destruktor `Release`volá .

## <a name="iprovideclassinfo2impl_tih"></a><a name="_tih"></a>IProvideClassInfo2Impl::_tih

Tento statický datový člen je instancí parametru šablony třídy `CComTypeInfoHolder` *tihclass*, což je ve výchozím nastavení .

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>Poznámky

`_tih`spravuje informace o typu pro coclass.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
