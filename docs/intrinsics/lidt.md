---
title: __lidt
ms.date: 09/02/2019
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 24778b761ada56830b155a2fc65e90f54ba729ed
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217504"
---
# <a name="__lidt"></a>__lidt

**Specifické pro společnost Microsoft**

Načte registraci tabulky deskriptoru přerušení (IDTR) s hodnotou v zadaném umístění v paměti.

## <a name="syntax"></a>Syntaxe

```C
void __lidt(void * Source);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Zdroj*|pro Ukazatel na hodnotu, která má být zkopírována do IDTR.|

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__lidt`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Funkce je ekvivalentní `LIDT` instrukci počítače a je k dispozici pouze v režimu jádra. `__lidt` Pokud chcete získat další informace, vyhledejte dokument "Intel Architecture Software Developer 's Manual, Volume 2: Odkaz na sadu instrukcí "na webu [společnosti Intel](https://software.intel.com/articles/intel-sdm) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__sidt](../intrinsics/sidt.md)
