---
title: Přesunout – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
ms.openlocfilehash: 65fe85e95453165430c7ef3cfd4c4bb2babd9868
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213704"
---
# <a name="move-function"></a>Přesunout – funkce

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
inline typename RemoveReference<T>::Type&& Move(
   _Inout_ T&& arg
);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ argumentu.

*ARG*<br/>
Argument, který chcete přesunout.

## <a name="return-value"></a>Návratová hodnota

Parametr *arg* za odkazem nebo vlastnostmi rvalue (pokud existují) byly odebrány.

## <a name="remarks"></a>Poznámky

Přesune zadaný argument z jednoho umístění do druhého.

Další informace najdete v části věnované **sémantikě přesunutí** v [odkazu Rvalue deklarátor: & &](../../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** interní. h

**Obor názvů:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)
