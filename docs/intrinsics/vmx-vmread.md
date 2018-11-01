---
title: __vmx_vmread
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmread
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
ms.openlocfilehash: 0a4528bed4426ce5b611e986a69f4b0b8c750548
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499096"
---
# <a name="vmxvmread"></a>__vmx_vmread

**Specifické pro Microsoft**

Načte zadaného pole z aktuální řídicí struktura virtuálního počítače (VMCS) a umístí jej do zadaného umístění.

## <a name="syntax"></a>Syntaxe

```
unsigned char __vmx_vmread(
   size_t Field,
   size_t *FieldValue
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Pole*|[in] Pole VMCS ke čtení.|
|*FieldValue*|[in] Ukazatel na umístění pro ukládání hodnoty horní četlo VMCS pole určené identifikátorem `Field` parametru.|

## <a name="return-value"></a>Návratová hodnota

|Hodnota|Význam|
|-----------|-------------|
|0|Operace byla úspěšná.|
|1|Operace se nezdařila s rozšířenou stav k dispozici v `VM-instruction error field` z aktuální VMCS.|
|2|Operace selhala, aniž by k dispozici.|

## <a name="remarks"></a>Poznámky

`__vmx_vmread` Funkce je ekvivalentní volání `VMREAD` strojové instrukce. Hodnota `Field` parametr je kódovaný pole index, který je popsán v dokumentaci k Intel. Další informace, hledání dokumentů "Intel Virtualization technické specifikace pro the architekturou IA-32 Intel," dokumentu C97063-002 čísla na [společnosti Intel Corporation](https://software.intel.com/articles/intel-sdm) lokality a pak naleznete v dodatku C tohoto dokumentu .

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__vmx_vmread`|x64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)