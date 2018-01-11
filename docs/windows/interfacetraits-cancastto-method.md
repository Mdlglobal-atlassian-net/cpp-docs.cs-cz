---
title: "Interfacetraits::cancastto – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
dev_langs: C++
helpviewer_keywords: CanCastTo method
ms.assetid: 275847cb-69ea-42bf-910f-05ba6ef8b48d
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d8dfe6c1873d9cf897494eb6157c2be3baeb435
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="interfacetraitscancastto-method"></a>InterfaceTraits::CanCastTo – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
template<typename T>  
static __forceinline bool CanCastTo(  
   _In_ T* ptr,  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `ptr`  
 Název ukazatele typu.  
  
 `riid`  
 ID rozhraní `Base`.  
  
 `ppv`  
 Pokud tato operace úspěšná, `ppv` odkazuje na rozhraní zadané `Base`. V opačném `ppv` je nastaven na `nullptr`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato operace úspěšná a `ptr` vložena do ukazatel na `Base`, jinak hodnota `false` .  
  
## <a name="remarks"></a>Poznámky  
 Určuje, zda je zadaný ukazatel lze převést na ukazatel na `Base`.  
  
 Další informace o `Base`, najdete v části veřejné – definice TypeDef v [interfacetraits – struktura](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Interfacetraits – struktura](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)