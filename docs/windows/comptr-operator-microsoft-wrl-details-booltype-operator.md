---
title: ComPtr::operator Microsoft::WRL::Details::BoolType operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: cfba6521-fb30-4fb8-afb2-cfab1cb5e0b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb5735eeb9cd4048596588765468fbb9c5e07496
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652598"
---
# <a name="comptroperator-microsoftwrldetailsbooltype-operator"></a>ComPtr::operator Microsoft::WRL::Details::BoolType – operátor
Určuje, zda je či není **ComPtr** spravuje doba života objektu rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je přidruženo toto rozhraní **ComPtr**, adresu [boolstruct::Member –](../windows/boolstruct-member-data-member.md) datový člen; v opačném případě **nullptr**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Comptr – třída](../windows/comptr-class.md)   
 [ComPtr::Get – metoda](../windows/comptr-get-method.md)