---
title: rename_search_namespace – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rename_search_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_search_namespace attribute
ms.assetid: 47c9d7fd-59dc-4c62-87a1-9011a0040167
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0cc95851c4aa7127e690ec013b9d06d57f2730d
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808885"
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

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)