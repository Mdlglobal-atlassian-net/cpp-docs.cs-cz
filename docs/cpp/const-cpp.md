---
title: const (C++)
ms.date: 11/04/2016
f1_keywords:
- const_cpp
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
ms.openlocfilehash: cc1f117cc5f26edf9cd85461281b925c97fa5225
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180301"
---
# <a name="const-c"></a>const (C++)

Při úpravách deklarace dat určuje klíčové slovo **const** , že objekt nebo proměnnou nelze upravovat.

## <a name="syntax"></a>Syntaxe

```
const declaration ;
member-function const ;
```

## <a name="const-values"></a>konstantní hodnoty

Klíčové slovo **const** určuje, že hodnota proměnné je konstantní a instruuje kompilátor, aby zabránil programátorovi v úpravách.

```cpp
// constant_values1.cpp
int main() {
   const int i = 5;
   i = 10;   // C3892
   i++;   // C2105
}
```

V C++aplikaci můžete použít klíčové slovo **const** namísto [#define](../preprocessor/hash-define-directive-c-cpp.md) direktivy preprocesoru k definování konstantních hodnot. Hodnoty definované pomocí **const** jsou předmětem kontroly typu a lze je použít místo konstantních výrazů. V C++aplikaci můžete určit velikost pole s **konstantní** proměnnou následujícím způsobem:

```cpp
// constant_values2.cpp
// compile with: /c
const int maxarray = 255;
char store_char[maxarray];  // allowed in C++; not allowed in C
```

V jazyce C směřují výchozí hodnoty konstant na externí propojení tak, aby se mohly zobrazit pouze ve zdrojových souborech. V jazyce C++ směřují výchozí hodnoty konstant na vnitřní propojení tak, aby se mohly zobrazit pouze v rámci souborů hlaviček.

Klíčové slovo **const** lze také použít v deklaracích ukazatelů.

```cpp
// constant_values3.cpp
int main() {
   char *mybuf = 0, *yourbuf;
   char *const aptr = mybuf;
   *aptr = 'a';   // OK
   aptr = yourbuf;   // C3892
}
```

Ukazatel na proměnnou deklarovaný jako **const** lze přiřadit pouze k ukazateli, který je také deklarován jako **const**.

```cpp
// constant_values4.cpp
#include <stdio.h>
int main() {
   const char *mybuf = "test";
   char *yourbuf = "test2";
   printf_s("%s\n", mybuf);

   const char *bptr = mybuf;   // Pointer to constant data
   printf_s("%s\n", bptr);

   // *bptr = 'a';   // Error
}
```

Ukazatele na data konstanty lze použít jako parametry funkce pro zabránění úpravy parametru předaného prostřednictvím ukazatele.

Pro objekty, které jsou deklarovány jako **const**, lze volat pouze konstantní členské funkce. Tím je zajištěno, že objekt konstanty nebude nikdy změněn.

```cpp
birthday.getMonth();    // Okay
birthday.setMonth( 4 ); // Error
```

Pro nekonstantní objekt lze volat konstantní nebo nekonstantní členské funkce. Můžete také přetížit členskou funkci pomocí klíčového slova **const** ; To umožňuje volání jiné verze funkce pro konstantní a nekonstantní objekty.

Nelze deklarovat konstruktory nebo destruktory pomocí klíčového slova **const** .

## <a name="const-member-functions"></a>const členské funkce

Deklarace členské funkce pomocí klíčového slova **const** určuje, že funkce je funkce jen pro čtení, která nemění objekt, pro který je volána. Konstantní členská funkce nemůže změnit žádné nestatické datové členy ani volat žádné členské funkce, které nejsou konstantní. Chcete-li deklarovat konstantní členskou funkci, umístěte klíčové slovo **const** za pravou závorku seznamu argumentů. Klíčové slovo **const** je vyžadováno v deklaraci i v definici.

```cpp
// constant_member_function.cpp
class Date
{
public:
   Date( int mn, int dy, int yr );
   int getMonth() const;     // A read-only function
   void setMonth( int mn );   // A write function; can't be const
private:
   int month;
};

int Date::getMonth() const
{
   return month;        // Doesn't modify anything
}
void Date::setMonth( int mn )
{
   month = mn;          // Modifies data member
}
int main()
{
   Date MyDate( 7, 4, 1998 );
   const Date BirthDate( 1, 18, 1953 );
   MyDate.setMonth( 4 );    // Okay
   BirthDate.getMonth();    // Okay
   BirthDate.setMonth( 4 ); // C2662 Error
}
```

## <a name="c-and-c-const-differences"></a>Rozdíly v C++ jazyce C a const

Pokud deklarujete proměnnou jako **const** v souboru zdrojového kódu jazyka C, uděláte to takto:

```cpp
const int i = 2;
```

Následně je možné tuto proměnnou použít v jiném modulu takto:

```cpp
extern const int i;
```

Ale chcete-li získat stejné chování C++v nástroji, musíte deklarovat proměnnou **const** jako:

```cpp
extern const int i = 2;
```

Pokud chcete deklarovat **externou** proměnnou v souboru C++ zdrojového kódu pro použití v souboru zdrojového kódu jazyka C, použijte:

```cpp
extern "C" const int x=10;
```

pro zabránění v úpravě názvu kompilátorem jazyka C++.

## <a name="remarks"></a>Poznámky

Pokud je použit seznam parametrů členské funkce, klíčové slovo **const** určuje, že funkce neupraví objekt, pro který je vyvolán.

Další informace o **const**naleznete v následujících tématech:

- [Ukazatelé const a volatile](../cpp/const-and-volatile-pointers.md)

- [Kvalifikátory typu (Referenční dokumentace jazyka C)](../c-language/type-qualifiers.md)

- [volatile](../cpp/volatile-cpp.md)

- [#define](../preprocessor/hash-define-directive-c-cpp.md)

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)
