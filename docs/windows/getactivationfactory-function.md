---
title: Getactivationfactory – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f5afaa14d926cc7dde86cdbdb6b5ca8162f81d7c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402145"
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

**Namespace:** Windows::Foundation –

## <a name="see-also"></a>Viz také

[Windows::Foundation – obor názvů](../windows/windows-foundation-namespace.md)