---
title: Implementshelper – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
dev_langs:
- C++
helpviewer_keywords:
- ImplementsHelper structure
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 58f27e418946987633f771bc8d2c3224bc2cd7fd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="implementshelper-structure"></a>ImplementsHelper – struktura
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename RuntimeClassFlagsT,  
   typename ILst,  
   bool IsDelegateToClass  
>  
friend struct Details::ImplementsHelper;  
```  
  
#### <a name="parameters"></a>Parametry  
 `RuntimeClassFlagsT`  
 Pole příznaky, které určuje jeden nebo více [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) výčty.  
  
 `ILst`  
 Seznam ID rozhraní.  
  
 `IsDelegateToClass`  
 Zadejte `true` Pokud aktuální instancí třídy implementuje je základní třídou první ID rozhraní v `ILst`, jinak hodnota `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pomáhá implementovat [implementuje](../windows/implements-structure.md) struktura.  
  
 Tato šablona prochází seznam rozhraní a přidá je jako základní třídy a taky jako informace, které jsou nutné k povolení QueryInterface.  
  
## <a name="members"></a>Členové  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ImplementsHelper`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace (knihovna prostředí Windows Runtime)](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)