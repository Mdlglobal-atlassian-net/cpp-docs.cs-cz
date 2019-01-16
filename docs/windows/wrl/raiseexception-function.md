---
title: RaiseException – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: 0a1c661378c4b71378456f2813159b7415cf3fad
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334759"
---
# <a name="raiseexception-function"></a>RaiseException – funkce

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
inline void __declspec(noreturn)   RaiseException(
      HRESULT hr,
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);
```

### <a name="parameters"></a>Parametry

*hr*<br/>
Kód výjimky výjimek vyvolaných; To znamená, HRESULT neúspěšnou operaci.

*dwExceptionFlags*<br/>
Příznak, který označuje výjimce (hodnota příznaku je nula), nebo noncontinuable výjimky (hodnota příznaku je nenulová). Výjimkou je ve výchozím nastavení, co vznikla nevykonatelná.

## <a name="remarks"></a>Poznámky

Vyvolá výjimku v volajícího vlákna.

Další informace najdete v článku Windows `RaiseException` funkce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)