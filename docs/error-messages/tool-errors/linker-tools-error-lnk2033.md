---
title: Chyba linkerů LNK2033
ms.date: 11/04/2016
f1_keywords:
- LNK2033
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
ms.openlocfilehash: 7e95823e23215848ff3e5d201171523c9009eb2d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298903"
---
# <a name="linker-tools-error-lnk2033"></a>Chyba linkerů LNK2033

Nerozpoznaný token typeref (token) pro 'type'

Typ nemá definici v metadatech jazyka MSIL.

LNK2033 může dojít při kompilaci s **/CLR: safe** a ve kterých je Dopředná deklarace pro typ v modulu jazyka MSIL, kde se odkazuje typ v modulu MSIL.

Tento typ musí být definován v rámci **/CLR: safe**.

Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující ukázka generuje LNK2033.

```
// LNK2033.cpp
// compile with: /clr:safe
// LNK2033 expected
ref class A;
ref class B {};

int main() {
   A ^ aa = nullptr;
   B ^ bb = nullptr;   // OK
};
```