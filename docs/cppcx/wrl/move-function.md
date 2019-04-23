---
title: Přesunout – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
ms.openlocfilehash: 8d7c959ecb2d3c06872871ba062d2be603489141
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031271"
---
# <a name="move-function"></a>Přesunout – funkce

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
inline typename RemoveReference<T>::Type&& Move(
   _Inout_ T&& arg
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ argumentu.

*arg*<br/>
Argument pro přesunutí.

## <a name="return-value"></a>Návratová hodnota

Parametr *arg* po vlastností nebo odkaz rvalue, pokud existuje, se odebraly.

## <a name="remarks"></a>Poznámky

Zadaný argument přesune z jednoho umístění do druhého.

Další informace najdete v tématu **přesunutí sémantiky** část [Rvalue Reference Declarator: & &](../../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Viz také:

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)