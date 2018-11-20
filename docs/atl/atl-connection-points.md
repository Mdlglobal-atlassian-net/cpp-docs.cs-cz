---
title: ATL – body připojení
ms.date: 11/04/2016
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
ms.openlocfilehash: 520537f5d562450dc4ea2a5e5a0c68af513da509
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175053"
---
# <a name="atl-connection-points"></a>ATL – body připojení

Objekt umožňující připojení k je ten, který podporuje odchozí rozhraní. Odchozí rozhraní umožňuje objektu ke komunikaci s klientem. Pro každé rozhraní odchozí zpřístupňuje umožňující připojení k objektu spojovacího bodu. Každý odchozí rozhraní je implementováno klienta v objektu s názvem jímky.

![Body připojení](../atl/media/vc2zw31.gif "body připojení")

Každý bod připojení podporuje [IConnectionPoint](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpoint) rozhraní. Objekt umožňující připojení k zpřístupňuje jeho spojovací body do klienta prostřednictvím [IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer) rozhraní.

## <a name="in-this-section"></a>V tomto oddílu

[ATL – třídy bodu připojení](../atl/atl-connection-point-classes.md)<br/>
Stručně popisuje ATL – třídy, které podporují spojovací body.

[Přidání bodů připojení objektu](../atl/adding-connection-points-to-an-object.md)<br/>
Popisuje postup pro přidání bodů připojení objektu.

[ATL – příklad bodu připojení](../atl/atl-connection-point-example.md)<br/>
Poskytuje příklad deklarování bod připojení.

## <a name="related-sections"></a>Související oddíly

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Obsahuje odkazy na koncepční témata o tom, jak programovat pomocí knihovnu Active Template Library.

## <a name="see-also"></a>Viz také

[Koncepty](../atl/active-template-library-atl-concepts.md)

