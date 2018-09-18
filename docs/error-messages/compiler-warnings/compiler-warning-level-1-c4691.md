---
title: Upozornění (úroveň 1) C4691 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4691
dev_langs:
- C++
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca063d61b799a10bd1d629fdba1293e0a66b0752
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095115"
---
# <a name="compiler-warning-level-1-c4691"></a>Kompilátor upozornění (úroveň 1) C4691

'type': neodkazovaná sestavení 'file', typ definovaný v aktuální překladové jednotce použít místo toho se očekával odkazovaný typ

Metadata souboru, který obsahuje původní definice typu není odkazován, a kompilátor používá místní typ definice.

V případě, kdy se znovu sestavit *souboru*, C4691 můžete ignorovat nebo vypnout pomocí direktivy pragma [upozornění](../../preprocessor/warning.md).  To znamená pokud soubor, který vytváříte je stejný jako soubor, kde se očekává, že kompilátor najít definice typu, můžete ignorovat C4691.

Ale neočekávané chování může dojít, pokud kompilátor používá definici, která nepochází ze stejného sestavení, která je popsána v metadatech; Typy CLR jsou zadány nejen podle názvu typu, ale také podle sestavení.  To znamená se liší od sestavení y.dll určitého typu Z určitého typu Z z.dll sestavení.

## <a name="example"></a>Příklad

Tato ukázka obsahuje původní definici typu.

```
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

## <a name="example"></a>Příklad

Tato ukázka odkazuje C4691_a.dll a deklaruje pole typu Original_Type.

```
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C4691.  Všimněte si, že tato ukázka obsahuje definici pro Original_Type a neodkazuje na C4691a.dll.

Pokud chcete vyřešit, odkazovat na soubor metadat, který obsahuje původní definici typu a odeberte místní deklarace a definice.

```
// C4691_c.cpp
// compile with: /clr /LD /W1
// C4691 expected

// Uncomment the following line to resolve.
// #using "C4691_a.dll"
#using "C4691_b.dll"

// Delete the following line to resolve.
ref class Original_Type;

public ref class MyClass : Client {};
```