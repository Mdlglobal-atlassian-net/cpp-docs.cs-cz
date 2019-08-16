---
title: ISupportErrorInfoImpl – třída
ms.date: 06/13/2019
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
ms.openlocfilehash: d5e7f087f6646940777ae8b2d2a4ea888fdd3593
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495363"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl – třída

Tato třída poskytuje výchozí implementaci [rozhraní ISupportErrorInfo](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) a lze jej použít, pokud pouze jedno rozhraní generuje chyby v objektu.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>Parametry

*piid*<br/>
Ukazatel na IID rozhraní, které podporuje [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo).

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Označuje, zda rozhraní identifikované `riid` rozhraním podporuje rozhraní [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo) .|

## <a name="remarks"></a>Poznámky

[Rozhraní ISupportErrorInfo](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) zajišťuje, aby bylo možné vrátit informace o chybě klientovi. Objekty, které `IErrorInfo` používají, `ISupportErrorInfo`musí implementovat.

Třída `ISupportErrorInfoImpl` poskytuje výchozí `ISupportErrorInfo` implementaci a lze použít, pokud pouze jedno rozhraní generuje chyby v objektu. Příklad:

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

Označuje, zda rozhraní identifikované `riid` rozhraním podporuje rozhraní [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo) .

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Poznámky

Viz [ISupportErrorInfo:: InterfaceSupportsErrorInfo](/windows/win32/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
