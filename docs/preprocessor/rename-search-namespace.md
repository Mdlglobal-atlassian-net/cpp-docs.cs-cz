---
title: rename_search_namespace
ms.date: 10/18/2018
f1_keywords:
- rename_search_namespace
helpviewer_keywords:
- rename_search_namespace attribute
ms.assetid: 47c9d7fd-59dc-4c62-87a1-9011a0040167
ms.openlocfilehash: ca5d24ca9cc12e9defaa395cf150bc3c04ee4439
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59022850"
---
# <a name="renamesearchnamespace"></a>rename_search_namespace

**Specifické pro C++**

Má stejné funkce jako [rename_namespace](../preprocessor/rename-namespace.md) atribut, ale je použita v knihovnách typů, které používáte `#import` s [auto_search –](../preprocessor/auto-search.md) atribut.

## <a name="syntax"></a>Syntaxe

```
rename_search_namespace("NewName")
```

### <a name="parameters"></a>Parametry

*NewName*<br/>
Nový název oboru názvů.

## <a name="remarks"></a>Poznámky

**Specifické pro END C++**

## <a name="see-also"></a>Viz také:

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)