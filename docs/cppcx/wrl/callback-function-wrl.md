---
title: Funkce zpětného volání (WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Callback
ms.assetid: afb15d25-3230-44f7-b321-e17c54872943
ms.openlocfilehash: 138ad9d5d3bd4cf9e5263845f950dbbe7971fde6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214133"
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
Parametr šablony, který určuje rozhraní delegáta, které má být voláno při výskytu události.

*TCallback*<br/>
Parametr šablony, který určuje typ objektu, který představuje objekt a jeho členskou funkci zpětného volání.

*TCallbackObject*<br/>
Parametr šablony, který určuje objekt, jehož členská funkce je metoda, která má být volána, když dojde k události.

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

*onCuePoint*<br/>
Objekt, který reprezentuje objekt zpětného volání a jeho členskou funkci.

*object*<br/>
Objekt, jehož členská funkce je volána, když dojde k události.

*Metoda*<br/>
Členská funkce, která se má zavolat při výskytu události

## <a name="return-value"></a>Návratová hodnota

Objekt, jehož členská funkce je zadanou metodou zpětného volání.

## <a name="remarks"></a>Poznámky

Základ objektu delegáta musí být `IUnknown`, nikoli `IInspectable`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Event. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)
