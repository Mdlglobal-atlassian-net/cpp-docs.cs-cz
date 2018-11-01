---
title: no_registry
ms.date: 10/18/2018
f1_keywords:
- no_registry
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
ms.openlocfilehash: bd101f5ca1776518ff4c5092da99134110bbb0b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503022"
---
# <a name="noregistry"></a>no_registry

**no_registry s: %** sděluje kompilátoru, aby v registru nevyhledával knihovny typů importované pomocí `#import`.

## <a name="syntax"></a>Syntaxe

```
#import filename no_registry
```

### <a name="parameters"></a>Parametry

*Název souboru*<br/>
Knihovna typů.

## <a name="remarks"></a>Poznámky

Pokud odkazovanou knihovnu typů nebyl nalezen v adresářích souborů k zahrnutí, kompilace se nezdaří, i v případě, že knihovna typů nachází v registru.  **no_registry s: %** rozšíří do ostatních knihoven typů importovaných implicitně pomocí `auto_search`.

Kompilátor nikdy nebude hledat v registru typy knihoven, které jsou určeny názvem souboru a které jsou předány přímo do direktivy `#import`.

Když `auto_search` není zadána, další `#import`s se dá vygenerovat pomocí **no_registry s: %** nastavení počáteční `#import` (pokud počáteční `#import` byl – direktiva **no_registry s: %** , `auto_search`– vygeneruje `#import` je také **no_registry s: %**.)

**no_registry s: %** je užitečné, pokud chcete importovat křížově odkazované knihovny typů bez rizika, že kompilátor vyhledá starší verzi souboru v registru. **no_registry s: %** je také užitečné, pokud knihovna typů není registrována.

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)