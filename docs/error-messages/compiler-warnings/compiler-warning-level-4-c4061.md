---
title: Kompilátor upozornění (úroveň 4) C4061
ms.date: 04/05/2019
f1_keywords:
- C4061
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
ms.openlocfilehash: 073e3e9cb1cb5bb6b0f66157c986072227960212
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401420"
---
# <a name="compiler-warning-level-4-c4061"></a>Kompilátor upozornění (úroveň 4) C4061

> Enumerátor "*identifikátor*"v přepnutí výčtu'*výčet*' není explicitně zpracován popisek případu

Zadaný čítač *identifikátor* nemá žádná přidružená obslužná rutina `switch` příkaz, který má `default` případ. Chybí příkaz case může být dohledu nebo nemusí být problém. Může záviset na Určuje, zda je čítač zařizuje služba výchozí případ nebo ne. Pro související upozornění na nevyužitých výčty v `switch` příkazy, které nemají `default` případu, viz [C4062](compiler-warning-level-4-c4062.md).

Toto upozornění je vypnuto ve výchozím nastavení. Další informace o tom, jak povolit upozornění, které jsou ve výchozím nastavení vypnuta, najdete v části [kompilátoru upozornění, která je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4061; přidáte případ pro chybí enumerátor opravit:

```cpp
// C4061.cpp
// compile with: /W4
#pragma warning(default : 4061)

enum E { a, b, c };
void func ( E e )
{
   switch(e)
   {
      case a:
      case b:
      default:
         break;
   }   // C4061 c' not handled
}

int main()
{
}
```

## <a name="see-also"></a>Viz také:

[Upozornění kompilátoru (úroveň 4) C4062](compiler-warning-level-4-c4062.md)
