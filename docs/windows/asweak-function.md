---
title: AsWeak – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
ms.openlocfilehash: 0c3250b18422f64e71d8e8d7dac8dc5ab204145b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616733"
---
# <a name="asweak-function"></a>AsWeak – funkce

Získá nestálý odkaz pro zadanou instanci.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
HRESULT AsWeak(
   _In_ T* p,
   _Out_ WeakRef* pWeak
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Ukazatel na typ parametru *p*.

*p*<br/>
Instance typu.

*pWeak*<br/>
Když tato operace dokončí, ukazatel na Slabý odkaz na parametr *p*.

## <a name="return-value"></a>Návratová hodnota

S_OK, pokud je tato operace úspěšná; v opačném případě chybu HRESULT určující příčinu selhání.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)