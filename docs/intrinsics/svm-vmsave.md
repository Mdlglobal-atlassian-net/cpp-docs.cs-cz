---
title: __svm_vmsave
ms.date: 11/04/2016
f1_keywords:
- __svm_vmsave
helpviewer_keywords:
- VMSAVE instruction
- __svm_vmsave intrinsic
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
ms.openlocfilehash: d683a13f636db9683b4a7c8d075ad6c3c88c2aed
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023409"
---
# <a name="svmvmsave"></a>__svm_vmsave

**Specifické pro Microsoft**

Uloží podmnožinu stav procesoru řídicí blok zadaný virtuální počítač (VMCB).

## <a name="syntax"></a>Syntaxe

```
void __svm_vmsave(
   size_t VmcbPhysicalAddress
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*VmcbPhysicalAddress*|[in] Fyzickou adresu VMCB.|

## <a name="remarks"></a>Poznámky

`__svm_vmsave` Funkce je ekvivalentní volání `VMSAVE` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace vyhledejte dokument, "ruční svazek programátor architektury AMD64 2: Číslo 24593 revize 3.11 nebo novější na systému programování,"dokumentu [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokality.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__svm_vmsave`|x86, x64|

**Soubor hlaviček** \<intrin.h >

**END Specifické pro Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_vmrun](../intrinsics/svm-vmrun.md)<br/>
[__svm_vmload](../intrinsics/svm-vmload.md)