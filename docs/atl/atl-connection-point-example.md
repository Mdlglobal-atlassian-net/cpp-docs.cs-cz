---
title: ATL – příklad bodu připojení
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
ms.openlocfilehash: 9312db740171672e6b0f231855408e0d0a9e060d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495989"
---
# <a name="atl-connection-point-example"></a>ATL – příklad bodu připojení

Tento příklad ukazuje, objekt, který podporuje [ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) jako odchozí rozhraní:

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

Při zadávání `IPropertyNotifySink` jako odchozí rozhraní, můžete použít třídu [ipropertynotifysinkcp –](../atl/reference/ipropertynotifysinkcp-class.md) místo `IConnectionPointImpl`. Příklad:

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>Viz také

[Spojovací bod](../atl/atl-connection-points.md)

