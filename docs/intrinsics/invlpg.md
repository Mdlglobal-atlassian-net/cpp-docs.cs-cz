---
title: __invlpg
ms.date: 11/04/2016
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: 0ff46aa15fbb8728ce02255209a32f01a168609b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629382"
---
# <a name="invlpg"></a>__invlpg

**Specifické pro Microsoft**

Generuje x86 `invlpg` instrukce, což způsobí neplatnost vyrovnávací paměti Page Table Entry překladu (vyrovnávací paměti TLB) pro stránku související s pamětí, na které odkazuje `Address`.

## <a name="syntax"></a>Syntaxe

```
void __invlpg(
   void* Address
);
```

#### <a name="parameters"></a>Parametry

*Adresa*<br/>
[in] 64-bit adresa.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__invlpg`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Vnitřní objekt `__invlpg` vysílá Privilegovaná instrukce a je dostupná pouze v režimu jádra s úrovní oprávnění (PANELU) 0.

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)