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
ms.openlocfilehash: 9d55241ddefce0e4fcd7f72698779d6e4ec97e20
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464990"
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf – metoda
Uvolní rozhraní přidružené k tomuto **ComPtr** a potom načte adresu [ptr_ –](../windows/comptr-ptr-data-member.md) datový člen, který obsahuje ukazatel rozhraní, která byla vydána.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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