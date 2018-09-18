---
title: Upozornění Linkerů LNK4222 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4222
dev_langs:
- C++
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abc4f85fbc361b37d9325f9d395a1c34e1eeed2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106922"
---
# <a name="linker-tools-warning-lnk4222"></a>Upozornění linkerů LNK4222

exportovanému symbolu 'symbol' by se nemělo přiřadit ordinální číslo.

Podle pořadových čísel nesmí exportovat těchto symbolů:

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

Tyto funkce jsou vždy umístěny podle názvu, používat `GetProcAddress`. Linker upozorňuje na tento druh export je, protože by mohlo způsobit větší obrázek. To může dojít, pokud je velká s relativně málo exporty oblasti ordinální exporty. Například

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

bude vyžadovat 100 sloty v exportní tabulce adresu s 98 z nich stačí přednastavené (2 až 99). Na druhou stranu

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

bude vyžadovat dvěma sloty. (Mějte na paměti, že můžete také exportovat s [/EXPORT](../../build/reference/export-exports-a-function.md) – možnost linkeru.)