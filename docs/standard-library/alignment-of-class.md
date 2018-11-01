---
title: alignment_of – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: 2633749a72ceeea197579dca4300b58250f60d73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604389"
---
# <a name="alignmentof-class"></a>alignment_of – třída

Získá zarovnání zadaného typu. Tato struktura je implementován z hlediska [alignof](../cpp/alignof-and-alignas-cpp.md). Použití `alignof` přímo kdy stačí jednoduše k dotazování na zarovnání hodnotu. Alignment_of – použijte v případě potřebujete integrální konstantou, například při odbavení značky.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Dotaz typu obsahuje hodnotu zarovnání typu *Ty*.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[aligned_storage – třída](../standard-library/aligned-storage-class.md)<br/>
