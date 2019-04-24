---
title: raw_interfaces_only
ms.date: 11/04/2016
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: 48133b85ccb5ddb8de8e6cb614d41cde22dac66b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179786"
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**Specifické pro C++**

Potlačí generování obálky funkce zpracování chyb a [vlastnost](../cpp/property-cpp.md) deklarace, které používají tyto funkce obálky.

## <a name="syntax"></a>Syntaxe

```
raw_interfaces_only
```

## <a name="remarks"></a>Poznámky

**Raw_interfaces_only** atribut navíc způsobí, že výchozí předpony v názvu bez vlastností funkcí, které mají být odebrány. Za normálních okolností je předpona **raw_**. Pokud tento atribut není zadán, jsou uvedené názvy přímo z knihovny typů.

Tento atribut umožňuje vystavit pouze nízké úrovně obsah knihovny typů.

**Specifické pro END C++**

## <a name="see-also"></a>Viz také:

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)