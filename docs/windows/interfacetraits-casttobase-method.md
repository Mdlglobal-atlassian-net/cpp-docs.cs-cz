---
title: Interfacetraits::casttobase – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
dev_langs:
- C++
helpviewer_keywords:
- CastToBase method
ms.assetid: 0591a017-0adf-4358-b946-eb0a307ce7f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8cd8fa2106ac3792c0352aa40ea34b049c1e5ce4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878522"
---
# <a name="interfacetraitscasttobase-method"></a>InterfaceTraits::CastToBase – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
static __forceinline Base* CastToBase(  
   _In_ T* ptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ parametru `ptr`.  
  
 `ptr`  
 Ukazatel na typ `T`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `Base`.  
  
## <a name="remarks"></a>Poznámky  
 Vrhá zadaný ukazatel na ukazatel na `Base`.  
  
 Další informace o `Base`, najdete v části veřejné – definice TypeDef v [interfacetraits – struktura](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Interfacetraits – struktura](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)