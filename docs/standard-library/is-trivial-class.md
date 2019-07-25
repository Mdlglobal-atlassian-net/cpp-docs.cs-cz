---
title: is_trivial – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivial
helpviewer_keywords:
- is_trivial
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
ms.openlocfilehash: 1d218848fd65ca68022e3e66df02201582626711
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457426"
---
# <a name="istrivial-class"></a>is_trivial – třída

Testuje, zda je typ triviální typ.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivial;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud je typ *T* triviální typ, jinak má hodnotu false. Triviální typy jsou skalární typy, triviální kopírovací typy tříd, pole těchto typů a verze, které jsou kvalifikovány u těchto typů.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
