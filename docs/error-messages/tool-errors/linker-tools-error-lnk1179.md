---
title: Chyba linkerů LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: a267019f1be08cc8dcffdff3b4ba0b73357cccd4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183954"
---
# <a name="linker-tools-error-lnk1179"></a>Chyba linkerů LNK1179

soubor je neplatný nebo poškozený: duplicitní COMDAT ' filename '

Modul objektu obsahuje dva nebo více sekvence COMDAT se stejným názvem.

Tato chyba může být způsobena použitím [/h](../../build/reference/h-restrict-length-of-external-names.md), která omezuje délku externích názvů a [/Gy](../../build/reference/gy-enable-function-level-linking.md), která zabalí funkce v sekvence COMDAT.

## <a name="example"></a>Příklad

V následujícím kódu jsou `function1` a `function2` v prvních osmi znacích identické. Kompilace s **/Gy** a **/h8** vytvoří chybu propojení.

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
