---
title: Chyba linkerů LNK2033
ms.date: 11/04/2016
f1_keywords:
- LNK2033
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
ms.openlocfilehash: 407f5eaf94a0e2da43425c3bbdd1955a88c95f14
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991187"
---
# <a name="linker-tools-error-lnk2033"></a>Chyba linkerů LNK2033

Nerozpoznaný token TypeRef (token) pro typ

Typ nemá v metadatech MSIL definici.

LINKERŮ LNK2033 může nastat při kompilaci s možností **/clr: Safe** a tam, kde je pouze Dopředná deklarace pro typ v modulu MSIL, kde je typ odkazován v modulu MSIL.

Typ musí být definován v oblasti **/clr: Safe**.

Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující ukázka generuje LINKERŮ LNK2033.

```cpp
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
