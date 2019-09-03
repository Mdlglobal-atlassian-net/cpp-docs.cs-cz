---
title: __vmx_vmread
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmread
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
ms.openlocfilehash: 409835ac29d6f2e839de62291cc5b142166a465c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219430"
---
# <a name="__vmx_vmread"></a>__vmx_vmread

**Specifické pro společnost Microsoft**

Přečte zadané pole z aktuální struktury řízení virtuálních počítačů (VMCS) a umístí ho do zadaného umístění.

## <a name="syntax"></a>Syntaxe

```C
unsigned char __vmx_vmread(
   size_t Field,
   size_t *FieldValue
);
```

### <a name="parameters"></a>Parametry

*Dílčí*\
pro Pole VMCS pro čtení.

*Hodnotapole*\
pro Ukazatel na umístění pro uložení hodnoty načtený z pole VMCS zadaného `Field` parametrem.

## <a name="return-value"></a>Návratová hodnota

|Value|Význam|
|-----------|-------------|
|0|Operace byla úspěšná.|
|1|Operace se nezdařila s rozšířeným stavem dostupným v `VM-instruction error field` aktuálním VMCS.|
|2|Operace se nezdařila bez dostupného stavu.|

## <a name="remarks"></a>Poznámky

Funkce je ekvivalentní `VMREAD` instrukci počítače. `__vmx_vmread` Hodnota `Field` parametru je kódovaný index pole, který je popsán v dokumentaci k platformě Intel. Další informace najdete v příloze C tématu "technické specifikace virtualizace Intel pro architekturu IA-32 Intel" na webu [společnosti Intel](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__vmx_vmread`|x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)
