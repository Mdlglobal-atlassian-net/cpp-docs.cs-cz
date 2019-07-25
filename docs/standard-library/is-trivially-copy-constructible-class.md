---
title: is_trivially_copy_constructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
ms.openlocfilehash: f8c4026da424e77b57555dd4c342c9ac7a386591
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447990"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible – třída

Testuje, zda má typ konstruktor triviální kopie.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud typ *T* je třída, která má konstruktor triviální kopie, v opačném případě obsahuje hodnotu false.

Kopírovací konstruktor pro třídu *t* je triviální, pokud je implicitně deklarována, třída *t* nemá žádné virtuální funkce ani virtuální základy, všechny přímé základy třídy *t* mají konstruktory triviální kopie, třídy všech nestatických datových členů. Třída typu má konstruktory triviální kopie a třídy všech nestatických datových členů typu Array třídy mají konstruktory triviálního kopírování.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
