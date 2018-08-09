---
title: Implements::casttounknown – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: efaf7b51da1e4a4e744133884b92ac78db3b3f66
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017764"
---
# <a name="implementscasttounknown-method"></a>Implements::CastToUnknown – metoda
Získá ukazatel na základní `IUnknown` rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__forceinline IUnknown* CastToUnknown();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato operace je vždy úspěšné a vrátí `IUnknown` ukazatele.  
  
## <a name="remarks"></a>Poznámky  
 Interní pomocné funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Implements – struktura](../windows/implements-structure.md)