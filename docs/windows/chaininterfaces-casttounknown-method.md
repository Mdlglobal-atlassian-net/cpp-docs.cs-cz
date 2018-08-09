---
title: Chaininterfaces::casttounknown – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: a6a58555-e5b0-4773-aba0-959d9d362c6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 45cc86c873e7c45a7352f0035b2fd16e312e7c6c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644443"
---
# <a name="chaininterfacescasttounknown-method"></a>ChainInterfaces::CastToUnknown – metoda
Přetypování ukazatele rozhraní typu definované *I0* parametr šablony na ukazatel na `IUnknown`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__forceinline IUnknown* CastToUnknown();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `IUnknown`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ChainInterfaces – struktura](../windows/chaininterfaces-structure.md)