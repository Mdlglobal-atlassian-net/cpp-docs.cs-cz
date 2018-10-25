---
title: raw_interfaces_only | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_interfaces_only
dev_langs:
- C++
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 789c9179b2ba48f5c3796f709931728bc756aaaa
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075031"
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