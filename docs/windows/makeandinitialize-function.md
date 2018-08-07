---
title: Makeandinitialize – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
dev_langs:
- C++
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cbdb6a312d6658fc880aa43ffc1205378d3935e7
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607647"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize – funkce
Inicializuje zadanou třídu Windows Runtime. Tato funkce slouží k vytvoření instance komponenty, který je definován ve stejném modulu.  
  
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
  
### <a name="parameters"></a>Parametry  
 *T*  
 Uživatel zadal třídu, která dědí z `WRL::RuntimeClass`.  
  
 *TArg1*  
 Typ argumentu 1, který je předán do třídy zadaného modulu runtime.  
  
 *TArg2*  
 Typ argumentu 2, který je předán do třídy zadaného modulu runtime.  
  
 *TArg3*  
 Typ argumentu 3, který je předán do třídy zadaného modulu runtime.  
  
 *TArg4*  
 Typ argumentu 4, který je předán do třídy zadaného modulu runtime.  
  
 *TArg5*  
 Typ argumentu 5, který je předán do třídy zadaného modulu runtime.  
  
 *TArg6*  
 Typ argumentu 6, který je předán do třídy zadaného modulu runtime.  
  
 *TArg7*  
 Typ argumentu 7, který je předán do třídy zadaného modulu runtime.  
  
 *TArg8*  
 Typ argumentu 8, který je předán do třídy zadaného modulu runtime.  
  
 *TArg9*  
 Typ argumentu 9, který je předán do třídy zadaného modulu runtime.  
  
 *arg1*  
 Argument 1, který je předán do třídy zadaného modulu runtime.  
  
 *arg2*  
 Argument 2, který je předán do třídy zadaného modulu runtime.  
  
 *arg3*  
 Argument 3, který je předán do třídy zadaného modulu runtime.  
  
 *arg4*  
 Argument 4, který je předán do třídy zadaného modulu runtime.  
  
 *arg5*  
 Argument 5, který je předán do třídy zadaného modulu runtime.  
  
 *arg6*  
 Argument 6, který je předán do třídy zadaného modulu runtime.  
  
 *arg7*  
 Argument 7, který je předán do třídy zadaného modulu runtime.  
  
 *arg8*  
 Argument 8, který je předán do třídy zadaného modulu runtime.  
  
 *arg9*  
 Argument 9, který je předán do třídy zadaného modulu runtime.  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnotu HRESULT.  
  
## <a name="remarks"></a>Poznámky  
 Naleznete v tématu [postupy: vytvoření instance komponenty knihovny WRL přímo](../windows/how-to-instantiate-wrl-components-directly.md) další rozdíly mezi touto funkcí a [Microsoft::WRL:: Make](../windows/make-function.md)a příklad.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)