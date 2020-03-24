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
ms.openlocfilehash: 430b4ed3f6a02fd3db2bcab05fbb7f21f5367b5c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213977"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory – funkce

Načte objekt pro vytváření aktivace pro typ určený parametrem šablony.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
inline HRESULT GetActivationFactory(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory
);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Parametr šablony, který určuje typ továrny aktivace.

*activatableClassId*<br/>
Název třídy, kterou může továrna aktivace vyvolat.

*instalací*<br/>
Po dokončení této operace se vytvoří odkaz na objekt pro vytváření aktivace pro typ *T*.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě se jedná o chybu HRESULT, která indikuje, proč tato operace selhala.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Client. h

**Obor názvů:** Windows:: Foundation

## <a name="see-also"></a>Viz také

[Windows::Foundation – obor názvů](windows-foundation-namespace.md)
