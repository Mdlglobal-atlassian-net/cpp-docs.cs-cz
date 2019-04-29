---
title: __svm_skinit
ms.date: 11/04/2016
f1_keywords:
- __svm_skinit
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
ms.openlocfilehash: 199cba2623f9d8e47c08be642ec485599b87976e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390240"
---
# <a name="svmskinit"></a>__svm_skinit

**Microsoft Specific**

Iniciuje načítání ověřitelně zabezpečeného softwaru, jako je monitorování virtuálního počítače.

## <a name="syntax"></a>Syntaxe

```
void __svm_skinit(
   int SLB
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`SLB`|Fyzická adresa 32-bit bajtu 64 kB blok zabezpečení zavaděč (SLB).|

## <a name="remarks"></a>Poznámky

`__svm_skinit` Funkce je ekvivalentní volání `SKINIT` strojové instrukce. Tato funkce je součástí zabezpečení systému, který používá procesor a modul pro důvěryhodného Platform (TPM) k ověření a načtení důvěryhodný software volá zabezpečení jádra (SK). Monitorování virtuálního počítače je příkladem zabezpečení jádra. Systém zabezpečení ověří součástí programu načteny během procesu inicializace a chrání součásti v manipulaci přerušení, přístup k zařízení nebo jiný program, pokud je počítač procesory.

`SLB` Parametr určuje fyzickou adresu 64 kB blok paměti volá *zabezpečení Block zavaděč* (SLB). Nástroj SLB obsahuje program s názvem zabezpečené zavaděč, který vytvoří prostředí operačního systému počítač a následně načte zabezpečení jádra.

Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace vyhledejte dokument, "ruční svazek programátor architektury AMD64 2: Číslo 24593 revize 3.11, systém programování,"dokumentu na [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokality.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__svm_skinit`|x86, x64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)