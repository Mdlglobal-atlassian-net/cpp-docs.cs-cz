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
ms.openlocfilehash: 1a4ec737c3f24899e50220c3e862283b88a826b9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461161"
---
# <a name="comptroperator-microsoftwrldetailsbooltype-operator"></a>ComPtr::operator Microsoft::WRL::Details::BoolType – operátor
Určuje, zda je či není **ComPtr** spravuje doba života objektu rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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