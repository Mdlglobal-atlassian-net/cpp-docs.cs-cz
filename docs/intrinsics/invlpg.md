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
ms.openlocfilehash: b4f941baae9f03ed288a99d59e2b06262962e339
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023309"
---
# <a name="invlpg"></a>__invlpg

**Microsoft Specific**

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

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)