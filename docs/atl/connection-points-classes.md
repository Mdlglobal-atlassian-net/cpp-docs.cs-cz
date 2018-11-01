---
title: Body připojení tříd (knihovny ATL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.connection
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
ms.openlocfilehash: 4965e5e371bd96903cad4d7f1e2b0ce3216107ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593970"
---
# <a name="connection-points-classes"></a>Třídy bodů připojení

Následující třídy poskytují podporu pro spojovací body:

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementuje kontejner bodu připojení.

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementuje bod připojení.

- [Ipropertynotifysinkcp –](../atl/reference/ipropertynotifysinkcp-class.md) implementuje představující bod připojení [ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) rozhraní.

- [Ccomdynamicunkarray –](../atl/reference/ccomdynamicunkarray-class.md) spravuje neomezené možnosti připojení mezi bodem připojení a jeho jímky.

- [Ccomunkarray –](../atl/reference/ccomunkarray-class.md) spravuje pevný počet připojení mezi bodem připojení a jeho jímky.

- [Cfirepropnotifyevent –](../atl/reference/cfirepropnotifyevent-class.md) upozorní jímkou klienta, který na vlastnost objektu došlo ke změně nebo je změnit.

- [Idispeventimpl –](../atl/reference/idispeventimpl-class.md) poskytuje podporu pro spojovací body pro objekt knihovny ATL modelu COM. S mapou jímky událostí, který je poskytován váš objekt modelu COM jsou mapovány tyto body připojení.

- [Idispeventsimpleimpl –](../atl/reference/idispeventsimpleimpl-class.md) mapování funguje ve spojení s jímky událostí ve své třídě pro směrování událostí na odpovídající obslužné rutiny.

## <a name="related-articles"></a>Související články

[Body připojení](../atl/atl-connection-points.md)

[Zpracování událostí a ATL](../atl/event-handling-and-atl.md)

## <a name="see-also"></a>Viz také

[Přehled tříd](../atl/atl-class-overview.md)<br/>
[Makra bodů připojení](../atl/reference/connection-point-macros.md)<br/>
[Globální funkce bodů připojení](../atl/reference/connection-point-global-functions.md)

