---
title: __vmx_vmwrite
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmwrite
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
ms.openlocfilehash: cdc5590858f160db24bf75ef11c8f20b204a3152
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219389"
---
# <a name="__vmx_vmwrite"></a>__vmx_vmwrite

**Specifické pro společnost Microsoft**

Zapíše zadanou hodnotu do zadaného pole v aktuální struktuře řízení virtuálních počítačů (VMCS).

## <a name="syntax"></a>Syntaxe

```C
unsigned char __vmx_vmwrite(
   size_t Field,
   size_t FieldValue
);
```

### <a name="parameters"></a>Parametry

*Dílčí*\
pro Pole VMCS, které se má zapsat

*Hodnotapole*\
pro Hodnota, která se má zapsat do pole VMCS

## <a name="return-value"></a>Návratová hodnota

0\
Operace byla úspěšná.

1\
Operace se nezdařila s rozšířeným stavem dostupným v `VM-instruction error field` aktuálním VMCS.

2\
Operace se nezdařila bez dostupného stavu.

## <a name="remarks"></a>Poznámky

Funkce je ekvivalentní `VMWRITE` instrukci počítače. `__vmx_vmwrite` Hodnota `Field` parametru je kódovaný index pole, který je popsán v dokumentaci k platformě Intel. Další informace najdete v příloze C tématu "technické specifikace virtualizace Intel pro architekturu IA-32 Intel" na webu [společnosti Intel](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__vmx_vmwrite`|x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmread](../intrinsics/vmx-vmread.md)
