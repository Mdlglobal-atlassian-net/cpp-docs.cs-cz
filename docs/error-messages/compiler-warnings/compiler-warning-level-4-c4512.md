---
title: Upozornění kompilátoru (úroveň 4) C4512
ms.date: 11/04/2016
f1_keywords:
- C4512
helpviewer_keywords:
- C4512
ms.assetid: afb68995-684a-4be5-a73a-38d7a16dc030
ms.openlocfilehash: c09832a4f27bff51cbb5bd847a3123e62c9ee8d5
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991012"
---
# <a name="compiler-warning-level-4-c4512"></a>Upozornění kompilátoru (úroveň 4) C4512

' class ': operátor přiřazení nelze vygenerovat

Kompilátor nemůže pro danou třídu vygenerovat operátor přiřazení. Nebyl vytvořen žádný operátor přiřazení.

Operátor přiřazení pro základní třídu, která není přístupná odvozenou třídou, může toto upozornění způsobit.

Chcete-li se tomuto upozornění vyhnout, zadejte uživatelsky definovaný operátor přiřazení pro třídu.

Kompilátor také vygeneruje funkci operátoru přiřazení pro třídu, která nedefinuje jednu. Tento operátor přiřazení je kopírování členů kopie datových členů objektu. Protože `const` datové položky nelze po inicializaci upravovat, pokud třída obsahuje položku `const`, výchozí operátor přiřazení nefunguje. Další příčinou upozornění C4512 je deklarace nestatického datového členu typu odkazu. Pokud je záměrem vytvořit nekopírovací typ, je nutné také zabránit vytvoření výchozího kopírovacího konstruktoru.

Upozornění C4512 pro váš kód můžete vyřešit jedním ze tří způsobů:

- Explicitně definujte operátor přiřazení pro třídu.

- Odeberte **const** nebo operátor reference z datové položky ve třídě.

- Upozornění můžete potlačit pomocí příkazu #pragma [Warning](../../preprocessor/warning.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C4512.

```cpp
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
