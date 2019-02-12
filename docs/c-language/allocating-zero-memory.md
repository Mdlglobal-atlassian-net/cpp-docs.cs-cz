---
title: Přidělování nulové paměti
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
ms.openlocfilehash: 40f21c0fa9a2a4068cb2592c49ccefed82176a35
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147461"
---
# <a name="allocating-zero-memory"></a>Přidělování nulové paměti

**ANSI 4.10.3** chování `calloc`, `malloc`, nebo `realloc` fungovat, pokud je požadovaná velikost nula

Funkce `calloc`, `malloc` a `realloc` přijímají nulu jako argument. Není přidělena žádná skutečná paměť, ale je vrácen platný ukazatel a blok paměti lze modifikovat později pomocí funkce realloc.

## <a name="see-also"></a>Viz také:

[Funkce knihovny](../c-language/library-functions.md)
