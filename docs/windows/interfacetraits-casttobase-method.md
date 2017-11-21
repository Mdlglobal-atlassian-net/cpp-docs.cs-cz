---
title: "Interfacetraits::casttobase – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
dev_langs: C++
helpviewer_keywords: CastToBase method
ms.assetid: 0591a017-0adf-4358-b946-eb0a307ce7f2
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fa78bd28bbc65c93c201f044055cde40d5d79cf6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="interfacetraitscasttobase-method"></a>InterfaceTraits::CastToBase – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<  
   typename T  
>  
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
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)