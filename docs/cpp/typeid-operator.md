---
title: typeid – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db9e019c3c9cc7e7e71726a8bd11e83ca4c99cdf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020659"
---
# <a name="typeid-operator"></a>typeid – operátor

## <a name="syntax"></a>Syntaxe

```
typeid(type-id)
typeid(expression)
```

## <a name="remarks"></a>Poznámky

**Typeid** operátor umožňuje typ objektu má být stanovena v době běhu.

Výsledek **typeid** je `const type_info&`. Hodnota je odkaz na `type_info` objekt, který představuje buď *id typu* nebo typu *výraz*podle toho, jaký tvar operátoru **typeid** se používá. Zobrazit [type_info – třída](../cpp/type-info-class.md) Další informace.

**Typeid** operátor nepracuje se spravovanými typy (abstraktní deklarátory nebo instance), najdete v článku [typeid](../windows/typeid-cpp-component-extensions.md) Další informace o získání <xref:System.Type> zadaného typu.

**Typeid** operátor provádí kontrolu za běhu při použití na l hodnotu polymorfního typu třídy, kde nelze určit skutečný typ objektu pomocí poskytnutých statických údajů. Takové případy jsou:

- odkaz na třídu,

- Ukazatel, přístup přes ukazatel pomocí \*

- indexovaný ukazatel (tj. [ ]). (Použití indexu s ukazatelem na polymorfní typ není obecně bezpečné.)

Pokud *výraz* odkazuje na typ základní třídy, ale objekt je ve skutečnosti typem odvozeným ze základní třídy, `type_info` reference pro odvozenou třídu, je výsledek. *Výraz* musí odkazovat na polymorfní typ (třídu s virtuálními funkcemi). V opačném případě je výsledek `type_info` pro statické třídy uvedené v *výraz*. Dále musí být ukazatel odkázán tak, aby se použil objekt, na který odkazuje. Bez odkázání ukazatele, výsledkem bude `type_info` pro ukazatele, nikoli odkazuje na. Příklad:

```cpp
// expre_typeid_Operator.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <typeinfo.h>

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

Pokud *výraz* je odkazován ukazatelem a hodnota ukazatele je nula, **typeid** vyvolá [bad_typeid – výjimka](../cpp/bad-typeid-exception.md). Pokud ukazatel neodkazuje na platný objekt `__non_rtti_object` je vyvolána výjimka, označující pokus analyzovat RTTI, která způsobila chybu (např. narušení přístupu), protože objekt je nějakým způsobem neplatný (Chybný ukazatel nebo kód nebyl zkompilován s [GR](../build/reference/gr-enable-run-time-type-information.md)).

Pokud *výraz* není ukazatelem ani odkazem na základní třídu objektu, výsledkem je `type_info` představující statický typ odkazu *výraz*. *Statického typu* výrazu odkazuje na typ výrazu jako je znám v době kompilace. Sémantika provádění je při vyhodnocování statického typu výrazu ignorována. Kromě toho jsou odkazy ignorovány, pokud je to při stanovení statického typu výrazu možné:

```cpp
// expre_typeid_Operator_2.cpp
#include <typeinfo>

int main()
{
   typeid(int) == typeid(int&); // evaluates to true
}
```

**typeid** lze také použít v šablonách pro určení typu parametru šablony:

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

[Informace o typu modulu runtime](../cpp/run-time-type-information.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)