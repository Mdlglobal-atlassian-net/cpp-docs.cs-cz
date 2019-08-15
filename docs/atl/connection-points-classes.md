---
title: Třídy spojovacích bodů (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
ms.openlocfilehash: 0dba06b072e1e9ca545ccbea196fcfe371b02157
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492448"
---
# <a name="connection-points-classes"></a>Třídy spojovacích bodů

Následující třídy poskytují podporu pro body připojení:

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) Implementuje kontejner bodu připojení.

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) Implementuje bod připojení.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) Implementuje bod připojení představující rozhraní [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) .

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) Spravuje neomezená připojení mezi spojovacím bodem a jeho jímkami.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) Spravuje pevný počet připojení mezi spojovacím bodem a jeho jímkami.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) Upozorňuje na jímku klienta, že vlastnost objektu se změnila nebo se má změnit.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) Poskytuje podporu pro body připojení pro objekt ATL modelu COM. Tyto spojovací body jsou namapovány pomocí mapy jímky událostí, která je k dispozici v objektu COM.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) Pracuje ve spojení s mapou jímky událostí ve vaší třídě pro směrování událostí do příslušné funkce obslužné rutiny.

## <a name="related-articles"></a>Související články

[Body připojení](../atl/atl-connection-points.md)

[Zpracování událostí a ATL](../atl/event-handling-and-atl.md)

## <a name="see-also"></a>Viz také:

[Přehled třídy](../atl/atl-class-overview.md)<br/>
[Makra bodů připojení](../atl/reference/connection-point-macros.md)<br/>
[Globální funkce bodů připojení](../atl/reference/connection-point-global-functions.md)
