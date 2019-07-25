---
title: is_trivially_default_constructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_default_constructible
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
ms.openlocfilehash: 19a5e8afedf3e59d5dafa937af4f7d35343eb7d9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459642"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible – třída

Testuje, zda má typ triviální výchozí konstruktor.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud *je typ,* který je třída, která má triviální konstruktor, jinak obsahuje hodnotu false.

Výchozí konstruktor třídy *ty* je triviální, pokud:

- je implicitně deklarovaný výchozí konstruktor.

- Třída *ty* nemá žádné virtuální funkce.

- Třída *ty* nemá žádné virtuální základy.

- všechny přímé základny třídy *ty* mají triviální konstruktory.

- třídy všech nestatických datových členů typu třídy mají triviální konstruktory.

- třídy všech nestatických datových členů typu Array třídy mají triviální konstruktory.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
