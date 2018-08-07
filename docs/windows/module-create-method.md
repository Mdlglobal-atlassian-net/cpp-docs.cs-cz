---
title: Module::Create – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0d49a6f0b5172b0971f755fc61b7767f0f4427d
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603300"
---
# <a name="modulecreate-method"></a>Module::Create – metoda
Vytvoří instanci modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW static Module& Create();  
template<typename T>  
WRL_NOTHROW static Module& Create(  
   T callback  
);  
template<typename T>  
WRL_NOTHROW static Module& Create(  
   _In_ T* object,  
   _In_ void (T::* method)()  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Typ modulu.  
  
 *zpětné volání*  
 Volá se, když se uvolní objekt poslední instance modulu.  
  
 *object*  
 *Objekt* a *metoda* v kombinaci se používají parametry. Když se uvolní objekt poslední instance v modulu odkazuje na poslední instance objektu.  
  
 *– Metoda*  
 *Objekt* a *metoda* v kombinaci se používají parametry. Odkazuje na metodu poslední instance objektu poslední objekt instance v modulu se při uvolnění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Odkaz na modul.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
[Module – třída](../windows/module-class.md)