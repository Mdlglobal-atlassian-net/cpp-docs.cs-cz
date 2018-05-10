---
title: Comptr::detach – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: b9016775-1ade-4581-be1f-0d6f9c2ca658
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: afa5976d26351ed3022c58fa8226b6038fa816c0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="comptrdetach-method"></a>ComPtr::Detach – metoda
To zrušíte `ComPtr` z rozhraní, který reprezentuje objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
T* Detach();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní, která je reprezentována to `ComPtr` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)