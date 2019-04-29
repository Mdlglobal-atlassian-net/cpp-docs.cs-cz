---
title: AsWeak – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
ms.openlocfilehash: 45df6332fccb2a22284eb6478c7554d87318ca78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398846"
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

## <a name="see-also"></a>Viz také:

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)