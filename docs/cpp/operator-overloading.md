---
title: Přetížení operátoru
ms.date: 11/04/2016
f1_keywords:
- operator_cpp
- operator
helpviewer_keywords:
- redefinable operators [C++]
- non-redefinable operators [C++]
- operator keyword [C++]
- operators [C++], overloading
- operator overloading
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
ms.openlocfilehash: a16f68088ffffd6c3cf38f5ae3adda5f2d59fb57
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188568"
---
# <a name="operator-overloading"></a>Přetěžování operátoru

Klíčové slovo **Operator** deklaruje funkci určující, který *symbol operátora* znamená při použití na instance třídy. To dává operátor více než jeden význam nebo "přetížení". Kompilátor rozlišuje různé významy operátoru zkoumáním typů jeho operandů.

## <a name="syntax"></a>Syntaxe

> *type* **operátor** typu operátor *– symbol* **(** *parametr-list* **)**

## <a name="remarks"></a>Poznámky

Funkci většiny předdefinovaných operátorů můžete znovu definovat globálně nebo na základě třídy podle třídy. Přetížené operátory jsou implementovány jako funkce.

Název přetíženého operátoru je **operátor** *x*, kde *x* je operátor, jak je uveden v následující tabulce. Chcete-li například přetížit operátor sčítání, definujete funkci s názvem **Operator +** . Podobně pro přetížení operátoru sčítání/přiřazení **+=** definujte funkci s názvem **Operator + =** .

### <a name="redefinable-operators"></a>Znovu definovatelné operátory

|Operátor|Název|Typ|
|--------------|----------|----------|
|**,**|Čárka|Binární hodnota|
|**!**|Logický operátor NOT|Unární|
|**!=**|Nerovnost|Binární hodnota|
|**%**|Modulus|Binární hodnota|
|**%=**|Přiřazení modulus|Binární hodnota|
|**&**|Bitový operátor AND|Binární hodnota|
|**&**|Adresa|Unární|
|**&&**|Logický operátor AND|Binární hodnota|
|**&=**|Přiřazení bitového operátoru AND|Binární hodnota|
|**( )**|Volání funkce|—|
|**( )**|Operátor přetypování|Unární|
|**&#42;**|Násobení|Binární hodnota|
|**&#42;**|Ukazatel na odkaz|Unární|
|**&#42;=**|Přiřazení násobení|Binární hodnota|
|**+**|Sčítání|Binární hodnota|
|**+**|Unární plus|Unární|
|**++**|Přírůstek <sup>1</sup>|Unární|
|**+=**|Přiřazení sčítání|Binární hodnota|
|**-**|Odčítání|Binární hodnota|
|**-**|Unární negace|Unární|
|**--**|Snížení <sup>1</sup>|Unární|
|**-=**|Přiřazení odčítání|Binární hodnota|
|**->**|Výběr členů|Binární hodnota|
|**->&#42;**|Výběr ukazatele na člena|Binární hodnota|
|**/**|Dělení|Binární hodnota|
|**/=**|Přiřazení dělení|Binární hodnota|
|**\<**|Je menší než|Binární hodnota|
|**<<**|Posun doleva|Binární hodnota|
|**<<=**|Přiřazení posunutí doleva|Binární hodnota|
|**<=**|Je menší nebo rovno|Binární hodnota|
|**=**|Přiřazení|Binární hodnota|
|**==**|Rovnost|Binární hodnota|
|**>**|Větší než|Binární hodnota|
|**>=**|Je větší nebo rovno|Binární hodnota|
|**>>**|Posun doprava|Binární hodnota|
|**>>=**|Přiřazení posunutí doprava|Binární hodnota|
|**[ ]**|Dolní index pole|—|
|**^**|Exkluzivní nebo|Binární hodnota|
|**^=**|Exkluzivní nebo přiřazení|Binární hodnota|
|**&#124;**|Bitový inkluzivní operátor OR|Binární hodnota|
|**&#124;=**|Přiřazení s bitovým operátorem OR|Binární hodnota|
|**&#124;&#124;**|Logický operátor OR|Binární hodnota|
|**~**|Doplněk|Unární|
|**odstranění**|Odstranit|—|
|**new**|Nový|—|
|operátory převodu|operátory převodu|Unární|

existuje <sup>1</sup> dvě verze unárních operátorů přírůstek a snížení: postinkrement a Increment.

Další informace najdete v tématu [Obecná pravidla přetížení operátoru](../cpp/general-rules-for-operator-overloading.md) . Omezení pro různé kategorie přetížených operátorů jsou popsána v následujících tématech:

- [Unární operátory](../cpp/overloading-unary-operators.md)

- [Binární operátory](../cpp/binary-operators.md)

- [Přiřazení](../cpp/assignment.md)

- [Volání funkcí](../cpp/function-call-cpp.md)

- [Podskripty](../cpp/subscripting.md)

- [Přístup ke členu třídy](../cpp/member-access.md)

- [Zvýšení a snížení](../cpp/increment-and-decrement-operator-overloading-cpp.md)

- [Převody typů definovaných uživatelem](../cpp/user-defined-type-conversions-cpp.md)

Operátory zobrazené v následující tabulce nelze přečítat. Tabulka obsahuje symboly preprocesoru **#** a **##** .

### <a name="nonredefinable-operators"></a>Nonredefinable operátory

|Operátor|Název|
|-|-|
|**.**|Výběr členů|
|**.&#42;**|Výběr ukazatele na člena|
|**::**|Rozlišení rozsahu|
|**? :**|Podmíněné|
|**#**|Preprocesor převedený na řetězec|
|**##**|Zřetězení preprocesoru|

I když jsou přetížené operátory obvykle volány kompilátorem, když jsou zjištěny v kódu, mohou být vyvolány explicitně stejným způsobem jako jakýkoli člen nebo nečlenská funkce, která je volána:

```cpp
Point pt;
pt.operator+( 3 );  // Call addition operator to add 3 to pt.
```

## <a name="example"></a>Příklad

Následující příklad převede operátor **+** pro přidání dvou komplexních čísel a vrátí výsledek.

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

## <a name="see-also"></a>Viz také

[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
