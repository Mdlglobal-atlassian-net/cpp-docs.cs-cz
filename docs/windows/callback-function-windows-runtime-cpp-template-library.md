---
title: Zpětné volání – funkce (knihovna šablon C++ prostředí Windows Runtime) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Callback
dev_langs:
- C++
ms.assetid: afb15d25-3230-44f7-b321-e17c54872943
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19bb77128eee9cc8af514e60730c3a39115695cc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426534"
---
# <a name="callback-function-windows-runtime-c-template-library"></a>Zpětné volání – funkce (knihovna šablon C++ prostředí Windows Runtime)

Vytvoří objekt, jehož členská funkce je metoda zpětného volání.

## <a name="syntax"></a>Syntaxe

```cpp
template<
   typename TDelegateInterface,
   typename TCallback
>
ComPtr<TDelegateInterface> Callback(
   TCallbackcallback
);
template<
   typename TDelegateInterface,
   typename TCallbackObject
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)()  
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1)  
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2)  
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3)  
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4)  
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5)  
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6)  
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7)  
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7,
   TArg8)  
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
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
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7,
   TArg8,
   TArg9)  
);
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Parametr šablony určuje rozhraní delegáta pro volání při výskytu události.

*TCallback*<br/>
Parametr šablony určující typ objektu, který reprezentuje objekt a jeho členskou funkci zpětného volání.

*TCallbackObject*<br/>
Parametr šablony, který určuje objekt, jehož členská funkce je metoda volání při výskytu události.

*TArg1*<br/>
Parametr šablony, který určuje typ prvního argumentu metody zpětného volání.

*TArg2*<br/>
Parametr šablony, který určuje typ druhého argumentu metody zpětného volání.

*TArg3*<br/>
Parametr šablony, který určuje typ třetího argumentu metody zpětného volání.

*TArg4*<br/>
Parametr šablony, který určuje typ čtvrtého argumentu metody zpětného volání.

*TArg5*<br/>
Parametr šablony, který určuje typ pátého argumentu metody zpětného volání.

*TArg6*<br/>
Parametr šablony, který určuje typ šestého argumentu metody zpětného volání.

*TArg7*<br/>
Parametr šablony, který určuje typ sedmého argumentu metody zpětného volání.

*TArg8*<br/>
Parametr šablony, který určuje typ osmého argumentu metody zpětného volání.

*TArg9*<br/>
Parametr šablony, který určuje typ devátého argumentu metody zpětného volání.

*zpětné volání*<br/>
Objekt představující objekt zpětného volání a jeho členskou funkci.

*object*<br/>
Objekt, jehož členská funkce je volána, když dojde k události.

*– Metoda*<br/>
Členská funkci volat při výskytu události.

## <a name="return-value"></a>Návratová hodnota

Objekt, jehož členská funkce je metoda zpětného volání zadané.

## <a name="remarks"></a>Poznámky

Základ objektu delegáta musí být `IUnknown`, nikoli `IInspectable`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)