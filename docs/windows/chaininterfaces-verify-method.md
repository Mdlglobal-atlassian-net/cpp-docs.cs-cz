---
title: Chaininterfaces::Verify – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c83479434a936f32fb0f7367d8cd02c6676c74e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860691"
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify – metoda
Ověřuje, že každé rozhraní definované parametry šablony `I0` prostřednictvím `I9` dědí z IUnknown nebo IInspectable a že `I0` dědí z `I1` prostřednictvím `I9`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud se ověření nezdaří, `static_assert` vysílá chybová zpráva popisující chybu.  
  
## <a name="remarks"></a>Poznámky  
 Parametry šablony `I0` a `I1` jsou povinné, parametry a `I2` prostřednictvím `I9` jsou volitelné.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ChainInterfaces – struktura](../windows/chaininterfaces-structure.md)