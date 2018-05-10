---
title: Interfacetraits::casttounknown – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: aca47fa0-3c60-47f2-a73c-258f7160adff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a2fdc46f57f834c3e8217049574ea504aae16f03
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="interfacetraitscasttounknown-method"></a>InterfaceTraits::CastToUnknown – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
static __forceinline IUnknown* CastToUnknown(  
   _In_ T* ptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ parametru `ptr`.  
  
 `ptr`  
 Ukazatel na typ `T`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na IUnknown, ze kterého `Base` je odvozený.  
  
## <a name="remarks"></a>Poznámky  
 Vrhá zadaný ukazatel na ukazatel IUnknown.  
  
 Další informace o `Base`, najdete v části veřejné – definice TypeDef v [interfacetraits – struktura](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Interfacetraits – struktura](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)