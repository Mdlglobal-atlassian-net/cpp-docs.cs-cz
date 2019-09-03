---
title: __outdwordstring
ms.date: 09/02/2019
f1_keywords:
- __outdwordstring
helpviewer_keywords:
- outsd instruction
- __outdwordstring intrinsic
- rep outsd instruction
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
ms.openlocfilehash: 50908a65795af617f18a497c073cfefe009dfd80
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217158"
---
# <a name="__outdwordstring"></a>__outdwordstring

**Specifické pro společnost Microsoft**

Vygeneruje `Count` `Buffer` `Port`instrukci, která odesílá doubleword počínaje na vstupně-výstupním portu určeném parametrem. `rep outsd`

## <a name="syntax"></a>Syntaxe

```C
void __outdwordstring(
   unsigned short Port,
   unsigned long* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>Parametry

*Přístavní*\
pro Port, do kterého se mají data odeslat.

*Vyrovnávací paměti*\
pro Ukazatel na data, která se mají odeslat na zadaný port.

*Výpočtu*\
pro Počet doubleword, které se mají odeslat

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__outdwordstring`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
