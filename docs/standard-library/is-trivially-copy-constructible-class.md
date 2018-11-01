---
title: is_trivially_copy_constructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
ms.openlocfilehash: aa6d6b19ae2bd5d6967c57db61c5697c0c6153e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630513"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible – třída

Testuje, zda je typ má konstruktor kopie triviální.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je třída, která má triviální kopírovací konstruktor, jinak má hodnotu false.

Kopírovací konstruktor pro třídu *T* je jednoduché, pokud je implicitně deklarován, třída *T* nemá žádné virtuální funkce a virtuálních základních tříd, všechny báze s přímým přístupem třídy *T* mají triviální kopírovací konstruktory tříd všechny nestatické datové členy typu třídy musí mít triviální kopírovací konstruktory a třídy nestatických datových členů typu pole třídy musí mít triviální kopírovací konstruktory.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
