---
title: Chyba linkerů LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: 49fa7e7963d6bb561e1602b58fe1f26c5f3d54bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436228"
---
# <a name="linker-tools-error-lnk1312"></a>Chyba linkerů LNK1312

soubor je neplatný nebo poškozený: nelze importovat sestavení

Při sestavování sestavení, soubor než modul nebo sestavení zkompilovaná **/CLR** byl předán **/ASSEMBLYMODULE** – možnost linkeru.  Pokud jste předali soubor objektu do **/ASSEMBLYMODULE**, stačí pouze předat objekt přímo do linkeru, místo na **/ASSEMBLYMODULE**.

## <a name="example"></a>Příklad

Následující příklad vytvoří soubor .obj.

```
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

## <a name="example"></a>Příklad

Následující ukázka generuje LNK1312.

```
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```