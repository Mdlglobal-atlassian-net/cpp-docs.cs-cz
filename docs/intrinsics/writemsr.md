---
title: __writemsr
ms.date: 11/04/2016
f1_keywords:
- __writemsr
helpviewer_keywords:
- Write Model Specific Register instruction
- wrmsr instruction
- __writemsr intrinsic
ms.assetid: 938b1553-51a8-4822-a818-6bed79b0fde5
ms.openlocfilehash: ac57bac1d132c581ee12048b89d13ed1d1fdb7da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389707"
---
# <a name="writemsr"></a>__writemsr

**Microsoft Specific**

Generuje zápisu pro konkrétní registraci modelu (`wrmsr`) instrukce.

## <a name="syntax"></a>Syntaxe

```
void __writemsr(
   unsigned long Register,
   unsigned __int64 Value
);
```

#### <a name="parameters"></a>Parametry

*Register*<br/>
[in] Model konkrétním registru.

*Hodnota*<br/>
[in] Hodnota k zápisu.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__writemsr`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tato funkce slouží pouze v režimu jádra a tato rutina je dostupný jenom jako vnitřní.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)