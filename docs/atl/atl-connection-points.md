---
title: ATL – body připojení | Microsoft Docs
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
ms.openlocfilehash: 179f4329d55261d71d3d122e6a2601ce7e805c0f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="atl-connection-points"></a>ATL – body připojení
Objekt umožňující připojení je ten, který podporuje odchozí rozhraní. Odchozí rozhraní umožňuje objekt ke komunikaci s klientem. Objekt umožňující připojení odchozích rozhraní, zpřístupní bod připojení. Každý odchozí rozhraní je implementováno klientem na objektu s názvem jímky.  
  
 ![Body připojení](../atl/media/vc2zw31.gif "vc2zw31")  
  
 Každý bod připojení podporuje [IConnectionPoint –](http://msdn.microsoft.com/library/windows/desktop/ms694318) rozhraní. Objekt umožňující připojení zveřejňuje jeho body připojení klienta prostřednictvím [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857) rozhraní.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ATL – třídy bodu připojení](../atl/atl-connection-point-classes.md)  
 Stručně popisuje třídy ATL, které podporují body připojení.  
  
 [Přidání bodů připojení objektu](../atl/adding-connection-points-to-an-object.md)  
 Popisuje postup použít k přidání body připojení k objektu.  
  
 [ATL – příklad bodu připojení](../atl/atl-connection-point-example.md)  
 Poskytuje příklad deklarování bod připojení.  
  
## <a name="related-sections"></a>Související oddíly  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Obsahuje odkazy na koncepční témata o tom, jak program pomocí knihovny Active šablony.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)

