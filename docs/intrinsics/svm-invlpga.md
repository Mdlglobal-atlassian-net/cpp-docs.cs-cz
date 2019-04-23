---
title: __svm_invlpga
ms.date: 11/04/2016
f1_keywords:
- __svm_invlpga
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
ms.openlocfilehash: 5e470fc12ad47aa156c513b293543fa356398d5e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031130"
---
# <a name="svminvlpga"></a>__svm_invlpga

**Microsoft Specific**

Zruší platnost položky mapování adresy ve vyrovnávací paměti počítače překlad doplňování vzhled. Parametry zadejte virtuální adresu a adresu místo identifikátor stránky zrušit platnost.

## <a name="syntax"></a>Syntaxe

```
void __svm_invlpga(void *Va, int ASID);
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Va*|[in] Virtuální adresa stránky zrušit platnost.|
|*ASID*|[in] Adresa místa identifikátor (ASID) na stránce zrušit platnost.|

## <a name="remarks"></a>Poznámky

`__svm_invlpga` Funkce je ekvivalentní volání `INVLPGA` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace vyhledejte dokument, "ruční svazek programátor architektury AMD64 2: Číslo 24593 revize 3.11, systém programování,"dokumentu na [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokality.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__svm_invlpga`|x86, x64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)