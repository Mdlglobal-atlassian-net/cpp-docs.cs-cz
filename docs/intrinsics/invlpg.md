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
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023309"
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

**END Specifické pro Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)