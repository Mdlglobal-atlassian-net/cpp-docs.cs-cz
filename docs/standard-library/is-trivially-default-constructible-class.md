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
ms.openlocfilehash: 73bdd8186f2ce56e4a6ecec0fa4f9468d9da8e8c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102704"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible – třída

Testuje, zda má typ jednoduchého dotazu výchozí konstruktor.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

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
