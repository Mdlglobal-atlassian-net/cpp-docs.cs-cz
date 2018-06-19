---
title: is_trivially_default_constructible – třída | Microsoft Docs
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
ms.openlocfilehash: 8f2bd65fa7145325fd4c5c2f1a2483851d0738b7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852133"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible – třída

Testy, pokud má typ trivial výchozí konstruktor.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>Parametry

`Ty` Typ k dotazu.

## <a name="remarks"></a>Poznámky

Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` je třída, která má triviálního konstruktoru, jinak má hodnotu false.

Výchozí konstruktor pro třídu `Ty` je jednoduchá pokud:

- je implicitně deklarované výchozí konstruktor

- Třída `Ty` nemá žádné virtuální funkce

- Třída `Ty` nemá žádné virtuální základny

- všechny přímo základny třídy `Ty` mít trivial konstruktory

- třídy všech členů nestatické datového typu třídy mají trivial konstruktory

- třídy všech členů nestatické datové pole typu třídy mají trivial konstruktory

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
