---
title: "Comptr::comptr – konstruktor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr, constructor
ms.assetid: eaf70907-beac-458f-a503-2e5e27b0c196
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f8f6234bf2dff0dab801c982a585dc30e338bb7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="comptrcomptr-constructor"></a>ComPtr::ComPtr – konstruktor
Intializes novou instanci třídy ComPtr – třída. Přetížení zadejte výchozí, kopírovat, přesunout a převod konstruktory.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW ComPtr();  
WRL_NOTHROW ComPtr(  
   decltype(__nullptr)  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr(  
   const ComPtr& other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   const ComPtr<U> &other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr &&other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr<U>&& other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `U`  
 Typ parametru `other`.  
  
 `other`  
 Objekt typu `U`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 První konstruktor je výchozí konstruktor, který implictly vytvoří prázdný objekt. Druhý konstruktor Určuje [__nullptr](../windows/nullptr-cpp-component-extensions.md), které explicitně vytvoří prázdný objekt.  
  
 Třetí konstruktoru vytvoří objekt z objektu určeného ukazatel.  
  
 Konstruktory čtvrté a páté jsou kopie konstruktorů. V páté konstruktoru zkopíruje objektu, když je převést na typ aktuální.  
  
 Konstruktory šesté a sedmého jsou přesunutí konstruktory. Sedmého konstruktor přesune objekt, pokud je převést na typ aktuální.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)