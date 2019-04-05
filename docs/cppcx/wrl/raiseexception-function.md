---
title: RaiseException – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: 08305c5d59d7e272aac87ad9aa183c8e82588632
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029956"
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

## <a name="see-also"></a>Viz také:

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)