---
title: ATL – body připojení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f7c9360af2b5e2220daacabcd9ac04e108871dc
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764225"
---
# <a name="atl-connection-points"></a>ATL – body připojení

Objekt umožňující připojení k je ten, který podporuje odchozí rozhraní. Odchozí rozhraní umožňuje objektu ke komunikaci s klientem. Pro každé rozhraní odchozí zpřístupňuje umožňující připojení k objektu spojovacího bodu. Každý odchozí rozhraní je implementováno klienta v objektu s názvem jímky.

![Body připojení](../atl/media/vc2zw31.gif "vc2zw31")

Každý bod připojení podporuje [IConnectionPoint](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpoint) rozhraní. Objekt umožňující připojení k zpřístupňuje jeho spojovací body do klienta prostřednictvím [IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer) rozhraní.

## <a name="in-this-section"></a>V tomto oddílu

[ATL – třídy bodu připojení](../atl/atl-connection-point-classes.md)  
Stručně popisuje ATL – třídy, které podporují spojovací body.

[Přidání bodů připojení objektu](../atl/adding-connection-points-to-an-object.md)  
Popisuje postup pro přidání bodů připojení objektu.

[ATL – příklad bodu připojení](../atl/atl-connection-point-example.md)  
Poskytuje příklad deklarování bod připojení.

## <a name="related-sections"></a>Související oddíly

[ATL](../atl/active-template-library-atl-concepts.md)  
Obsahuje odkazy na koncepční témata o tom, jak programovat pomocí knihovnu Active Template Library.

## <a name="see-also"></a>Viz také

[Koncepty](../atl/active-template-library-atl-concepts.md)

