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
ms.openlocfilehash: 0a5d3888657d491502b13283b5b9d7141940ade3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
[Module – třídy](../windows/module-class.md)

 