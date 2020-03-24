---
title: RaiseException – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: 3270057bf5b1b27a98bef1ab236291eab15d27ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213626"
---
# <a name="raiseexception-function"></a>RaiseException – funkce

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
inline void __declspec(noreturn)   RaiseException(
      HRESULT hr,
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);
```

### <a name="parameters"></a>Parametry

*oddělení*<br/>
Kód výjimky vyvolané výjimky; To znamená, že HRESULT operace, která selhala.

*dwExceptionFlags*<br/>
Příznak, který označuje kontinuitnou výjimku (hodnota příznaku je nula) nebo nespojitelné výjimky (hodnota příznaku je nenulová). Ve výchozím nastavení je výjimka nenepřetržitá.

## <a name="remarks"></a>Poznámky

Vyvolá výjimku ve volajícím vlákně.

Další informace najdete v tématu funkce Windows `RaiseException`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** interní. h

**Obor názvů:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)
