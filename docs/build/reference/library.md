---
title: KNIHOVNA | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- LIBRARY
dev_langs:
- C++
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43b14e8e8ff4871ba4319c7f4fac5545e72e710b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723551"
---
# <a name="library"></a>KNIHOVNA

Říká odkaz pro vytvoření knihovny DLL. Ve stejnou dobu propojení vytvoří knihovnu importu souboru .exp se používá v sestavení.

```
LIBRARY [library][BASE=address]
```

## <a name="remarks"></a>Poznámky

*Knihovny* argument určuje název knihovny DLL. Můžete také použít [/OUT](../../build/reference/out-output-file-name.md) – možnost linkeru zadat název výstupní knihovnu DLL.

ZÁKLADNÍ =*adresu* argument nastaví základní adresu, operační systém používá k načtení knihovny DLL. Tento argument přepíše výchozí umístění knihovny DLL 0x10000000. Viz popis [/základní](../../build/reference/base-base-address.md) možnost Podrobnosti o základní adresy.

Nezapomeňte použít [/dll](../../build/reference/dll-build-a-dll.md) – možnost linkeru při sestavování knihovny DLL.

## <a name="see-also"></a>Viz také

[Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)