---
title: Kompilátor upozornění (úroveň 4) C4512
ms.date: 11/04/2016
f1_keywords:
- C4512
helpviewer_keywords:
- C4512
ms.assetid: afb68995-684a-4be5-a73a-38d7a16dc030
ms.openlocfilehash: c5e84fe1d0e558e689e48fba8df112861f81acec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220987"
---
# <a name="compiler-warning-level-4-c4512"></a>Kompilátor upozornění (úroveň 4) C4512

'class': operátor přiřazení se nepodařilo vygenerovat.

Kompilátor nemůže generovat operátor přiřazení pro danou třídu. Byl vytvořen žádný operátor přiřazení.

Operátor přiřazení základní třídy, které nejsou přístupné prostřednictvím odvozené třídy mohou způsobit, že toto upozornění.

K tomuto upozornění předejít, zadejte operátor přiřazení definované uživatelem pro třídu.

Kompilátor vygeneruje také funkci operátoru přiřazení pro třídu, která žádné nedefinuje. Tento operátor přiřazení je kopírování členů datové členy objektu. Protože `const` datové položky nelze změnit po inicializaci, pokud třída obsahuje `const` položky, výchozí operátor přiřazení nebude fungovat. Další příčinou C4512 upozornění je deklarovaná nestatický datový člen odkazového typu. Pokud je cílem vytvoření nekopírovatelných typu, je nutné zabránit vytvoření výchozího konstruktoru kopie.

Vyřešit upozornění C4512 pro váš kód v jednom ze tří způsobů:

- Explicitně definujte operátor přiřazení pro třídu.

- Odebrat **const** nebo operátor odkaz z položky dat ve třídě.

- Použijte #pragma [upozornění](../../preprocessor/warning.md) příkaz upozornění můžete potlačit.

## <a name="example"></a>Příklad

Následující ukázka generuje C4512.

```
// C4512.cpp
// compile with: /EHsc /W4
// processor: x86

class Base {
private:
   const int a;

public:
   Base(int val = 0) : a(val) {}
   int get_a() { return a; }
};   // C4512 warning

class Base2 {
private:
   const int a;

public:
   Base2(int val = 0) : a(val) {}
   Base2 & operator=( const Base2 & ) { return *this; }
   int get_a() { return a; }
};

// Type designer intends this to be non-copyable because it has a
// reference member
class Base3
{
private:
   char& cr;

public:
   Base3(char& r) : cr(r) {}
   // Uncomment the following line to explicitly disable copying:
   // Base3(const Base3&) = delete;
};   // C4512 warning

int main() {
   Base first;
   Base second;

   // OK
   Base2 first2;
   Base2 second2;

   char c = 'x';
   Base3 first3(c);
   Base3 second3 = first3; // C2280 if no default copy ctor
}
```