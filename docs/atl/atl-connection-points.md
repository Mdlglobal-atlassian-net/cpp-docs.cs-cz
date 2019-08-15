---
title: ATL – body připojení
ms.date: 11/04/2016
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
ms.openlocfilehash: df69496a6d245702a9598d684b25122ca55b1e6d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491802"
---
# <a name="atl-connection-points"></a>ATL – body připojení

Připojitelné objekty je jeden, který podporuje odchozí rozhraní. Odchozí rozhraní umožňuje objektu komunikovat s klientem. U každého odchozího rozhraní zpřístupňuje objekt připojení spojovací bod. Každé odchozí rozhraní je implementováno klientem na objektu s názvem jímka.

![Body připojení](../atl/media/vc2zw31.gif "Body připojení")

Každý bod připojení podporuje rozhraní [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) . Objekt připojit k klientovi zpřístupňuje body připojení klientovi prostřednictvím rozhraní [IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer) .

## <a name="in-this-section"></a>V tomto oddílu

[ATL – třídy bodu připojení](../atl/atl-connection-point-classes.md)<br/>
Stručně popisuje třídy ATL, které podporují spojovací body.

[Přidání bodů připojení objektu](../atl/adding-connection-points-to-an-object.md)<br/>
Popisuje kroky, které slouží k přidání bodů připojení do objektu.

[ATL – příklad bodu připojení](../atl/atl-connection-point-example.md)<br/>
Poskytuje příklad pro deklarování spojovacího bodu.

## <a name="related-sections"></a>Související oddíly

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Obsahuje odkazy na koncepční témata o tom, jak programovat pomocí knihovny Active Template Library.

## <a name="see-also"></a>Viz také:

[Charakteristiky](../atl/active-template-library-atl-concepts.md)
