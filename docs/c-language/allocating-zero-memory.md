---
title: Přidělování nulové paměti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc3b7a92cdc8a05c73f15c7cea917d86a3b6bb46
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085053"
---
# <a name="allocating-zero-memory"></a>Přidělování nulové paměti

**ANSI 4.10.3** chování `calloc`, `malloc`, nebo `realloc` fungovat, pokud je požadovaná velikost nula

Funkce `calloc`, `malloc` a `realloc` přijímají nulu jako argument. Není přidělena žádná skutečná paměť, ale je vrácen platný ukazatel a blok paměti lze modifikovat později pomocí funkce realloc.

## <a name="see-also"></a>Viz také

[Funkce knihovny](../c-language/library-functions.md)