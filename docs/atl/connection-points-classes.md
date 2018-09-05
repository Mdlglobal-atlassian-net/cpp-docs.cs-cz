---
title: Třídy bodů připojení (ATL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.connection
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e24d6333faee842227edb09ea05aa6a1f8b0d9a0
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763598"
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

[Přehled tříd](../atl/atl-class-overview.md)   
[Makra bodů připojení](../atl/reference/connection-point-macros.md)   
[Globální funkce bodů připojení](../atl/reference/connection-point-global-functions.md)

