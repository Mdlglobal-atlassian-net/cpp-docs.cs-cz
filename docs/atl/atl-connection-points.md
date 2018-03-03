---
title: "ATL – body připojení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2063bd35627fd86c0cab82e4e50e5e8a126ddfa7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

