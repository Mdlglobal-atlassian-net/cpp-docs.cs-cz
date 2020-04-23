---
title: Chyba linkerů LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: d85693cec11ef53a6bbbb60d8ced716d2a0bb131
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754343"
---
# <a name="linker-tools-error-lnk1179"></a>Chyba linkerů LNK1179

neplatný nebo poškozený soubor: duplicitní COMDAT 'název_souboru'

Modul objektu obsahuje dva nebo více comdatů se stejným názvem.

Tato chyba může být způsobena pomocí [/H](../../build/reference/h-restrict-length-of-external-names.md), který omezuje délku externí názvy a [/Gy](../../build/reference/gy-enable-function-level-linking.md), které balíčky funkce v COMDATs.

## <a name="example"></a>Příklad

V následujícím kódu `function1` `function2` a jsou identické v prvních osmi znaků. Kompilace s **/Gy** a **/H8** vytvoří chybu propojení.

```cpp
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```
