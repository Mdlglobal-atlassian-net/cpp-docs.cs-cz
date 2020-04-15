---
title: Třída iSupportErrorInfoImpl
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
ms.openlocfilehash: 4c60b58ba697f00b146077a2cdecd727fe2cac02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326368"
---
# <a name="isupporterrorinfoimpl-class"></a>Třída iSupportErrorInfoImpl

Tato třída poskytuje výchozí implementaci [rozhraní ISupportErrorInfo](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) a lze ji použít pouze v případě, že pouze jedno rozhraní generuje chyby na objektu.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

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

|Name (Název)|Popis|
|----------|-----------------|
|[iSupportErrorInfoimpl::InterfaceSupportsErrorErrorInfoInfo](#interfacesupportserrorinfo)|Označuje, zda rozhraní `riid` identifikované rozhraním [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo) podporuje.|

## <a name="remarks"></a>Poznámky

[Rozhraní ISupportErrorInfo](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) zajišťuje, že informace o chybě mohou být vráceny klientovi. Objekty, `IErrorInfo` které `ISupportErrorInfo`používají musí implementovat .

Třída `ISupportErrorInfoImpl` poskytuje výchozí `ISupportErrorInfo` implementaci a lze použít, když pouze jedno rozhraní generuje chyby na objektu. Příklad:

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="isupporterrorinfoimplinterfacesupportserrorinfo"></a><a name="interfacesupportserrorinfo"></a>iSupportErrorInfoimpl::InterfaceSupportsErrorErrorInfoInfo

Označuje, zda rozhraní `riid` identifikované rozhraním [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo) podporuje.

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Poznámky

Viz [ISupportErrorInfo::InterfaceSupportsErrorInfo](/windows/win32/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
