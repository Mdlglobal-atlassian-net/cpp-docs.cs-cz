---
title: __svm_vmload | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_vmload
dev_langs:
- C++
helpviewer_keywords:
- __svm_vmload intrinsic
- VMLOAD instruction
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 837889478a4a646f8fb3829b3a05d0842edc1090
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399857"
---
# <a name="svmvmload"></a>__svm_vmload

**Specifické pro Microsoft**

Načte podmnožinu stav procesoru z řídicí blok zadaný virtuální počítač (VMCB).

## <a name="syntax"></a>Syntaxe

```
void __svm_vmload(
   size_t VmcbPhysicalAddress
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*VmcbPhysicalAddress*|[in] Fyzickou adresu VMCB.|

## <a name="remarks"></a>Poznámky

`__svm_vmload` Funkce je ekvivalentní volání `VMLOAD` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace vyhledejte dokument, "programátor architektury AMD64 ruční svazek 2: programování v systému," číslo 24593 revize 3.11, v dokumentu [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokality.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__svm_vmload`|x86, x64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_vmrun](../intrinsics/svm-vmrun.md)<br/>
[__svm_vmsave](../intrinsics/svm-vmsave.md)