---
title: Příklad spojovacího bodu ATL
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
ms.openlocfilehash: f33364cee65031c358fb546312f3fe2b7ae854d3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491799"
---
# <a name="atl-connection-point-example"></a>Příklad spojovacího bodu ATL

Tento příklad ukazuje objekt, který podporuje [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) jako odchozí rozhraní:

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

Při zadávání `IPropertyNotifySink` jako odchozí rozhraní můžete namísto použít třídu `IConnectionPointImpl` [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) . Příklad:

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>Viz také:

[Bod připojení](../atl/atl-connection-points.md)
