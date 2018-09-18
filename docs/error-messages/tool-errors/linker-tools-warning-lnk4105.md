---
title: Upozornění Linkerů LNK4105 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4105
dev_langs:
- C++
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4411421741cf8bf7c714a6322d58bd177e7e7270
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024980"
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