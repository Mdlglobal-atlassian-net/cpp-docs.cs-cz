---
title: __svm_invlpga | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_invlpga
dev_langs:
- C++
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3fa5655911366b0adf21618ec7be7eeccdca9c5a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401902"
---
# <a name="svminvlpga"></a>__svm_invlpga

**Specifické pro Microsoft**

Zruší platnost položky mapování adresy ve vyrovnávací paměti počítače překlad doplňování vzhled. Parametry zadejte virtuální adresu a adresu místo identifikátor stránky zrušit platnost.

## <a name="syntax"></a>Syntaxe

```
void __svm_invlpga(void *Va, int ASID);
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*posouzení ohrožení zabezpečení*|[in] Virtuální adresa stránky zrušit platnost.|
|*ASID*|[in] Adresa místa identifikátor (ASID) na stránce zrušit platnost.|

## <a name="remarks"></a>Poznámky

`__svm_invlpga` Funkce je ekvivalentní volání `INVLPGA` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace vyhledejte dokument, "programátor architektury AMD64 ruční svazek 2: programování v systému," číslo 24593 revize 3.11, v dokumentu [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokality.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__svm_invlpga`|x86, x64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)