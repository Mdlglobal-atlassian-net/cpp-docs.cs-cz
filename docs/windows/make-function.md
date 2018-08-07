---
title: Make – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
dev_langs:
- C++
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9941f2b1bce67fb09c69db6278de94c102f88473
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604866"
---
# <a name="make-function"></a>Make – funkce
Inicializuje zadanou třídu Windows Runtime. Tato funkce slouží k vytvoření instance komponenty, který je definován ve stejném modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8,  
   typename TArg9  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7,  
   TArg8 &&arg8,  
   TArg9 &&arg9  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7,  
   TArg8 &&arg8  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2  
);  
template <  
   typename T,  
   typename TArg1  
>  
ComPtr<T> Make(  
   TArg1 &&arg1  
);  
template <  
   typename T  
>  
ComPtr<T> Make();  
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
 A `ComPtr<T>` objektu v případě úspěchu; jinak, **nullptr**.  
  
## <a name="remarks"></a>Poznámky  
 Naleznete v tématu [postupy: vytvoření instance komponenty knihovny WRL přímo](../windows/how-to-instantiate-wrl-components-directly.md) další rozdíly mezi touto funkcí a [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)a příklad.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)