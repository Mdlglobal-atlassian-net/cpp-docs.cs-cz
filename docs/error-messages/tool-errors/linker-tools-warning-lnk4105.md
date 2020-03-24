---
title: Upozornění linkerů LNK4105
ms.date: 11/04/2016
f1_keywords:
- LNK4105
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
ms.openlocfilehash: 655a6dfde77984cd0c941ec0d8abb0c4d099c80f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183290"
---
# <a name="linker-tools-warning-lnk4105"></a>Upozornění linkerů LNK4105

není zadaný žádný argument s možností Option; ignoruje se možnost.

K tomuto upozornění dochází pouze v případě, že je nastavena možnost [/LIBPATH](../../build/reference/libpath-additional-libpath.md) . Pokud s touto možností není zadán žádný adresář, linker ignoruje možnost a vygeneruje tuto zprávu upozornění.

Pokud nepotřebujete přepsat existující nastavení knihovny prostředí, odeberte možnost/LIBPATH z příkazového řádku linkeru. Pokud chcete pro knihovny použít alternativní cestu pro hledání, zadejte alternativní cestu za možností/LIBPATH.

## <a name="example"></a>Příklad

```
link /libpath:c:\filepath\lib bar.obj
```

Před vyhledáváním ve výchozích umístěních nasměruje linker, aby hledal požadované knihovny v `c:\filepath\lib`.
