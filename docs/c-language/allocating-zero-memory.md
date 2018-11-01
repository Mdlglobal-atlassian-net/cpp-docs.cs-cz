---
title: Přidělování nulové paměti
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
ms.openlocfilehash: c7d5f307a38fff938c94cf2e1660cec99262a10a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447304"
---
# <a name="allocating-zero-memory"></a>Přidělování nulové paměti

**ANSI 4.10.3** chování `calloc`, `malloc`, nebo `realloc` fungovat, pokud je požadovaná velikost nula

Funkce `calloc`, `malloc` a `realloc` přijímají nulu jako argument. Není přidělena žádná skutečná paměť, ale je vrácen platný ukazatel a blok paměti lze modifikovat později pomocí funkce realloc.

## <a name="see-also"></a>Viz také

[Funkce knihovny](../c-language/library-functions.md)