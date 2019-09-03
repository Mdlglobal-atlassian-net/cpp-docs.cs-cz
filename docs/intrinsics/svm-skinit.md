---
title: __svm_skinit
ms.date: 09/02/2019
f1_keywords:
- __svm_skinit
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
ms.openlocfilehash: 6657921d647a23bf027a5800702527951f7f6831
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219868"
---
# <a name="__svm_skinit"></a>__svm_skinit

**Specifické pro společnost Microsoft**

Inicializuje načítání ověřeného zabezpečeného softwaru, jako je například monitorování virtuálního počítače.

## <a name="syntax"></a>Syntaxe

```C
void __svm_skinit(
   int block_address
);
```

### <a name="parameters"></a>Parametry

*block_address*\
32 fyzická adresa zablokování zabezpečeného zavaděče (SLB) pro 64 kB bajtů.

## <a name="remarks"></a>Poznámky

Funkce je ekvivalentní `SKINIT` instrukci počítače. `__svm_skinit` Tato funkce je součástí systému zabezpečení, který používá procesor a čip TPM (Trusted Platform Module) k ověření a načtení důvěryhodného softwaru označovaného jako *jádro zabezpečení* (SK). Monitorování virtuálního počítače je příkladem jádra zabezpečení. Systém zabezpečení ověřuje součásti programu, které byly načteny během procesu inicializace. Chrání součásti proti manipulaci prostřednictvím přerušení, přístupu k zařízení nebo jiného programu, pokud je počítač více procesorů.

Parametr *block_address* určuje fyzickou adresu bloku 64 MB paměti označovaného jako *zabezpečený blok zavaděče* (SLB). SLB obsahuje program nazvaný *zabezpečený zavaděč*. Pro tento počítač vytvoří operační prostředí a pak načte jádro zabezpečení.

Tato funkce podporuje interakci monitorování virtuálního počítače hostitele s hostovaným operačním systémem a jeho aplikacemi. Další informace najdete v tématu "ručním svazkem pro programátory AMD64 architektury": Programování systému, "na webu [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__svm_skinit`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
