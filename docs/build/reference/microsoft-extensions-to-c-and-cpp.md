---
title: Rozšíření Microsoft pro C a C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 903ad9d5a44bb455bede52aa3456d03456f54d13
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379338"
---
# <a name="microsoft-extensions-to-c-and-c"></a>Rozšíření Microsoft pro C a C++
Jazyk Visual C++ rozšiřuje standardy ANSI C a ANSI C++ následujícím způsobem.  
  
## <a name="keywords"></a>Klíčová slova  
 Je přidáno několik klíčových slov. V seznamu [klíčová slova](../../cpp/keywords-cpp.md), klíčová slova, která mají dva úvodní podtržítka jsou rozšíření Visual C++.  
  
## <a name="out-of-class-definition-of-static-const-integral-or-enum-members"></a>Definice statických konstantních celočíselných (nebo výčtových) členů mimo třídu  
 V části standardní (**/Za**), je nutno provést definici třídy na více systémů pro datové členy, jak je vidět tady:  
  
```  
  
      class CMyClass  {  
   static const int max = 5;  
   int m_array[max];  
}  
...  
const int CMyClass::max;   // out of class definition  
```  
  
 V části **/Ze**, definice na více systémů třídy je volitelný pro statické, const integrální a const výčtu datových členů. Pouze celočíselné a výčtové typy, které jsou statické a konstantní, mohou mít inicializátory ve třídě. Inicializační výraz musí být konstantní výraz.  
  
 Chcete-li se vyhnout se chybám při definici třídy na více systémů je zadané v hlavičce souboru a soubor hlaviček je součástí několika zdrojových souborů, použijte [selectany](../../cpp/selectany.md). Příklad:  
  
```  
__declspec(selectany) const int CMyClass::max = 5;  
```  
  
## <a name="casts"></a>Přetypování  
 Kompilátor jazyka C i C++ podporuje tyto druhy přetypování, které nejsou ve standardu ANSI:  
  
-   Nestandardní přetypování vracející l-hodnoty. Příklad:  
  
    ```  
    char *p;  
    (( int * ) p )++;  
    ```  
  
    > [!NOTE]
    >  Toto rozšíření je k dispozici pouze v jazyce C. V kódu jazyka C++ lze použít následující formy standardu ANSI C ke změně ukazatele, pokud je to ukazatel na jiný typ.  
  
     Aby předchozí příklad vyhověl standardu ANSI C, měl by být přepsán následujícím způsobem.  
  
    ```  
    p = ( char * )(( int * )p + 1 );  
    ```  
  
-   Přetypování ukazatele na funkci na ukazatele na data, která nejsou ve standardu ANSI. Příklad:  
  
    ```  
    int ( * pfunc ) ();   
    int *pdata;  
    pdata = ( int * ) pfunc;  
    ```  
  
     Chcete-li provést stejné přetypování a zároveň zachovat kompatibilitu se standardem ANSI, lze ukazatele na funkci přetypovat na typ `uintptr_t` před tím, než jej přetypujete na ukazatel na data:  
  
    ```  
    pdata = ( int * ) (uintptr_t) pfunc;  
    ```  
  
## <a name="variable-length-argument-lists"></a>Seznamy argumentů s proměnnou délkou  
 Kompilátor jazyka C i C++ podporuje deklarátor funkce, který určuje proměnný počet argumentů následovaný definicí funkce, která místo toho poskytuje typ:  
  
```  
void myfunc( int x, ... );  
void myfunc( int x, char * c )  
{ }  
```  
  
## <a name="single-line-comments"></a>Jednořádkové komentáře  
 Kompilátor jazyka C podporuje jednořádkové komentáře, které lze vytvořit pomocí dvou znaků zpětného lomítka (//):  
  
```  
// This is a single-line comment.  
```  
  
## <a name="scope"></a>Rozsah  
 Kompilátor jazyka C podporuje následující funkce vztahující se k rozsahu.  
  
-   Redefinice externích položek jako statických:  
  
    ```  
    extern int clip();  
    static int clip()  
    {}  
    ```  
  
-   Použití neškodné redefinice typedef v rámci stejného rozsahu:  
  
    ```  
    typedef int INT;  
    typedef int INT;  
    ```  
  
-   Deklarátory funkce mají rozsah souboru:  
  
    ```  
    void func1()  
    {  
        extern int func2( double );  
    }  
    int main( void )  
    {  
        func2( 4 );    //  /Ze passes 4 as type double  
    }                  //  /Za passes 4 as type int  
    ```  
  
-   Použití proměnných v rozsahu bloku, které jsou inicializovány pomocí nekonstantních výrazů:  
  
    ```  
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
  
-   Smíšené znakové a řetězcové konstanty v inicializátoru:  
  
    ```  
    char arr[5] = {'a', 'b', "cde"};  
    ```  
  
-   Bit pole, které mají základní typy jiné než **nepodepsané int** nebo **podepsané int**.  
  
-   Deklarátory, které nemají typ:  
  
    ```  
    x;  
    int main( void )  
    {  
        x = 1;  
    }  
    ```  
  
-   Pole bez velikosti jako poslední pole ve strukturách a sjednoceních:  
  
    ```  
    struct zero  
    {  
        char *c;  
        int zarray[];  
    };  
    ```  
  
-   Nepojmenované struktury (anonymní):  
  
    ```  
    struct  
    {  
        int i;  
        char *s;  
    };  
    ```  
  
-   Nepojmenovaná sjednocení (anonymní):  
  
    ```  
    union  
    {  
        int i;  
        float fl;  
    };  
    ```  
  
-   Nepojmenované členy:  
  
    ```  
    struct s  
    {  
       unsigned int flag : 1;  
       unsigned int : 31;  
    }  
    ```  
  
## <a name="intrinsic-floating-point-functions"></a>Vnitřní funkce s plovoucí desetinnou čárkou  
 Kompilátor C++ i kompilátor jazyka C podporují vložené generování **x86 konkrétní >** z `atan`, `atan2`, `cos`, `exp`, `log`, `log10`, `sin`, `sqrt`, a `tan` funkce **END x86 konkrétní** při **/Oi** je zadán. Pokud jsou tyto vnitřní objekty použity, kompilátor jazyka C přijde o shodu se standardem ANSI, protože nenastavují proměnnou `errno`.  
  
## <a name="passing-a-non-const-pointer-parameter-to-a-function-that-expects-a-reference-to-a-const-pointer-parameter"></a>Předání nekonstantního ukazatele jako parametru funkci, která očekává odkaz na parametr konstantního ukazatele  
 Toto je rozšíření jazyka C++. Tento kód bude kompilovat s **/Ze**:  
  
```  
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
  
## <a name="iso646h-not-enabled"></a>Standard ISO646.H není povolen.  
 V části **/Ze**, je nutné zahrnout iso646.h – Pokud chcete používat textové formy následující operátory:  
  
-   && (and)  
  
-   &= (and_eq)  
  
-   & (bitand)  
  
-   &#124;(bitor)  
  
-   ~ (compl)  
  
-   ! (not)  
  
-   != (not_eq)  
  
-   &#124;&#124;(nebo)  
  
-   &#124;= (or_eq –)  
  
-   ^ (xor)  
  
-   ^= (xor_eq)  
  
## <a name="address-of-string-literal-has-type-const-char--not-const-char--"></a>Adresa textového literálu má typ const char [], nikoli typ const char (*) []  
 Následující příklad výstup char const (\*) [4] v části **/Za**, ale char const [4] v části **/Ze**.  
  
```  
#include <stdio.h>  
#include <typeinfo>  
  
int main()  
{  
    printf_s("%s\n", typeid(&"abc").name());  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [/ Za, /Ze (zakázat jazyková rozšíření)](../../build/reference/za-ze-disable-language-extensions.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)