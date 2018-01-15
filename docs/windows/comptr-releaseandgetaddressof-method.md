---
title: "Comptr::releaseandgetaddressof – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
dev_langs: C++
helpviewer_keywords: ReleaseAndGetAddressOf method
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: be56e7afb23295e9b03d801943af25c652d18758
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf – metoda
Uvolní rozhraní přidružené k této ComPtr a pak načte adresu [ptr_ –](../windows/comptr-ptr-data-member.md) datového člena, který obsahuje ukazatel na rozhraní, která byla vydána.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
T** ReleaseAndGetAddressOf();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Na adresu [ptr_ –](../windows/comptr-ptr-data-member.md) data členem této ComPtr.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)   
 [ComPtr::ptr_ – datový člen](../windows/comptr-ptr-data-member.md)