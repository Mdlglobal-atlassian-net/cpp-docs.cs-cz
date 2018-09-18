---
title: Přetížení operátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- operator_cpp
- operator
dev_langs:
- C++
helpviewer_keywords:
- redefinable operators [C++]
- non-redefinable operators [C++]
- operator keyword [C++]
- operators [C++], overloading
- operator overloading
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff6be1e24371692c53621cf6583677cc97d631b4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059188"
---
# <a name="operator-overloading"></a>Přetížení operátoru

**Operátor** – klíčové slovo deklaruje funkci určíte, co *symbol operátoru* znamená, že při použití u instance třídy. Operátor, který poskytuje více než jeden význam, nebo "přetížení" ho. Kompilátor rozlišuje mezi různé významy operátor prozkoumáním typy jeho operandů.

## <a name="syntax"></a>Syntaxe

> *typ* **operátor** *symbol operátoru* **(** *seznam parametrů* **)**

## <a name="remarks"></a>Poznámky

Funkce nejvíce integrovaných operátory možné předefinovat globálně nebo na základě třídy třídy. Přetížené operátory jsou implementovány jako funkce.

Název přetíženého operátoru je **operátor** *x*, kde *x* je operátor, který se zobrazí v následující tabulce. Pro přetížení operátoru sčítání, můžete definovat funkci s názvem **operátor +**. Podobně, přetížení operátoru sčítání/přiřazení **+=**, definovat funkci s názvem **operator +=**.

### <a name="redefinable-operators"></a>Které lze znovu definovat operátory

|Operátor|Název|Typ|
|--------------|----------|----------|
|**,**|Čárka|binární|
|**\!**|Logický operátor NOT|Unární|
|**\!=**|Nerovnost|binární|
|**%**|Modulus|binární|
|**%=**|Přiřazení modulus|binární|
|**&**|Bitový operátor AND|binární|
|**&**|Adresa|Unární|
|**&&**|Logický operátor AND|binární|
|**&=**|Přiřazení bitového operátoru AND|binární|
|**( )**|Volání funkce|—|
|**( )**|Operátor přetypování|Unární|
|**&#42;**|Násobení|binární|
|**&#42;**|Přesměrování ukazatele|Unární|
|**&#42;=**|Přiřazení násobení|binární|
|**+**|Sčítání|binární|
|**+**|Unární Plus|Unární|
|**++**|Přírůstek <sup>1</sup>|Unární|
|**+=**|Přiřazení sčítání|binární|
|**-**|Odčítání|binární|
|**-**|Unární negace|Unární|
|**--**|Snížení <sup>1</sup>|Unární|
|**-=**|Přiřazení odčítání|binární|
|**->**|Výběr členů|binární|
|**->&#42;**|Výběr pointer-to-member|binární|
|**/**|Dělení|binární|
|**/=**|Přiřazení dělení|binární|
|**\<**|Menší než|binární|
|**<<**|Posun doleva|binární|
|**<<=**|Přiřazení posunutí doleva|binární|
|**<=**|Menší nebo rovno|binární|
|**=**|Přiřazení|binární|
|**==**|Rovnost|binární|
|**>**|Větší než|binární|
|**>=**|Větší nebo rovno|binární|
|**>>**|Posun doprava|binární|
|**>>=**|Operátor posunutí doprava|binární|
|**[ ]**|Dolní index pole|—|
|**^**|Exkluzivní operátor OR|binární|
|**^=**|Exkluzivní OR přiřazení|binární|
|**&#124;**|Bitový inkluzivní operátor OR|binární|
|**&#124;=**|Přiřazení s bitovým operátorem OR|binární|
|**&#124;&#124;**|Logický operátor OR|binární|
|**~**|Doplněk|Unární|
|**delete**|Odstranit|—|
|**new**|Nový|—|
|operátory převodu|operátory převodu|Unární|

<sup>1</sup> zvýšit dvě verze Unární a operátory snížení existovat: preinkrement a postinkrement.

Zobrazit [obecná pravidla přetížení operátoru](../cpp/general-rules-for-operator-overloading.md) Další informace. Omezení pro různé kategorie přetížené operátory jsou popsány v následujících tématech:

- [Unární operátory](../cpp/overloading-unary-operators.md)

- [Binární operátory](../cpp/binary-operators.md)

- [Přiřazení](../cpp/assignment.md)

- [Volání funkcí](../cpp/function-call-cpp.md)

- [Podskripty](../cpp/subscripting.md)

- [Přístup ke členům třídy](../cpp/member-access.md)

- [Inkrementace a dekrementace](../cpp/increment-and-decrement-operator-overloading-cpp.md).

- [Převody typů definovaných uživatelem](../cpp/user-defined-type-conversions-cpp.md)

Nemohou být přetíženy operátory uvedené v následující tabulce. Tabulka obsahuje symboly preprocesoru **#** a **##**.

### <a name="nonredefinable-operators"></a>Operátory Nonredefinable

|Operátor|Název|
|-|-|
|**.**|Výběr členů|
|**.&#42;**|Výběr pointer-to-member|
|**::**|Rozlišení rozsahu|
|**? :**|Podmiňovací operátor|
|**#**|Preprocesoru převést na řetězec|
|**##**|Zřetězit preprocesoru|

I když přetížené operátory jsou obvykle nevolá implicitně kompilátorem vyskytne v kódu, mohou být volány explicitně stejným způsobem jako člen nebo nečlenské funkce se volá:

```cpp
Point pt;
pt.operator+( 3 );  // Call addition operator to add 3 to pt.
```

## <a name="example"></a>Příklad

Následující příklad přetížení **+** operátor přidáte komplexní dvě čísla a vrátí výsledek.

```cpp
// operator_overloading.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Complex {
   Complex( double r, double i ) : re(r), im(i) {}
   Complex operator+( Complex &other );
   void Display( ) {   cout << re << ", " << im << endl; }
private:
   double re, im;
};

// Operator overloaded using a member function
Complex Complex::operator+( Complex &other ) {
   return Complex( re + other.re, im + other.im );
}

int main() {
   Complex a = Complex( 1.2, 3.4 );
   Complex b = Complex( 5.6, 7.8 );
   Complex c = Complex( 0.0, 0.0 );

   c = a + b;
   c.Display();
}
```

```Output
6.8, 11.2
```

## <a name="in-this-section"></a>V tomto oddílu

- [Obecná pravidla přetížení operátoru](../cpp/general-rules-for-operator-overloading.md)

- [Přetížení unárních operátorů](../cpp/overloading-unary-operators.md)

- [Binární operátory](../cpp/binary-operators.md)

- [Přiřazení](../cpp/assignment.md)

- [Volání funkcí](../cpp/function-call-cpp.md)

- [Podskripty](../cpp/subscripting.md)

- [Přístup ke členu](../cpp/member-access.md)

## <a name="see-also"></a>Viz také:

[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)