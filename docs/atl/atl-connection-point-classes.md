---
title: Třídy přípojných bodů knihovny ATL
ms.date: 11/04/2016
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
ms.openlocfilehash: 8644fc087d7f0a651724c40d2868e96c9b6ec96a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491826"
---
# <a name="atl-connection-point-classes"></a>Třídy přípojných bodů knihovny ATL

ATL používá následující třídy pro podporu přípojných bodů:

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementuje bod připojení. IID odchozího rozhraní, které představuje, je předán jako parametr šablony.

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementuje kontejner spojovacího bodu a spravuje seznam `IConnectionPointImpl` objektů.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementuje bod připojení představující rozhraní [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) .

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) spravuje libovolný počet připojení mezi spojovacím bodem a jeho jímkami.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) spravuje předdefinovaný počet připojení, která jsou určena parametrem šablony.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) upozorní obslužnou jímku klienta, že vlastnost objektu se změnila nebo se má změnit.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) poskytuje podporu pro body připojení pro objekt ATL modelu COM. Tyto spojovací body jsou namapovány pomocí mapy jímky událostí, která je k dispozici v objektu COM.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) pracuje ve spojení s mapou jímky událostí ve vaší třídě a směruje události do příslušné funkce obslužné rutiny.

## <a name="see-also"></a>Viz také:

[Bod připojení](../atl/atl-connection-points.md)
