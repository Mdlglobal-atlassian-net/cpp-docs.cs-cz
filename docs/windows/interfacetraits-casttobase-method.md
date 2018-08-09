---
title: Interfacetraits::casttobase – metoda | Dokumentace Microsoftu
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
ms.openlocfilehash: 32c45c5445b6258f1ed2e1da220b2899a76aa9c9
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017068"
---
# <a name="interfacetraitscasttobase-method"></a>InterfaceTraits::CastToBase – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename T>  
static __forceinline Base* CastToBase(  
   _In_ T* ptr  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Typ parametru *ptr*.  
  
 *ptr*  
 Ukazatel na typ *T*.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `Base`.  
  
## <a name="remarks"></a>Poznámky  
 Přetypování zadaný ukazatel na ukazatel na `Base`.  
  
 Další informace o `Base`, naleznete v části veřejné definice TypeDef [interfacetraits – struktura](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Interfacetraits – struktura](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)