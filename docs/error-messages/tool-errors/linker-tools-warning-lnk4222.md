---
title: Upozornění linkerů LNK4222
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: f74379861ad04142fd78a8e307af165072c9cadd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183030"
---
# <a name="linker-tools-warning-lnk4222"></a>Upozornění linkerů LNK4222

exportovaný symbol symbol by neměl být přiřazený pořadovým číslem.

Následující symboly by neměly být exportovány podle pořadového čísla:

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

Tyto funkce jsou vždy umístěny podle názvu, pomocí `GetProcAddress`. Linker upozorňuje na tento druh exportu je, protože by mohlo dojít k většímu obrázku. K tomu může dojít, pokud je rozsah exportních pořadů velký s relativně malým počtem exportů. Například:

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

bude vyžadovat 100 slotů v tabulce adres pro export s 98 (2-99) pouze Filler. Na druhou stranu

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

bude vyžadovat dva sloty. (Nezapomeňte, že můžete také exportovat pomocí možnosti linkeru [/Export](../../build/reference/export-exports-a-function.md) .)
