---
title: Chyba linkerů LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: 71aba1f20cfaf5b6b9ec33d43ebde594e381921f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391410"
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