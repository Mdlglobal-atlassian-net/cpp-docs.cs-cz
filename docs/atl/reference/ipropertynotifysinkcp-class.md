---
title: Ipropertynotifysinkcp – třída
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: 6a80ff17b5d8083704b144686d8bff27be115b18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461604"
---
# <a name="ipropertynotifysinkcp-class"></a>Ipropertynotifysinkcp – třída

Tato třída zveřejňuje [ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) rozhraní jako odchozí rozhraní umožňující připojení k objektu.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IPropertyNotifySinkCP`.

*CDV*<br/>
Třída, která spravuje připojení mezi bodem připojení a jeho jímky. Výchozí hodnota je [ccomdynamicunkarray –](../../atl/reference/ccomdynamicunkarray-class.md), který umožňuje neomezený počet připojení. Můžete také použít [ccomunkarray –](../../atl/reference/ccomunkarray-class.md), která určuje pevný počet připojení.

## <a name="remarks"></a>Poznámky

`IPropertyNotifySinkCP` dědí všechny metody prostřednictvím její základní třídě [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).

[Ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) rozhraní umožňuje vnořený objekt k přijímání oznámení o změně vlastnosti. Třída `IPropertyNotifySinkCP` zpřístupní toto rozhraní jako odchozí rozhraní umožňující připojení k objektu. Klient musí implementovat `IPropertyNotifySink` metody na jímce.

Odvodit třídu z `IPropertyNotifySinkCP` Pokud chcete vytvořit, který představuje bod připojení `IPropertyNotifySink` rozhraní.

Další informace o použití spojovacích bodů v ATL, najdete v článku [spojovací body](../../atl/atl-connection-points.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="see-also"></a>Viz také

[IConnectionPointImpl – třída](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[IConnectionPointContainerImpl – třída](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
