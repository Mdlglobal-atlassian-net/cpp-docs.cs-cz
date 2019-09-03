---
title: __outbytestring
ms.date: 09/02/2019
f1_keywords:
- __outbytestring
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
ms.openlocfilehash: 31caf17db5d56efccd6b30200994b1080356b4c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217168"
---
# <a name="__outbytestring"></a>__outbytestring

**Specifické pro společnost Microsoft**

Vygeneruje `Count` `Buffer` `Port`instrukci, která pošle prvních bajtů dat, na které odkazuje, na port určený parametrem. `rep outsb`

## <a name="syntax"></a>Syntaxe

```C
void __outbytestring(
   unsigned short Port,
   unsigned char* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>Parametry

*Přístavní*\
pro Port, do kterého se mají data odeslat.

*Vyrovnávací paměti*\
pro Data, která se mají odeslat na zadaný port.

*Výpočtu*\
pro Počet bajtů dat, která se mají odeslat.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__outbytestring`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
