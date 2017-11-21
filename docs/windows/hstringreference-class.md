---
title: "HStringReference – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HStringReference
dev_langs: C++
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1d09ba7fff2426f58f72b26a2c7e7681cecde8b5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hstringreference-class"></a>HStringReference – třída
Představuje HSTRING, který je vytvořený z existujícího řetězce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class HStringReference;  
```  
  
## <a name="remarks"></a>Poznámky  
 Doba platnosti zálohování vyrovnávací paměti v nové HSTRING není spravován pomocí prostředí Windows Runtime. Volající přiděluje zdrojový řetězec na rámec zásobníku, aby se zabránilo přidělení haldy a omezit riziko nevrácenou pamětí. Volající musí také zajistit, že zdrojový řetězec zůstává beze změny po dobu životnosti připojené HSTRING. Další informace najdete v tématu [WindowsCreateStringReference funkce](http://msdn.microsoft.com/en-us/0361bb7e-da49-4289-a93e-de7aab8712ac).  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Hstringreference::hstringreference – konstruktor](../windows/hstringreference-hstringreference-constructor.md)|Inicializuje novou instanci třídy HStringReference.|  
  
### <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|[Hstringreference::CopyTo – metoda](../windows/hstringreference-copyto-method.md)|Kopie aktuální HStringReference objektu na objekt HSTRING.|  
|[Hstringreference::Get – metoda](../windows/hstringreference-get-method.md)|Načte hodnotu základní HSTRING popisovač.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[HStringReference::Operator = – operátor](../windows/hstringreference-operator-assign-operator.md)|Hodnota jiného objektu HStringReference přesune na aktuální objekt HStringReference.|  
|[HStringReference::Operator == – operátor](../windows/hstringreference-operator-equality-operator.md)|Určuje, zda dva parametry jsou stejné.|  
|[HStringReference::Operator! = – operátor](../windows/hstringreference-operator-inequality-operator.md)|Určuje, zda dva parametry nejsou stejné.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `HStringReference`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: wrappers – Namespace](../windows/microsoft-wrl-wrappers-namespace.md)