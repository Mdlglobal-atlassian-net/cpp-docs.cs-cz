---
title: "Chaininterfaces::iidcount – konstanta | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::ChainInterfaces::IidCount
dev_langs: C++
helpviewer_keywords: IidCount constant
ms.assetid: d4a90aa0-513c-4e99-b978-e12149734936
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a1a3409452fcae3764519c4beeb3557e5fd877b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="chaininterfacesiidcount-constant"></a>ChainInterfaces::IidCount – konstanta
Celkový počet rozhraní ID obsažené v rozhraní určeného parametry šablony `I0` prostřednictvím `I9`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Celkový počet ID rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Parametry šablony `I0` a `I1` jsou povinné, parametry a `I2` prostřednictvím `I9` jsou volitelné. Počet IID každé rozhraní je obvykle 1.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Chaininterfaces – struktura](../windows/chaininterfaces-structure.md)