---
title: is_trivially_move_constructible třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 58bcd000f34941ec37141f9be4b4b3a56e0b9197
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible – třída

Testy, pokud má typ trivial přesunout konstruktor.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametry

`Ty` Typ k dotazu.

## <a name="remarks"></a>Poznámky

Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` je třída, která má trivial konstruktor move, jinak má hodnotu false.

Konstruktor move pro třídu `Ty` je jednoduchá pokud:

implicitně je deklarovaná

jeho typy parametrů jsou rovnocenná implicitní deklarace

Třída `Ty` nemá žádné virtuální funkce

Třída `Ty` nemá žádné virtuální základny

Třída nemá žádné volatile nestatické datové členy

všechny přímo základny třídy `Ty` mít konstruktory trivial přesunutí

třídy všechny členy nestatické datového typu třídy mít konstruktory trivial přesunutí

třídy všechny členy nestatické datové pole typu třídy mít konstruktory trivial přesunutí

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
