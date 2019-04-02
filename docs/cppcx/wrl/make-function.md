---
title: Make – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
ms.openlocfilehash: cab261724399107c57b36a9020906a96697f7eca
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786551"
---
# <a name="make-function"></a>Make – funkce

Inicializuje zadanou třídu Windows Runtime. Tato funkce slouží k vytvoření instance komponenty, který je definován ve stejném modulu.

## <a name="syntax"></a>Syntaxe

```cpp
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

*T*<br/>
Uživatel zadal třídu, která dědí z `WRL::RuntimeClass`.

*TArg1*<br/>
Typ argumentu 1, který je předán do třídy zadaného modulu runtime.

*TArg2*<br/>
Typ argumentu 2, který je předán do třídy zadaného modulu runtime.

*TArg3*<br/>
Typ argumentu 3, který je předán do třídy zadaného modulu runtime.

*TArg4*<br/>
Typ argumentu 4, který je předán do třídy zadaného modulu runtime.

*TArg5*<br/>
Typ argumentu 5, který je předán do třídy zadaného modulu runtime.

*TArg6*<br/>
Typ argumentu 6, který je předán do třídy zadaného modulu runtime.

*TArg7*<br/>
Typ argumentu 7, který je předán do třídy zadaného modulu runtime.

*TArg8*<br/>
Typ argumentu 8, který je předán do třídy zadaného modulu runtime.

*TArg9*<br/>
Typ argumentu 9, který je předán do třídy zadaného modulu runtime.

*arg1*<br/>
Argument 1, který je předán do třídy zadaného modulu runtime.

*arg2*<br/>
Argument 2, který je předán do třídy zadaného modulu runtime.

*arg3*<br/>
Argument 3, který je předán do třídy zadaného modulu runtime.

*arg4*<br/>
Argument 4, který je předán do třídy zadaného modulu runtime.

*arg5*<br/>
Argument 5, který je předán do třídy zadaného modulu runtime.

*arg6*<br/>
Argument 6, který je předán do třídy zadaného modulu runtime.

*arg7*<br/>
Argument 7, který je předán do třídy zadaného modulu runtime.

*arg8*<br/>
Argument 8, který je předán do třídy zadaného modulu runtime.

*arg9*<br/>
Argument 9, který je předán do třídy zadaného modulu runtime.

## <a name="return-value"></a>Návratová hodnota

A `ComPtr<T>` objektu v případě úspěchu; jinak, `nullptr`.

## <a name="remarks"></a>Poznámky

Zobrazit [jak: Vytvoření instance komponenty přímo ke knihovně WRL](how-to-instantiate-wrl-components-directly.md) další rozdíly mezi touto funkcí a [Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md)a pro příklad.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)