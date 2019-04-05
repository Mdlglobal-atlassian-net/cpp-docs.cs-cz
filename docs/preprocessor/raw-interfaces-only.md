---
title: raw_interfaces_only
ms.date: 11/04/2016
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: 48133b85ccb5ddb8de8e6cb614d41cde22dac66b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028257"
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

[#import – atributy](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)