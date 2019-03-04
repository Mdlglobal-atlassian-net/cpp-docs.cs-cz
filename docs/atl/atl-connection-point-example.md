---
title: ATL – příklad bodu připojení
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
ms.openlocfilehash: 3113637a3f777a56bc0b0994203ce709fbc189d5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265064"
---
# <a name="atl-connection-point-example"></a>ATL – příklad bodu připojení

Tento příklad ukazuje, objekt, který podporuje [ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) jako odchozí rozhraní:

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

Při zadávání `IPropertyNotifySink` jako odchozí rozhraní, můžete použít třídu [ipropertynotifysinkcp –](../atl/reference/ipropertynotifysinkcp-class.md) místo `IConnectionPointImpl`. Příklad:

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>Viz také:

[Spojovací bod](../atl/atl-connection-points.md)
