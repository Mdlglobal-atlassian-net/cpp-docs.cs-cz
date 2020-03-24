---
title: MakeAndInitialize – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
ms.openlocfilehash: 28d9e586a766a131e7ab6280859845810c1d9814
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213795"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize – funkce

Inicializuje určenou třídu prostředí Windows Runtime. Pomocí této funkce lze vytvořit instanci komponenty, která je definována ve stejném modulu.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename T,
    typename I,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9>
HRESULT MakeAndInitialize(
    _Outptr_result_nullonfailure_ I** ppvObject,
    TArg1 &&arg1,
    TArg2 &&arg2,
    TArg3 &&arg3,
    TArg4 &&arg4,
    TArg5 &&arg5,
    TArg6 &&arg6,
    TArg7 &&arg7,
    TArg8 &&arg8,
    TArg9 &&arg9) throw()
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Uživatelem zadaná třída, která dědí z `WRL::RuntimeClass`.

*TArg1*<br/>
Typ argumentu 1, který je předán zadané třídě modulu runtime.

*TArg2*<br/>
Typ argumentu 2, který je předán zadané třídě modulu runtime.

*TArg3*<br/>
Typ argumentu 3, který se předává zadané třídě modulu runtime.

*TArg4*<br/>
Typ argumentu 4, který je předán zadané třídě modulu runtime.

*TArg5*<br/>
Typ argumentu 5, který je předán zadané třídě modulu runtime.

*TArg6*<br/>
Typ argumentu 6, který je předán zadané třídě modulu runtime.

*TArg7*<br/>
Typ argumentu 7, který je předán zadané třídě modulu runtime.

*TArg8*<br/>
Typ argumentu 8, který je předán zadané třídě modulu runtime.

*TArg9*<br/>
Typ argumentu 9, který je předán zadané třídě modulu runtime.

*arg1*<br/>
Argument 1, který je předán zadané třídě modulu runtime.

*arg2*<br/>
Argument 2, který je předán zadané třídě modulu runtime.

*arg3*<br/>
Argument 3, který je předán zadané třídě modulu runtime.

*arg4*<br/>
Argument 4, který je předán zadané třídě modulu runtime.

*arg5*<br/>
Argument 5, který je předán zadané třídě modulu runtime.

*arg6*<br/>
Argument 6, který je předán zadané třídě modulu runtime.

*arg7*<br/>
Argument 7, který je předán zadané třídě modulu runtime.

*arg8*<br/>
Argument 8, který je předán zadané třídě modulu runtime.

*arg9*<br/>
Argument 9, který je předán zadané třídě modulu runtime.

## <a name="return-value"></a>Návratová hodnota

Hodnota HRESULT.

## <a name="remarks"></a>Poznámky

Informace o rozdílech mezi touto funkcí a [Microsoft:: WRL:: Udělejte](make-function.md)a jako příklad naleznete v tématu [How to: instance WRL Components](how-to-instantiate-wrl-components-directly.md) .

## <a name="requirements"></a>Požadavky

**Hlavička:** Implements. h

**Obor názvů:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)
