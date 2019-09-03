---
title: __readmsr
ms.date: 09/02/2019
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 4398b9d42369e3a914dbec1ed2d14cafecf58483
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222337"
---
# <a name="__readmsr"></a>__readmsr

**Specifické pro společnost Microsoft**

Vygeneruje `register` instrukci, která načte registr specifický pro model určený pomocí a vrátí jeho hodnotu. `rdmsr`

## <a name="syntax"></a>Syntaxe

```C
__int64 __readmsr(
   int register
);
```

### <a name="parameters"></a>Parametry

*Registrace*\
pro Registr specifický pro daný model.

## <a name="return-value"></a>Návratová hodnota

Hodnota v zadaném registru.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__readmsr`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Tato funkce je k dispozici pouze v režimu jádra a rutina je k dispozici pouze jako vnitřní.

Další informace najdete v dokumentaci k nástroji AMD.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
