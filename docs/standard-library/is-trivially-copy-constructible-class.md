---
title: is_trivially_copy_constructible – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 410566c623595cc941ab6e6ad21dd95bd70fe516
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963664"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible – třída

Testuje, zda je typ má konstruktor kopie triviální.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>Parametry

*T* typ dotazu.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je třída, která má triviální kopírovací konstruktor, jinak má hodnotu false.

Kopírovací konstruktor pro třídu *T* je jednoduché, pokud je implicitně deklarován, třída *T* nemá žádné virtuální funkce a virtuálních základních tříd, všechny báze s přímým přístupem třídy *T* mají triviální kopírovací konstruktory tříd všechny nestatické datové členy typu třídy musí mít triviální kopírovací konstruktory a třídy nestatických datových členů typu pole třídy musí mít triviální kopírovací konstruktory.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
