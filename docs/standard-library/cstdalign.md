---
title: '&lt;cstdalign&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdalign>
- cstdalign
- __alignas_is_defined
- __alignof_is_defined
helpviewer_keywords:
- cstdalign header
- __alignas_is_defined
- __alignof_is_defined
ms.assetid: 9d570924-d299-4225-9a58-8c4c820f5903
ms.openlocfilehash: 603a590190c50495aa80f1b41a574149eb8f760a
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68342248"
---
# <a name="ltcstdaligngt"></a>&lt;cstdalign&gt;

V některých C++ standardních implementacích knihovny tato hlavička obsahuje hlavičku \<standardní knihovny jazyka C stdalign. h > a přidává `std` přidružené názvy do oboru názvů. Protože tato hlavička není implementována v MSVC, \<záhlaví cstdalign > definuje makra `__alignas_is_defined` kompatibility a `__alignof_is_defined`.

> [!NOTE]
> Vzhledem k \<tomu, že hlavička stdalign. h > definuje makra, C++která jsou klíčová slova v, včetně nemá žádný vliv. Hlavička stdalign. h > je zastaralá v C++ \< Hlavička \<> cstdalign je v c++ 17 zastaralá a odebrala se v konceptu c++ 20 Standard.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<cstdalign >

**Obor názvů:** std

## <a name="macros"></a>Makra

| – Makro | Popis |
| - | - |
| `__alignas_is_defined` | Makro kompatibility jazyka C, které se rozšíří na celočíselnou konstantu 1. |
| `__alignof_is_defined` | Makro kompatibility jazyka C, které se rozšíří na celočíselnou konstantu 1. |

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](cpp-standard-library-header-files.md)\
[C++Přehled standardní knihovny](cpp-standard-library-overview.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](thread-safety-in-the-cpp-standard-library.md)
