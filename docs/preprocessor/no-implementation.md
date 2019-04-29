---
title: no_implementation
ms.date: 11/04/2016
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: 26527ca69c66c73f5d41084dc42df5faa34481d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409808"
---
# <a name="noimplementation"></a>no_implementation
**Specifické pro C++**

Potlačí generování tli hlavičky, která obsahuje implementace členské funkce obálky.

## <a name="syntax"></a>Syntaxe

```
no_implementation
```

## <a name="remarks"></a>Poznámky

Pokud tento atribut je zadán, hlavičku .tlh s deklaracemi vystavit knihovny typů položek, vygeneruje se bez `#include` příkazu zahrnout hlavičku souboru tli.

Tento atribut se používá ve spojení s [implementation_only –](../preprocessor/implementation-only.md).

**Specifické pro END C++**

## <a name="see-also"></a>Viz také:

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)