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
ms.openlocfilehash: 99c5d961f3e25e17506e25148260b6966152af44
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596119"
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

*T*  
Parametr šablony určující typ objektu factory pro aktivaci.

*activatableClassId*  
Název třídy, která může vytvářet objektu factory pro aktivaci.

*objekt pro vytváření*  
Když tato operace dokončí, odkaz na objekt pro vytváření aktivace pro typ *T*.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě chybu HRESULT, která označuje, proč tato operace se nezdařila.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Windows::Foundation –

## <a name="see-also"></a>Viz také

[Windows::Foundation – obor názvů](../windows/windows-foundation-namespace.md)