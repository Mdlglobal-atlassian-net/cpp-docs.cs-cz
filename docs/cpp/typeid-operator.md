---
title: typeid – operátor
ms.date: 10/04/2019
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
ms.openlocfilehash: 93a2d3c494cd5aadafedcaaae9ec72809d633a4a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998746"
---
# <a name="typeid-operator"></a>typeid – operátor

## <a name="syntax"></a>Syntaxe

```
typeid(type-id)
typeid(expression)
```

## <a name="remarks"></a>Poznámky

Operátor **typeid** povoluje typ objektu, který se má určit v době běhu.

Výsledek **typeid** je `const type_info&`. Hodnota je odkaz na objekt `type_info`, který představuje *identifikátor typu* nebo typ *výrazu*, v závislosti na tom, který typ **typeid** je použit. Další informace naleznete v tématu [Třída type_info](../cpp/type-info-class.md).

Operátor **typeid** nefunguje se spravovanými typy (abstraktní deklarátory nebo instance). Informace o tom, jak získat <xref:System.Type> zadaného typu, naleznete v tématu [typeid](../extensions/typeid-cpp-component-extensions.md).

Operátor **typeid** provádí kontrolu za běhu při použití na l-hodnotu polymorfního typu třídy, kde skutečný typ objektu nelze určit pomocí zadaných statických informací. Takové případy jsou:

- odkaz na třídu,

- Ukazatel, na který se odkazuje `*`

- Ukazatel v dolním indexu (`[ ]`). (Není bezpečné použít dolní index s ukazatelem na polymorfní typ.)

Pokud *výraz* odkazuje na typ základní třídy, přesto je objekt skutečně typu odvozeného z této základní třídy, je výsledkem odkaz `type_info` pro odvozenou třídu. *Výraz* musí ukazovat na polymorfní typ (třídu s virtuálními funkcemi). V opačném případě je výsledkem `type_info` pro statickou třídu, na kterou se odkazuje ve *výrazu*. Kromě toho musí být ukazatel na odkaz, aby byl objekt použit jako ten, na který odkazuje. Bez přesměrování ukazatele bude výsledek `type_info` pro ukazatel, nikoli na to, na který odkazuje. Příklad:

```cpp
// expre_typeid_Operator.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <typeinfo>

class Base {
public:
   virtual void vvfunc() {}
};

class Derived : public Base {};

using namespace std;
int main() {
   Derived* pd = new Derived;
   Base* pb = pd;
   cout << typeid( pb ).name() << endl;   //prints "class Base *"
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"
   delete pd;
}
```

Pokud *výraz* odkazuje na ukazatel a hodnota ukazatele je nula, **typeid** vyvolá [výjimku bad_typeid](../cpp/bad-typeid-exception.md). Pokud ukazatel neukazuje na platný objekt, je vyvolána výjimka `__non_rtti_object`. Označuje pokus o analýzu RTTI, který aktivoval chybu, protože objekt je nějakým způsobem neplatný. (Například je to špatný ukazatel nebo kód nebyl zkompilován pomocí [/gr](../build/reference/gr-enable-run-time-type-information.md)).

Pokud *výraz* není ukazatel, a nikoli odkaz na základní třídu objektu, je výsledkem odkaz `type_info` reprezentující statický typ *výrazu*. *Statický typ* výrazu odkazuje na typ výrazu, který je známý v době kompilace. Sémantika provádění je při vyhodnocování statického typu výrazu ignorována. Kromě toho jsou odkazy ignorovány, pokud je to při stanovení statického typu výrazu možné:

```cpp
// expre_typeid_Operator_2.cpp
#include <typeinfo>

int main()
{
   typeid(int) == typeid(int&); // evaluates to true
}
```

**typeid** lze také použít v šablonách k určení typu parametru šablony:

```cpp
// expre_typeid_Operator_3.cpp
// compile with: /c
#include <typeinfo>
template < typename T >
T max( T arg1, T arg2 ) {
   cout << typeid( T ).name() << "s compared." << endl;
   return ( arg1 > arg2 ? arg1 : arg2 );
}
```

## <a name="see-also"></a>Viz také:

[Informace o typu běhového](../cpp/run-time-type-information.md)běhu \
[Klíčová slova](../cpp/keywords-cpp.md)
