---
title: __vmx_on
ms.date: 09/02/2019
f1_keywords:
- __vmx_on
helpviewer_keywords:
- VMXON instruction
- __vmx_on intrinsic
ms.assetid: 16804991-6a75-4adf-8ec2-bc95acfa4801
ms.openlocfilehash: b6041711d9b6806362b856475151f2c4f63750cb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219573"
---
# <a name="__vmx_on"></a>__vmx_on

**Specifické pro společnost Microsoft**

Aktivuje v procesoru operaci rozšíření virtuálních počítačů (VMX).

## <a name="syntax"></a>Syntaxe

```C
unsigned char __vmx_on(
   unsigned __int64 *VmsSupportPhysicalAddress
);
```

### <a name="parameters"></a>Parametry

*VmsSupportPhysicalAddress*\
pro Ukazatel na 64 fyzickou adresu, který odkazuje na strukturu řízení virtuálních počítačů (VMCS).

## <a name="return-value"></a>Návratová hodnota

|Value|Význam|
|-----------|-------------|
|0|Operace byla úspěšná.|
|1|Operace se nezdařila s rozšířeným stavem dostupným v `VM-instruction error field` aktuálním VMCS.|
|2|Operace se nezdařila bez dostupného stavu.|

## <a name="remarks"></a>Poznámky

Funkce odpovídá instrukci `VMXON`počítače. `__vmx_on` Tato funkce podporuje interakci monitorování virtuálního počítače hostitele s hostovaným operačním systémem a jeho aplikacemi. Další informace najdete v dokumentu "Technická specifikace technologie Intel Virtualization pro architekturu IA-32 Intel," číslo dokumentu C97063-002 "na webu [společnosti Intel](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__vmx_on`|x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
