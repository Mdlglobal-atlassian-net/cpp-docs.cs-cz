---
title: Chyba Linkerů LNK1179 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1179
dev_langs:
- C++
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d22ebb329d390d44aea44ff9dc6f3bf2f86a1d26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117451"
---
# <a name="linker-tools-error-lnk1179"></a>Chyba linkerů LNK1179

soubor je neplatný nebo poškozený: Duplicitní oddíl COMDAT 'filename.

Objekt modul obsahuje dva nebo více sekvence Comdat se stejným názvem.

Tato chyba může být způsobena pomocí [/H](../../build/reference/h-restrict-length-of-external-names.md), což omezuje délku externích názvů, a [/Gy](../../build/reference/gy-enable-function-level-linking.md), které balíčky funkcí do sekvencí Comdat.

## <a name="example"></a>Příklad

V následujícím kódu `function1` a `function2` jsou identické v prvních 8 znaků. Kompilace s **/Gy** a **/H8** vytvoří Chyba připojení.

```
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```