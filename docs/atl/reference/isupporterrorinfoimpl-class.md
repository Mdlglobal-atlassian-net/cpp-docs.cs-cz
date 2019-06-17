---
title: Isupporterrorinfoimpl – třída
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
ms.openlocfilehash: 650d90c9ec98754e11586f63e0871b70ebbe34f3
ms.sourcegitcommit: e79188287189b76b34eb7e8fb1bfe646bdb586bc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141707"
---
# <a name="isupporterrorinfoimpl-class"></a>Isupporterrorinfoimpl – třída

Tato třída poskytuje výchozí implementaci třídy [ISupportErrorInfo rozhraní](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) a můžou používat, když pouze jedno rozhraní vygeneruje chyby na objekt.

> [!IMPORTANT]
> Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>Parametry

*piid*<br/>
Ukazatel na IID rozhraní, které podporuje [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo).

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Určuje, zda rozhraní identifikovaný `riid` podporuje [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) rozhraní.|

## <a name="remarks"></a>Poznámky

[ISupportErrorInfo rozhraní](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) zajistí, že informace o chybě můžou být vrácen do klienta. Objekty, které používají `IErrorInfo` musí implementovat `ISupportErrorInfo`.

Třída `ISupportErrorInfoImpl` poskytuje výchozí implementaci třídy `ISupportErrorInfo` a můžou používat, když pouze jedno rozhraní vygeneruje chyby na objekt. Příklad:

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

Určuje, zda rozhraní identifikovaný `riid` podporuje [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) rozhraní.

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Poznámky

Zobrazit [ISupportErrorInfo::InterfaceSupportsErrorInfo](/windows/desktop/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) ve Windows SDK.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
