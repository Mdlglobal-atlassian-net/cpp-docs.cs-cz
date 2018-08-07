---
title: Hstringreference – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
dev_langs:
- C++
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 14ad6e511baa4c7b61a2205311bfb9ea4322a5b1
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605097"
---
# <a name="hstringreference-class"></a>HStringReference – třída
Představuje HSTRING, který je vytvořený z existujícího řetězce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class HStringReference;  
```  
  
## <a name="remarks"></a>Poznámky  
 Doba života běhu záložní vyrovnávací paměti v novém HSTRING není spravována modulu Windows Runtime. Volající alokuje zdrojový řetězec v zásobníku přidělení haldy a odstranilo nebezpečí nevracení paměti. Volající také musí zajistit, že zdrojový řetězec se nezmění po celou dobu životnosti připojených HSTRING. Další informace najdete v tématu [WindowsCreateStringReference funkce](http://msdn.microsoft.com/0361bb7e-da49-4289-a93e-de7aab8712ac).  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[HStringReference::HStringReference – konstruktor](../windows/hstringreference-hstringreference-constructor.md)|Inicializuje novou instanci třídy **HStringReference** třídy.|  
  
### <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|[HStringReference::CopyTo – metoda](../windows/hstringreference-copyto-method.md)|Zkopíruje aktuální **HStringReference** objektu na objekt HSTRING.|  
|[HStringReference::Get – metoda](../windows/hstringreference-get-method.md)|Načte hodnotu podkladového popisovače HSTRING.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[HStringReference::Operator= – operátor](../windows/hstringreference-operator-assign-operator.md)|Přesune hodnotu jiného **HStringReference** objektů na aktuální **HStringReference** objektu.|  
|[HStringReference::Operator== – operátor](../windows/hstringreference-operator-equality-operator.md)|Určuje, zda se tyto dva parametry rovnají.|  
|[HStringReference::Operator!= – operátor](../windows/hstringreference-operator-inequality-operator.md)|Určuje, zda dva parametry nerovnají.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `HStringReference`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)