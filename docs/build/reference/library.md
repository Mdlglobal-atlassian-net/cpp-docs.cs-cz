---
title: KNIHOVNA
ms.date: 11/04/2016
f1_keywords:
- LIBRARY
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
ms.openlocfilehash: 73609be698719da05fff357ba80200c49f598add
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422661"
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

## <a name="see-also"></a>Viz také:

[Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)
