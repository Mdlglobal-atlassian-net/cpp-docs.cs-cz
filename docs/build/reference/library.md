---
title: KNIHOVNA
ms.date: 11/04/2016
f1_keywords:
- LIBRARY
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
ms.openlocfilehash: f8e5fbc50551b0a44b91787f99999301a8245069
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582464"
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