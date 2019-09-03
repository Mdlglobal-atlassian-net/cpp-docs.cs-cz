---
title: _disable
ms.date: 09/02/2019
f1_keywords:
- _disable_cpp
- _disable
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
ms.openlocfilehash: 94be850e1d494ff62df84922b46f28481be68314
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216815"
---
# <a name="_disable"></a>_disable

**Specifické pro společnost Microsoft**

Zakáže přerušení.

## <a name="syntax"></a>Syntaxe

```C
void _disable(void);
```

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_disable`|x86, ARM, x64, ARM64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

`_disable`instruuje procesor, aby vymazal příznak přerušení. V systémech x86 Tato funkce vygeneruje instrukci pro vymazání příznaku přerušení (`cli`).

Tato funkce je k dispozici pouze v režimu jádra. Při použití v uživatelském režimu je výjimka privilegované instrukce vyvolána v době běhu.

Na platformách ARM a ARM64 je tato rutina dostupná jenom jako vnitřní.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
