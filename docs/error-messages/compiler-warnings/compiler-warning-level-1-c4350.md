---
title: Upozornění kompilátoru (úroveň 1) C4350
ms.date: 11/04/2016
f1_keywords:
- C4350
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
ms.openlocfilehash: 890ecd4fcec1212fa04a58b0eaab8c2eb4206763
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187216"
---
# <a name="compiler-warning-level-1-c4350"></a>Upozornění kompilátoru (úroveň 1) C4350

změna chování: byl zavolán člen 'member1' místo členu 'member2'

Rvalue nelze svázat s odkazem, který není typu const. Ve verzích vizuálu C++ před visual Studio 2003 bylo možné navazovat rvalue na odkaz, který není const, v přímé inicializaci. Tento kód nyní obsahuje upozornění.

Z důvodu zpětné kompatibility je stále možné navazovat vazby rvalue na nekonstantní odkazy, ale standardní převody jsou upřednostňovány všude, kde je to možné.

Toto upozornění představuje změnu chování z kompilátoru Visual C++ .NET 2002. Je-li povoleno, může být toto upozornění pravděpodobně zadáno pro správný kód. Může být například zadáno při použití šablony třídy **std:: auto_ptr** .

Pokud se zobrazí toto upozornění, Prohlédněte si kód a podívejte se, zda závisí na vazbách rvalue na nekonstantní odkazy. Přidání const k odkazu nebo poskytnutí dalšího přetížení const reference může problém vyřešit.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Následující ukázka generuje C4350:

```cpp
// C4350.cpp
// compile with: /W1
#pragma warning (default : 4350)
class A {};

class B
{
public:
   B(B&){}
   // try the following instead:
   // B(const B&){}

   B(A){}
   operator A(){ return A();}
};

B source() { return A(); }

int main()
{
   B ap(source());   // C4350
}
```
