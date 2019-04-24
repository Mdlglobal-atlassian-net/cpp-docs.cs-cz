---
title: Upozornění linkerů LNK4222
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: 52a4fee532eb9997dcf013f95246b27fdffc4c20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160403"
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