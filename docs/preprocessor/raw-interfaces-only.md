---
title: raw_interfaces_only
ms.date: 11/04/2016
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: c07401036261b9f93bb2c07dcf3aff1ecf72e2fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519350"
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

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)