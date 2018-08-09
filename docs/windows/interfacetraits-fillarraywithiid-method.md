---
title: Interfacetraits::fillarraywithiid – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: 73583177-adc9-4fcb-917d-fa7e6d07c990
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9851731635d940b878cf2012c8553773f485559b
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017376"
---
# <a name="interfacetraitsfillarraywithiid-method"></a>InterfaceTraits::FillArrayWithIid – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__forceinline static void FillArrayWithIid(  
   _Inout_ unsigned long &index,  
   _In_ IID* iids  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *index*  
 Ukazatel na pole, které obsahuje hodnotu index založený na nule.  
  
 *IID*  
 Pole ID rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Přiřadí Identifikátor rozhraní `Base` k prvku pole určená argumentem indexu.  
  
 Rozporu s názvem toto rozhraní API se mění pouze jedno pole elementu; není celého pole.  
  
 Další informace o `Base`, naleznete v části veřejné definice TypeDef [interfacetraits – struktura](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Interfacetraits – struktura](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)