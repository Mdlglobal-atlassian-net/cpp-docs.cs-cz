---
title: IProvideClassInfo2Impl – třída
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
ms.openlocfilehash: f0ff3607002d32b4e21f7fc2199cc5da3662af8b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495543"
---
# <a name="iprovideclassinfo2impl-class"></a>IProvideClassInfo2Impl – třída

Tato třída poskytuje výchozí implementaci metod [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) a [IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) .

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

*pcoclsid*<br/>
Ukazatel na identifikátor coclass.

*psrcid*<br/>
Ukazatel na identifikátor pro výchozí odchozí odesílající rozhraní třídy coclass.

*plibid*<br/>
Ukazatel na LIBID knihovny typů, která obsahuje informace o rozhraní. Ve výchozím nastavení je předána knihovna typů na úrovni serveru.

*wMajor*<br/>
Hlavní verze knihovny typů. Výchozí hodnota je 1.

*wMinor*<br/>
Vedlejší verze knihovny typů. Výchozí hodnota je 0.

*tihclass*<br/>
Třída, která slouží ke správě informací typu coclass. Výchozí hodnota je `CComTypeInfoHolder`.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Name|Popis|
|----------|-----------------|
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|`ITypeInfo` Načte ukazatel na informace typu coclass.|
|[IProvideClassInfo2Impl::GetGUID](#getguid)|Načte identifikátor GUID odchozího odesílajícího rozhraní objektu.|

### <a name="protected-data-members"></a>Chránění členové dat

|Name|Popis|
|----------|-----------------|
|[IProvideClassInfo2Impl::_tih](#_tih)|Spravuje informace o typu pro třídu coclass.|

## <a name="remarks"></a>Poznámky

Rozhraní [IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) rozšiřuje [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) přidáním `GetGUID` metody. Tato metoda umožňuje klientovi načíst identifikátor IID odchozího rozhraní objektu pro výchozí sadu událostí. Třída `IProvideClassInfo2Impl` poskytuje výchozí implementaci `IProvideClassInfo` metod a `IProvideClassInfo2` .

`IProvideClassInfo2Impl`obsahuje statického člena typu `CComTypeInfoHolder` , který spravuje informace o typu pro coclass.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="getclassinfo"></a>  IProvideClassInfo2Impl::GetClassInfo

`ITypeInfo` Načte ukazatel na informace typu coclass.

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Poznámky

Viz [IProvideClassInfo:: GetClassInfo](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) v Windows SDK.

##  <a name="getguid"></a>  IProvideClassInfo2Impl::GetGUID

Načte identifikátor GUID odchozího odesílajícího rozhraní objektu.

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>Poznámky

Viz [IProvideClassInfo2:: GetGUID](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) v Windows SDK.

##  <a name="iprovideclassinfo2impl"></a>IProvideClassInfo2Impl::IProvideClassInfo2Impl

Konstruktor

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>Poznámky

Volání `AddRef` [_tih](#_tih) člena. Destruktor volá `Release`.

##  <a name="_tih"></a>  IProvideClassInfo2Impl::_tih

Tento statický datový člen je instancí parametru šablony třídy, *tihclass*, který je `CComTypeInfoHolder`ve výchozím nastavení.

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>Poznámky

`_tih`spravuje informace o typu pro třídu coclass.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
