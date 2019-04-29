---
title: Kompilátor upozornění (úroveň 1) C4350
ms.date: 11/04/2016
f1_keywords:
- C4350
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
ms.openlocfilehash: 8f23751151d8d83c68608d926ef422d56dde41a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384202"
---
# <a name="compiler-warning-level-1-c4350"></a>Kompilátor upozornění (úroveň 1) C4350

změna chování: byl zavolán člen 'member1' místo členu 'member2'

R-hodnoty nemůže být vázán na nekonstantní odkaz. Ve verzích aplikace Visual C++ před Visual Studio 2003 bylo možné vytvořit vazbu rvalue na nekonstantní odkaz v přímé inicializaci. Tento kód nyní poskytuje upozornění.

Z důvodu zpětné kompatibility je stále možné svázat nekonstantní odkazy rvalue, ale standardní převody jsou upřednostňované, kdykoli je to možné.

Toto upozornění představuje ke změně chování od Visual C++ .NET 2002 kompilátor. Pokud je povoleno, toto upozornění může mít pravděpodobně pro správný kód. To může být Mějme například při použití **std::auto_ptr** šablony třídy.

Pokud se zobrazí toto upozornění, prozkoumejte kód a zjistěte, jestli je závislý na rvalue vazby na nekonstantní odkazy. Přidání odkazu na konstantní nebo které uvádějí další přetížení odkaz na objekt může problém vyřešit.

Toto upozornění je vypnuto ve výchozím nastavení. Další informace najdete v tématu [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

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