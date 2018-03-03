---
title: "ATL – kolekce a Enumerátor třídy | Microsoft Docs"
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
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b172c0d3a6f453ec0d5f7b5bb3584ebf2f5140e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="atl-collection-and-enumerator-classes"></a>ATL – kolekce a Enumerátor třídy
ATL obsahuje následující třídy, která vám pomůže implementovat kolekce a výčty.  
  
|Třída|Popis|  
|-----------|-----------------|  
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|Implementace rozhraní kolekce|  
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|Enumerátor implementace rozhraní (předpokládá data uložená v kontejneru kompatibilní knihovny C++ Standard)|  
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|Enumerátor implementace rozhraní (předpokládá data uložená v pole)|  
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|Implementace objektu enumerátor (používá `IEnumOnSTLImpl`)|  
|[CComEnum](../atl/reference/ccomenum-class.md)|Implementace objektu enumerátor (používá `CComEnumImpl`)|  
|[_Copy](../atl/atl-copy-policy-classes.md)|Zkopírujte zásady – třída|  
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|Zkopírujte zásady – třída|  
|[CAdapt](../atl/reference/cadapt-class.md)|Adaptér – třída (skryje **operátor &** povolení `CComPtr`, `CComQIPtr`, a `CComBSTR` k uložení do kontejnerů standardní knihovna C++)|  
  
## <a name="see-also"></a>Viz také  
 [Kolekce a výčty](../atl/atl-collections-and-enumerators.md)

