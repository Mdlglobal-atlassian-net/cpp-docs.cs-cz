---
title: "Makeandinitialize – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::MakeAndInitialize
dev_langs: C++
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a97796fa9b13e95cc446f04d7338dd91350c1c26
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize – funkce
Inicializuje pro zadanou třídu prostředí Windows Runtime. Tato funkce slouží k vytváření instancí komponenty, která je definována ve stejném modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <typename T, typename I,   
typename TArg1,   
typename TArg2,   
typename TArg3,   
typename TArg4,   
typename TArg5,   
typename TArg6,   
typename TArg7,   
typename TArg8,   
typename TArg9> HRESULT MakeAndInitialize(_Outptr_result_nullonfailure_ I** ppvObject, TArg1 &&arg1, TArg2 &&arg2, TArg3 &&arg3, TArg4 &&arg4, TArg5 &&arg5, TArg6 &&arg6, TArg7 &&arg7, TArg8 &&arg8, TArg9 &&arg9) throw()  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třídy definované uživatelem, která dědí z `WRL::RuntimeClass`.  
  
 `TArg1`  
 Typ argumentu 1, který je předán do zadaného modulu runtime – třída  
  
 `TArg2`  
 Typ argumentu 2, který je předán do zadaného modulu runtime – třída  
  
 `TArg3`  
 Typ argumentu 3, který je předán do zadaného modulu runtime – třída  
  
 `TArg4`  
 Typ argumentu 4, který je předán do zadaného modulu runtime – třída  
  
 `TArg5`  
 Typ argumentu 5, který je předán do zadaného modulu runtime – třída  
  
 `TArg6`  
 Typ argumentu 6, který je předán do zadaného modulu runtime – třída  
  
 `TArg7`  
 Typ argumentu 7, který je předán do zadaného modulu runtime – třída  
  
 `TArg8`  
 Typ argumentu 8, který je předán do zadaného modulu runtime – třída  
  
 `TArg9`  
 Typ argumentu 9, který je předán do zadaného modulu runtime – třída  
  
 `arg1`  
 Argument 1, který je předán do zadaného runtime třídy.  
  
 `arg2`  
 Argument 2, který je předán do zadaného runtime třídy.  
  
 `arg3`  
 Argument 3, který je předán do zadaného runtime třídy.  
  
 `arg4`  
 Argument 4, který je předán do zadaného runtime třídy.  
  
 `arg5`  
 Argument 5, který je předán do zadaného runtime třídy.  
  
 `arg6`  
 Argument 6, který je předán do zadaného runtime třídy.  
  
 `arg7`  
 Argument 7, který je předán do zadaného runtime třídy.  
  
 `arg8`  
 Argument 8, který je předán do zadaného runtime třídy.  
  
 `arg9`  
 Argument 9, který je předán do zadaného runtime třídy.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT` Hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [postupy: vytváření instancí komponent knihovny WRL přímo](../windows/how-to-instantiate-wrl-components-directly.md) další rozdíly mezi tato funkce a [Microsoft::WRL::Make](../windows/make-function.md)a příklad.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)