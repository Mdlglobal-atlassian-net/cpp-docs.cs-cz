---
title: Upozornění linkerů LNK4105
ms.date: 11/04/2016
f1_keywords:
- LNK4105
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
ms.openlocfilehash: 880c8519a530f492d0c322575a1386af8a7d0187
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475587"
---
# <a name="linker-tools-warning-lnk4105"></a>Upozornění linkerů LNK4105

žádný argument zadaný pomocí možnosti "možnost"; ignoruje se parametr

Toto varování se objeví jenom když [/Libpath](../../build/reference/libpath-additional-libpath.md) je možnost nastavená. Pokud tato možnost není zadán žádný adresář, linker ignoruje možnost a generuje toto upozornění.

Pokud chcete přepsat stávající nastavení knihovně prostředí nepotřebujete, odeberte z příkazového řádku linkeru možnost/Libpath. Pokud chcete použít jiný hledaný cestu pro knihovny, zadejte alternativní cestu, následující možnosti/Libpath.

## <a name="example"></a>Příklad

```
link /libpath:c:\filepath\lib bar.obj
```

bude směrovat linkeru, aby hledání požadované knihovny v `c:\filepath\lib` před vyhledáváním ve výchozích umístěních.