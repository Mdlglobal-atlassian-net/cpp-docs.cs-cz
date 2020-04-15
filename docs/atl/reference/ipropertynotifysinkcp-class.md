---
title: Třída IPropertyNotifySinkCP
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: c6d98bf5a6dfe5566839eb22bcd2bab2a9c28e4d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329599"
---
# <a name="ipropertynotifysinkcp-class"></a>Třída IPropertyNotifySinkCP

Tato třída zveřejňuje [rozhraní IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) jako odchozí rozhraní na připojitelný objekt.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IPropertyNotifySinkCP`.

*Cdv*<br/>
Třída, která spravuje připojení mezi bodem připojení a jímkami. Výchozí hodnota je [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), která umožňuje neomezené připojení. Můžete také použít [CComUnkArray](../../atl/reference/ccomunkarray-class.md), který určuje pevný počet připojení.

## <a name="remarks"></a>Poznámky

`IPropertyNotifySinkCP`dědí všechny metody prostřednictvím své základní třídy [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).

Rozhraní [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) umožňuje objektjímu pro příjem oznámení o změnách vlastností. Třída `IPropertyNotifySinkCP` zveřejňuje toto rozhraní jako odchozí rozhraní na připojitelný objekt. Klient musí implementovat metody na `IPropertyNotifySink` jímce.

Odvodit `IPropertyNotifySinkCP` třídu z, když chcete `IPropertyNotifySink` vytvořit spojovací bod, který představuje rozhraní.

Další informace o použití spojovacích bodů v atl naleznete v článku [Spojovací body](../../atl/atl-connection-points.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="see-also"></a>Viz také

[Třída IConnectionpointimpl](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[Třída IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
