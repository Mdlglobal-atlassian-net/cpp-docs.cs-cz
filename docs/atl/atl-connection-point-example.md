---
title: ATL – příklad bodu připojení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9aafd2676b1816737015b6af4fdbc9b3a710ae5
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752355"
---
# <a name="atl-connection-point-example"></a>ATL – příklad bodu připojení

Tento příklad ukazuje, objekt, který podporuje [ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) jako odchozí rozhraní:

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

Při zadávání `IPropertyNotifySink` jako odchozí rozhraní, můžete použít třídu [ipropertynotifysinkcp –](../atl/reference/ipropertynotifysinkcp-class.md) místo `IConnectionPointImpl`. Příklad:

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>Viz také

[Spojovací bod](../atl/atl-connection-points.md)

