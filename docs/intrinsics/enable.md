---
title: _enable
ms.date: 09/02/2019
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: 7adcd4eac807b8d0937efbbe6d89f8ad6dcb157c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217869"
---
# <a name="_enable"></a>_enable

**Specifické pro společnost Microsoft**

Povolí přerušení.

## <a name="syntax"></a>Syntaxe

```C
void _enable(void);
```

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`_enable`|x86, ARM, x64, ARM64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

`_enable`instruuje procesor, aby nastavil příznak přerušení. V systémech x86 Tato funkce vygeneruje instrukci pro nastavení příznaku přerušení (`sti`).

Tato funkce je k dispozici pouze v režimu jádra. Při použití v uživatelském režimu je vyvolána výjimka privilegované instrukce.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
