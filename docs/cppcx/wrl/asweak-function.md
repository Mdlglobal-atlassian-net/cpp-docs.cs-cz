---
title: AsWeak – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
ms.openlocfilehash: d11f55d57f4053fd6d46b727a8ed91b340d1764b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214172"
---
# <a name="asweak-function"></a>AsWeak – funkce

Načte slabý odkaz na zadanou instanci.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
HRESULT AsWeak(
   _In_ T* p,
   _Out_ WeakRef* pWeak
);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Ukazatel na typ parametru *p*.

*trub*<br/>
Instance typu.

*pWeak*<br/>
Po dokončení této operace bude ukazatel na slabý odkaz na parametr *p*.

## <a name="return-value"></a>Návratová hodnota

S_OK, pokud je tato operace úspěšná; v opačném případě se jedná o chybu HRESULT, která indikuje příčinu selhání.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Client. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)
