---
title: ChainInterfaces::IidCount – konstanta | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::IidCount
dev_langs:
- C++
helpviewer_keywords:
- IidCount constant
ms.assetid: d4a90aa0-513c-4e99-b978-e12149734936
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 417ca38ab44d334fd26c503edc2727934983c39d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648139"
---
# <a name="chaininterfacesiidcount-constant"></a>ChainInterfaces::IidCount – konstanta
Celkový počet rozhraní ID, které jsou součástí rozhraní určené parametry šablony *I0* prostřednictvím *I9*.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Celkový počet ID rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Parametry šablony *I0* a *I1* jsou povinné a parametry *I2* prostřednictvím *I9* jsou volitelné. Počet IID každé rozhraní, které je obvykle 1.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ChainInterfaces – struktura](../windows/chaininterfaces-structure.md)