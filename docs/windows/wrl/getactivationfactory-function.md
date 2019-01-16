---
title: GetActivationFactory – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
ms.openlocfilehash: 82c83e95648eeb0fc8985777156659a2ffb876a8
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334701"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory – funkce

Načte objekt factory pro aktivaci pro typ zadaný v parametru šablony.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
inline HRESULT GetActivationFactory(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Parametr šablony určující typ objektu factory pro aktivaci.

*activatableClassId*<br/>
Název třídy, která může vytvářet objektu factory pro aktivaci.

*objekt pro vytváření*<br/>
Když tato operace dokončí, odkaz na objekt pro vytváření aktivace pro typ *T*.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě chybu HRESULT, která označuje, proč tato operace se nezdařila.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Windows::Foundation

## <a name="see-also"></a>Viz také

[Windows::Foundation – obor názvů](windows-foundation-namespace.md)