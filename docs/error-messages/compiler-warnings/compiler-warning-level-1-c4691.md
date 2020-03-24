---
title: Upozornění kompilátoru (úroveň 1) C4691
ms.date: 11/04/2016
f1_keywords:
- C4691
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
ms.openlocfilehash: 8065129e20b627eb387421455527f6aaec3fdc2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175373"
---
# <a name="compiler-warning-level-1-c4691"></a>Upozornění kompilátoru (úroveň 1) C4691

Typ: odkazovaný typ se očekával v neodkazovaném sestavení ' file ', typ definovaný v aktuální jednotce překladu se místo toho použil.

Na soubor metadat obsahující definici původního typu se neodkazuje a kompilátor používá definici místního typu.

V případě, že znovu sestavíte *soubor*, C4691 lze ignorovat nebo vypnout pomocí [Upozornění](../../preprocessor/warning.md)pragma.  To znamená, že pokud soubor, který sestavíte, je stejný jako soubor, ve kterém kompilátor očekává nalezení definice typu, můžete ignorovat C4691.

Pokud však kompilátor používá definici, která není ze stejného sestavení, na které je odkazováno v metadatech, může dojít k neočekávanému chování. Typy CLR jsou zadány nejen názvem typu, ale také sestavením.  To znamená, že typ z z Assembly z. dll je jiný než typ z sestavení y. dll.

## <a name="example"></a>Příklad

Tato ukázka obsahuje původní definici typu.

```cpp
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

## <a name="example"></a>Příklad

Tato ukázka odkazuje na C4691_a. dll a deklaruje pole typu Original_Type.

```cpp
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C4691.  Všimněte si, že tento příklad obsahuje definici pro Original_Type a neodkazuje na C4691a. dll.

Pro vyřešení, odkazování na soubor metadat, který obsahuje definici původní typ a odebrání místní deklarace a definice.

```cpp
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
