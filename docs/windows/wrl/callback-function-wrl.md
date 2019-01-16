---
title: Funkce zpětného volání (WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Callback
ms.assetid: afb15d25-3230-44f7-b321-e17c54872943
ms.openlocfilehash: e5cccd337514df34729fc916900a7b16a15596fc
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334765"
---
# <a name="callback-function-wrl"></a>Funkce zpětného volání (WRL)

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

*callback*<br/>
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

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)