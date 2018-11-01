---
title: no_implementation
ms.date: 11/04/2016
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: d4e55d06bef823d28c5deb3467654bc530a3853e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456781"
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

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)