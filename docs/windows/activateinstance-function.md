---
title: Activateinstance – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
dev_langs:
- C++
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ebebe0bbceafe82c41ec99b2532c965670776127
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426390"
---
# <a name="activateinstance-function"></a>ActivateInstance – funkce

Zaregistruje a načte instanci zadaného typu definované v ID zadané třídy.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
inline HRESULT ActivateInstance(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ aktivace.

*activatableClassId*<br/>
Název ID třídy, která definuje parametr *T*.

*instance*<br/>
Když tato operace dokončí, odkaz na instanci *T*.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě chybu HRESULT určující příčinu chyby.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Windows::Foundation –

## <a name="see-also"></a>Viz také

[Windows::Foundation – obor názvů](../windows/windows-foundation-namespace.md)