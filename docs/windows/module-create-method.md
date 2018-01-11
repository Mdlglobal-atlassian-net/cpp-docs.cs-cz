---
title: "Module::Create – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::Create
dev_langs: C++
helpviewer_keywords: Create method
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f025c446dd6a7dab9b37d126d65e640a02b939b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="modulecreate-method"></a>Module::Create – metoda
Vytvoří instanci modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW static Module& Create();  
template<  
   typename T  
>  
WRL_NOTHROW static Module& Create(  
   T callback  
);  
template<  
   typename T  
>  
WRL_NOTHROW static Module& Create(  
   _In_ T* object,  
   _In_ void (T::* method)()  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ modulu.  
  
 `callback`  
 Volá se při uvolnění poslední instance objektu modulu.  
  
 `object`  
 `object` a `method` v kombinaci se používají parametry. Po vydání poslední instance objektu v modulu odkazuje na poslední instance objektu.  
  
 `method`  
 `object` a `method` v kombinaci se používají parametry. Body metodě poslední instance objektu, až bude vydaná poslední instance objektu v modulu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Odkaz na modul.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
[Module – třída](../windows/module-class.md)

 