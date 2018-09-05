---
title: ATL – třídy bodu připojení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 141142db5dff185cf4f8a0ad42c4b322e7d7739a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763877"
---
# <a name="atl-connection-point-classes"></a>ATL – třídy bodu připojení

ATL – používá následující třídy pro podporu spojovací body:

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementuje bod připojení. Identifikátor IID rozhraní odchozí, kterou představuje se předá jako parametr šablony.

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementuje kontejner bodu připojení a spravují seznam `IConnectionPointImpl` objekty.

- [Ipropertynotifysinkcp –](../atl/reference/ipropertynotifysinkcp-class.md) implementuje představující bod připojení [ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) rozhraní.

- [Ccomdynamicunkarray –](../atl/reference/ccomdynamicunkarray-class.md) spravuje libovolný počet připojení mezi bodem připojení a jeho jímky.

- [Ccomunkarray –](../atl/reference/ccomunkarray-class.md) spravuje předdefinovaném počtu připojení uvedená v parametru šablony.

- [Cfirepropnotifyevent –](../atl/reference/cfirepropnotifyevent-class.md) upozorní jímkou klienta, který na vlastnost objektu došlo ke změně nebo je změnit.

- [Idispeventimpl –](../atl/reference/idispeventimpl-class.md) poskytuje podporu pro spojovací body pro objekt knihovny ATL modelu COM. S mapou jímky událostí, který je poskytován váš objekt modelu COM jsou mapovány tyto body připojení.

- [Idispeventsimpleimpl –](../atl/reference/idispeventsimpleimpl-class.md) funguje ve spojení s mapou jímky událostí ve své třídě pro směrování událostí na odpovídající obslužné rutiny.

## <a name="see-also"></a>Viz také

[Spojovací bod](../atl/atl-connection-points.md)

