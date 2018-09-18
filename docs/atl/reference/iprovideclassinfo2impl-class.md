---
title: Iprovideclassinfo2impl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::GetClassInfo
- ATLCOM/ATL::IProvideClassInfo2Impl::GetGUID
- ATLCOM/ATL::IProvideClassInfo2Impl::_tih
dev_langs:
- C++
helpviewer_keywords:
- IProvideClassInfo2Impl class
- IProvideClassInfo2 ATL implementation
- class information, ATL
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c977ecc1094af37c5e2c2e3ed8f27a6f2bdf1c93
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033872"
---
# <a name="iprovideclassinfo2impl-class"></a>Iprovideclassinfo2impl – třída

Tato třída poskytuje výchozí implementaci třídy [iprovideclassinfo –](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo) a [IProvideClassInfo2](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo2) metody.

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
Ukazatel na identifikátor coclass'.

*psrcid*<br/>
Ukazatel na identifikátor coclass' výchozí odchozí dispinterface.

*plibid*<br/>
Ukazatel na LIBID knihovnu typů, který obsahuje informace o rozhraní. Ve výchozím nastavení je předán typ na úrovni serveru knihovny.

*wMajor*<br/>
Hlavní verze knihovny typů. Výchozí hodnota je 1.

*wMinor*<br/>
Dílčí verze knihovny typů. Výchozí hodnota je 0.

*tihclass*<br/>
Třída používá ke správě informací o typu coclass'. Výchozí hodnota je `CComTypeInfoHolder`.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Název|Popis|
|----------|-----------------|
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|Načte `ITypeInfo` ukazatel na informace o typu coclass'.|
|[IProvideClassInfo2Impl::GetGUID](#getguid)|Získá identifikátor GUID pro odchozí dispinterface daného objektu.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[IProvideClassInfo2Impl::_tih](#_tih)|Spravuje informace o typu coclass.|

## <a name="remarks"></a>Poznámky

[IProvideClassInfo2](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo2) rozhraní rozšiřuje [iprovideclassinfo –](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo) tak, že přidáte `GetGUID` metody. Tato metoda umožňuje klientovi k načtení objektu odchozí rozhraní IID pro jeho výchozí sadu událostí. Třída `IProvideClassInfo2Impl` poskytuje výchozí implementaci třídy `IProvideClassInfo` a `IProvideClassInfo2` metody.

`IProvideClassInfo2Impl` obsahuje statický člen typu `CComTypeInfoHolder` , který spravuje informace o typu coclass.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="getclassinfo"></a>  IProvideClassInfo2Impl::GetClassInfo

Načte `ITypeInfo` ukazatel na informace o typu coclass'.

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IProvideClassInfo::GetClassInfo](/windows/desktop/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) ve Windows SDK.

##  <a name="getguid"></a>  IProvideClassInfo2Impl::GetGUID

Získá identifikátor GUID pro odchozí dispinterface daného objektu.

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IProvideClassInfo2::GetGUID](/windows/desktop/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) ve Windows SDK.

##  <a name="iprovideclassinfo2impl"></a>  IProvideClassInfo2Impl::IProvideClassInfo2Impl

Konstruktor

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>Poznámky

Volání `AddRef` na [_tih](#_tih) člena. Volání destruktoru `Release`.

##  <a name="_tih"></a>  IProvideClassInfo2Impl::_tih

Tento statický datový člen je instancí parametru šablony třídy *tihclass*, která ve výchozím nastavení je `CComTypeInfoHolder`.

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>Poznámky

`_tih` Spravuje informace o typu coclass.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
