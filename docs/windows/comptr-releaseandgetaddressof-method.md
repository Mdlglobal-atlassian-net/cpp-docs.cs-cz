---
title: Comptr::releaseandgetaddressof – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- ReleaseAndGetAddressOf method
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3bded6992abc5b22e2c02a3364431a3f68b76ad6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649845"
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf – metoda
Uvolní rozhraní přidružené k tomuto **ComPtr** a potom načte adresu [ptr_ –](../windows/comptr-ptr-data-member.md) datový člen, který obsahuje ukazatel rozhraní, která byla vydána.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
T** ReleaseAndGetAddressOf();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Adresa [ptr_ –](../windows/comptr-ptr-data-member.md) datový člen tohoto **ComPtr**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Comptr – třída](../windows/comptr-class.md)   
 [ComPtr::ptr_ – datový člen](../windows/comptr-ptr-data-member.md)