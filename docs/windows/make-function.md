---
title: Make – funkce | Microsoft Docs
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
ms.openlocfilehash: f381a00b5ac1f105080355f1d3e3cd15efa5abf8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878070"
---
# <a name="make-function"></a>Make – funkce
Inicializuje pro zadanou třídu prostředí Windows Runtime. Tato funkce slouží k vytváření instancí komponenty, která je definována ve stejném modulu.  
  
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
 A `ComPtr<T>` objekt Pokud úspěšné, jinak `nullptr`.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [postupy: vytváření instancí komponent knihovny WRL přímo](../windows/how-to-instantiate-wrl-components-directly.md) další rozdíly mezi tato funkce a [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)a příklad.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)