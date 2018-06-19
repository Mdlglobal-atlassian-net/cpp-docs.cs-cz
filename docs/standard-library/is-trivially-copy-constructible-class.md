---
title: is_trivially_copy_constructible – třída | Microsoft Docs
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
ms.openlocfilehash: 01c95007f1db1bcaf549398fa8865a9e51fe23d1
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33954099"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible – třída

Testy, pokud má typ trivial kopírovacího konstruktoru.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>Parametry

`T` Typ k dotazu.

## <a name="remarks"></a>Poznámky

Instance predikátem typu obsahuje hodnotu true, pokud typ `T` je třída, která má trivial kopírovacího konstruktoru, jinak má hodnotu false.

Kopírovací konstruktor pro třídu `T` je jednoduchá, pokud je implicitně deklarovaná, třída `T` nemá žádné virtuální funkce nebo virtuální základů, všechny přímé základů třídy `T` mít trivial kopírovací konstruktory, třídy všechny nestatickou datové členy typu třídy trivial kopie konstruktorů a třídy všechny členy nestatické datové pole typu třídy trivial kopírovací konstruktory.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
