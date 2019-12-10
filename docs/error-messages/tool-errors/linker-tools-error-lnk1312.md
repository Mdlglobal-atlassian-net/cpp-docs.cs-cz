---
title: Chyba linkerů LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: e462d24f2eb54718ba73617146aab96bb14a66df
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990903"
---
# <a name="linker-tools-error-lnk1312"></a>Chyba linkerů LNK1312

soubor je neplatný nebo poškozený: nejde importovat sestavení.

Při sestavování sestavení je do Možnosti linkeru **/ASSEMBLYMODULE** předán jiný soubor než modul nebo sestavení kompilovaný s **/CLR** .  Pokud jste předali soubor objektu do **/ASSEMBLYMODULE**, stačí objekt předat přímo linkeru namísto **/ASSEMBLYMODULE**.

## <a name="example"></a>Příklad

Následující ukázka vytvořila soubor. obj.

```cpp
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

## <a name="example"></a>Příklad

Následující ukázka generuje LINKERŮ LNK1312.

```cpp
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```
