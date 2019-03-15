---
title: Rozšíření Microsoft pro C a C++
ms.date: 06/14/2018
helpviewer_keywords:
- or_eq operator
- ~ operator, extensions to C/C++
- '& operator, extensions to C/C++'
- '&= operator'
- iso646.h header
- Xor operator, Microsoft extensions to C/C++
- '!= operator'
- '! operator, extension to C++'
- Or operator, Microsoft extensions to C/C++
- ^ operator, extensions to C/C++
- ^= operator, C++ extensions
- xor_eq operator
- and_eq operator
- Microsoft extensions to C/C++
- '|= operator'
- '|| operator'
- And operator, extensions to C/C++
- NOT operator
- '&& operator'
- extensions, C language
- Visual C++, extensions to C/C++
- '| operator, extensions'
- not_eq operator
- Visual C, Microsoft extensions
- extensions
- compl method
ms.assetid: e811a74a-45ba-4c00-b206-2f2321b8689a
ms.openlocfilehash: dab8ac23be8b66ca84c57514c6c04e94dddebaae
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813887"
---
# <a name="microsoft-extensions-to-c-and-c"></a>Rozšíření Microsoft pro C a C++

Jazyk Visual C++ rozšiřuje standardy ANSI C a ANSI C++ následujícím způsobem.

## <a name="keywords"></a>Klíčová slova

Je přidáno několik klíčových slov. V seznamu v [klíčová slova](../../cpp/keywords-cpp.md), klíčová slova, která mají dvě úvodní podtržítka jsou rozšíření jazyka Visual C++.

## <a name="out-of-class-definition-of-static-const-integral-or-enum-members"></a>Mimo definici třídy statických const celočíselných (nebo výčtových) členů

V rámci standardu (**/Za**), je třeba definice mimo třídu pro datové členy, jak je znázorněno zde:

```cpp
class CMyClass  {
   static const int max = 5;
   int m_array[max];
}
// . . .
const int CMyClass::max;   // out of class definition
```

V části **/Ze**, je definice mimo třídu volitelná pro statické, konstantní celočíselné a konstantní výčtové datové členy. Pouze celočíselné a výčtové typy, které jsou statické a konstantní, mohou mít inicializátory ve třídě. Inicializační výraz musí být konstantní výraz.

Aby nedocházelo k chybám při definici mimo třídu je k dispozici v hlavičce souboru a soubor hlaviček je součástí více zdrojových souborů, použijte [selectany](../../cpp/selectany.md). Příklad:

```cpp
__declspec(selectany) const int CMyClass::max = 5;
```

## <a name="casts"></a>Přetypování

Kompilátor jazyka C i C++ podporuje tyto druhy přetypování, které nejsou ve standardu ANSI:

- Nestandardní přetypování vracející l-hodnoty. Příklad:

   ```C
   char *p;
   (( int * ) p )++;
   ```

   > [!NOTE]
   > Toto rozšíření je k dispozici pouze v jazyce C. V kódu jazyka C++ lze použít následující formy standardu ANSI C ke změně ukazatele, pokud je to ukazatel na jiný typ.

   Aby předchozí příklad vyhověl standardu ANSI C, měl by být přepsán následujícím způsobem.

   ```C
   p = ( char * )(( int * )p + 1 );
   ```

- Přetypování ukazatele na funkci na ukazatele na data, která nejsou ve standardu ANSI. Příklad:

   ```C
   int ( * pfunc ) ();
   int *pdata;
   pdata = ( int * ) pfunc;
   ```

   Chcete-li provést stejné přetypování a zároveň zachovat kompatibilitu se standardem ANSI, lze ukazatele na funkci přetypovat na typ `uintptr_t` před tím, než jej přetypujete na ukazatel na data:

   ```C
   pdata = ( int * ) (uintptr_t) pfunc;
   ```

## <a name="variable-length-argument-lists"></a>Seznamy argumentů s proměnnou délkou.

Kompilátor jazyka C i C++ podporuje deklarátor funkce, který určuje proměnný počet argumentů následovaný definicí funkce, která místo toho poskytuje typ:

```cpp
void myfunc( int x, ... );
void myfunc( int x, char * c )
{ }
```

## <a name="single-line-comments"></a>Jednořádkové komentáře

Kompilátor jazyka C podporuje jednořádkové komentáře, které lze vytvořit pomocí dvou znaků zpětného lomítka (//):

```C
// This is a single-line comment.
```

## <a name="scope"></a>Rozsah

Kompilátor jazyka C podporuje následující funkce vztahující se k rozsahu.

- Redefinice externích položek jako statických:

   ```C
   extern int clip();
   static int clip()
   {}
   ```

- Použití neškodné redefinice typedef v rámci stejného rozsahu:

   ```C
   typedef int INT;
   typedef int INT;
   ```

- Deklarátory funkce mají rozsah souboru:

   ```C
   void func1()
   {
       extern int func2( double );
   }
   int main( void )
   {
       func2( 4 );    //  /Ze passes 4 as type double
   }                  //  /Za passes 4 as type int
   ```

- Použití proměnných v rozsahu bloku, které jsou inicializovány pomocí nekonstantních výrazů:

   ```C
   int clip( int );
   int bar( int );
   int main( void )
   {
       int array[2] = { clip( 2 ), bar( 4 ) };
   }
   int clip( int x )
   {
       return x;
   }
   int bar( int x )
   {
       return x;
   }
   ```

## <a name="data-declarations-and-definitions"></a>Deklarace a definice dat

Kompilátor jazyka C podporuje následující funkce deklarace a definice dat.

- Smíšené znakové a řetězcové konstanty v inicializátoru:

   ```C
   char arr[5] = {'a', 'b', "cde"};
   ```

- Bitová pole, které mají základní typy jiné než **unsigned int** nebo **znaménkem**.

- Deklarátory, které nemají typ:

   ```C
   x;
   int main( void )
   {
       x = 1;
   }
   ```

- Pole bez velikosti jako poslední pole ve strukturách a sjednoceních:

   ```C
   struct zero
   {
       char *c;
       int zarray[];
   };
   ```

- Nepojmenované struktury (anonymní):

   ```C
   struct
   {
       int i;
       char *s;
   };
   ```

- Nepojmenovaná sjednocení (anonymní):

   ```C
   union
   {
       int i;
       float fl;
   };
   ```

- Nepojmenované členy:

   ```C
   struct s
   {
      unsigned int flag : 1;
      unsigned int : 31;
   }
   ```

## <a name="intrinsic-floating-point-functions"></a>Vnitřní funkce s plovoucí desetinnou čárkou

Oba x86 kompilátor jazyka C++ a kompilátor jazyka C podporuje vložené generování z `atan`, `atan2`, `cos`, `exp`, `log`, `log10`, `sin`, `sqrt`, a `tan` funkce při **/Oi** určena. Pokud jsou tyto vnitřní objekty použity, kompilátor jazyka C přijde o shodu se standardem ANSI, protože nenastavují proměnnou `errno`.

## <a name="passing-a-non-const-pointer-parameter-to-a-function-that-expects-a-reference-to-a-const-pointer-parameter"></a>Předání parametru nekonstantního ukazatele na funkci, která očekává odkaz na parametr konstantního ukazatele

Toto je rozšíření jazyka C++. Tento kód se zkompiluje podle **/Ze**:

```cpp
typedef   int   T;

const T  acT = 9;      // A constant of type 'T'
const T* pcT = &acT;   // A pointer to a constant of type 'T'

void func2 ( const T*& rpcT )   // A reference to a pointer to a constant of type 'T'
{
   rpcT = pcT;
}

T*   pT;               // A pointer to a 'T'

void func ()
{
   func2 ( pT );      // Should be an error, but isn't detected
   *pT   = 7;         // Invalidly overwrites the constant 'acT'
}
```

## <a name="iso646h-not-enabled"></a>ISO646. H není povoleno

V části **/Ze**, budete muset zahrnout soubor iso646.h, pokud chcete používat textové tvary následujících operátorů:

- && (and)

- &= (and_eq)

- & (bitand)

- &#124;(bitor)

- ~ (compl)

- ! (not)

- != (not_eq)

- &#124;&#124;(nebo)

- &#124;= (or_eq)

- ^ (xor)

- ^= (xor_eq)

## <a name="address-of-string-literal-has-type-const-char--not-const-char--"></a>Adresa řetězcového literálu má typ const char [], [] není const char (*)

V následujícím příkladu se výstup `char const (*)[4]` pod **/Za**, ale `char const [4]` pod **/Ze**.

```cpp
#include <stdio.h>
#include <typeinfo>

int main()
{
    printf_s("%s\n", typeid(&"abc").name());
}
```

## <a name="see-also"></a>Viz také:

- [/Za, /Ze (zakázání jazykových rozšíření)](za-ze-disable-language-extensions.md)
- [Možnosti kompilátoru MSVC](compiler-options.md)
- [Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
