---
title: _enable
ms.date: 11/04/2016
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: e1ece6d6f4040b81b55d8400407d46f165b56b53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349027"
---
# <a name="enable"></a>_enable

**Microsoft Specific**

Umožňuje přerušení.

## <a name="syntax"></a>Syntaxe

```
void _enable(void);
```

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`_enable`|x86, ARM, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

`_enable` dává pokyn k nastavení příznaku přerušení procesoru. Na x86 systémy, tato funkce generuje nastavit příznak přerušení (`sti`) instrukce.

Tato funkce je pouze k dispozici v režimu jádra. Pokud se použije v uživatelském režimu, je vyvolána výjimka Privilegovaná instrukce.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)