---
title: is_trivially_default_constructible – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa7b831790804005f0649dbae0dbb98df5121106
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954731"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible – třída

Testuje, zda má typ jednoduchého dotazu výchozí konstruktor.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>Parametry

*Ty* typ dotazu.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je třída, která má triviální konstruktor, jinak má hodnotu false.

Výchozí konstruktor pro třídu *Ty* triviální pokud:

- je implicitně deklarovaný výchozí konstruktor

- Třída *Ty* nemá žádné virtuální funkce

- Třída *Ty* nemá žádné virtuálních základních tříd

- všechny přímo základů třídy *Ty* mít triviální konstruktory

- třídy všechny nestatické datové členy typu třídy mají triviální konstruktory

- třídy nestatických datových členů typu pole třídy mají triviální konstruktory

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
