---
title: KNIHOVNA
ms.date: 11/04/2016
f1_keywords:
- LIBRARY
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
ms.openlocfilehash: b43f269726e8925abeefd41aab0edfd57b071035
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291090"
---
# <a name="library"></a>KNIHOVNA

Říká odkaz pro vytvoření knihovny DLL. Ve stejnou dobu propojení vytvoří knihovnu importu souboru .exp se používá v sestavení.

```
LIBRARY [library][BASE=address]
```

## <a name="remarks"></a>Poznámky

*Knihovny* argument určuje název knihovny DLL. Můžete také použít [/OUT](out-output-file-name.md) – možnost linkeru zadat název výstupní knihovnu DLL.

ZÁKLADNÍ =*adresu* argument nastaví základní adresu, operační systém používá k načtení knihovny DLL. Tento argument přepíše výchozí umístění knihovny DLL 0x10000000. Viz popis [/základní](base-base-address.md) možnost Podrobnosti o základní adresy.

Nezapomeňte použít [/dll](dll-build-a-dll.md) – možnost linkeru při sestavování knihovny DLL.

## <a name="see-also"></a>Viz také:

[Pravidla pro příkazy definice modulu](rules-for-module-definition-statements.md)
