---
title: no_implementation – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_implementation
dev_langs:
- C++
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f169b30394e3fdf893475a49946266143772eb7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078060"
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