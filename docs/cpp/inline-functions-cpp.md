---
title: Vložené funkce (C++)
ms.date: 10/09/2018
f1_keywords:
- __forceinline_cpp
- __inline_cpp
- inline_cpp
- __inline
- _inline
- __forceinline
- _forceinline
helpviewer_keywords:
- inline functions [C++], class members
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
ms.openlocfilehash: efaaacc46f63ac1a702ab2110d35fe80727ead1d
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857512"
---
# <a name="inline-functions-c"></a>Vložené funkce (C++)

Funkce definovaná v těle deklarace třídy je vloženou funkcí.

## <a name="example"></a>Příklad

V následující deklaraci třídy je konstruktor `Account` vloženou funkcí. Členské funkce `GetBalance`, `Deposit`a `Withdraw` nejsou zadány jako **inline** , ale lze je implementovat jako vložené funkce.

```cpp
// Inline_Member_Functions.cpp
class Account
{
public:
    Account(double initial_balance) { balance = initial_balance; }
    double GetBalance();
    double Deposit( double Amount );
    double Withdraw( double Amount );
private:
    double balance;
};

inline double Account::GetBalance()
{
    return balance;
}

inline double Account::Deposit( double Amount )
{
    return ( balance += Amount );
}

inline double Account::Withdraw( double Amount )
{
    return ( balance -= Amount );
}
int main()
{
}
```

> [!NOTE]
>  V deklaraci třídy byly funkce deklarovány bez klíčového slova **inline** . Klíčové slovo **inline** lze zadat v deklaraci třídy; výsledek je stejný.

Jedna vložená členská funkce musí být deklarována ve všech jednotkách kompilace stejně. Vlivem tohoto omezení se vložené funkce chovají stejně, jako by šlo o funkce s instancí. Kromě toho musí být vložená funkce definována právě jednou.

Členská funkce třídy je výchozím nastavením vnějšího propojení, pokud definice této funkce neobsahuje **vložený** specifikátor. Předchozí příklad ukazuje, že tyto funkce nemusí být explicitně deklarovány pomocí **vloženého** specifikátoru; použití funkce **inline** v definici funkce způsobí, že se jedná o vloženou funkci. Není však povoleno znovu deklarovat funkci jako **vloženou** po volání této funkce.

## <a name="inline-__inline-and-__forceinline"></a>Vložené, __inline a \__forceinline

**Vložené** a **__inline** specifikátory instruují kompilátor k vložení kopie těla funkce na každé místo, kde je funkce volána.

Vložení (též vložené rozšíření nebo vkládání) nastane pouze v případě, že se analýza nákladů a přínosů kompilátoru jeví jako zisková. Vložené rozšíření řeší nároky volání funkce případných nákladů obsáhlejšího kódu.

Klíčové slovo **__forceinline** Přepisuje analýzu nákladů a výhod a spoléhá na rozhodnutí programátora. Při použití **__forceinline**buďte opatrní. Nerozlišené použití **__forceinline** může mít za následek větší kód s nárůstem výkonu, nebo v některých případech i ztráty výkonu (například kvůli většímu stránkování většího spustitelného souboru).

Pomocí vložených funkcí lze program urychlit, protože tyto funkce odstraňují režii spojenou s voláním funkcí. Vložené rozšířené funkce jsou předmětem optimalizace kódu nedostupným pro běžné funkce.

Kompilátor zpracovává možnosti vloženého rozšíření a klíčová slova jako návrhy. Není zaručeno, že budou funkce vloženy. Nelze vynutit, aby kompilátor mohl vložit konkrétní funkci, a to ani s klíčovým slovem **__forceinline** . Při kompilaci s možností **/CLR**kompilátor nevloží funkci, pokud jsou na funkci aplikovány atributy zabezpečení.

Klíčové slovo **inline** je k dispozici pouze v C++. Klíčová slova **__inline** a **__forceinline** jsou k dispozici jak C++v jazyce C, tak i v. Z důvodu kompatibility s předchozími verzemi jsou **_inline** a **_forceinline** synonyma pro **__inline**a **__forceinline** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

Klíčové slovo **inline** instruuje kompilátor, že je upřednostňováno vložené rozšíření. Kompilátor však může vytvořit samostatnou instanci funkce (vytvoření instance) a může vytvořit standardní spojení volání namísto vložení kódu. Jsou dva případy, kdy tato situace může nastat:

- Rekurzivní funkce.

- Funkce, které jsou v jednotce překladu označovány prostřednictvím ukazatele jinam.

Tyto důvody mohou být v konfliktu s vkládáním, *jako by mohly být jiné*, na uvážení kompilátoru. neměli byste záviset na vloženém specifikátoru a způsobit tak, že funkce bude **vložena** .

Stejně jako u běžných funkcí neexistuje pořadí vyhodnocování argumentů vložené funkce. Ve skutečnosti může být odlišné od pořadí, ve kterém jsou vyhodnoceny argumenty při předávání pomocí protokolu volání normální funkce.

Možnost optimalizace kompilátoru [/ob](../build/reference/ob-inline-function-expansion.md) pomáhá určit, zda skutečně dojde k rozšíření vložené funkce.

[/LTCG](../build/reference/ltcg-link-time-code-generation.md) provádí vkládání mezi moduly bez ohledu na to, zda bylo vyžádáno ve zdrojovém kódu.

### <a name="example-1"></a>Příklad 1

```cpp
// inline_keyword1.cpp
// compile with: /c
inline int max( int a , int b ) {
   if( a > b )
      return a;
   return b;
}
```

Členské funkce třídy mohou být deklarovány jako vložené buď pomocí klíčového slova **inline** , nebo umístěním definice funkce v rámci definice třídy.

### <a name="example-2"></a>Příklad 2

```cpp
// inline_keyword2.cpp
// compile with: /EHsc /c
#include <iostream>
using namespace std;

class MyClass {
public:
   void print() { cout << i << ' '; }   // Implicitly inline
private:
   int i;
};
```

**Specifické pro společnost Microsoft**

Klíčové slovo **__inline** je ekvivalentní **vloženému**.

I když **__forceinline**, kompilátor nemůže vložit kód za všech okolností. Kompilátor nemůže provést vložení funkce, pokud:

- Funkce nebo její volající je zkompilován pomocí příkazu /Ob0 (výchozí možnost sestavení pro ladění).

- Funkce a volající používají různé druhy zpracování výjimek (zpracování výjimek jazyka C++ ve funkci, strukturované zpracování výjimek u volajícího).

- Funkce má proměnný seznam argumentů.

- Funkce používá vložené sestavení, dokud není zkompilována pomocí /Og, /Ox, /O1 nebo /O2.

- Funkce je rekurzivní a není doprovázena **#pragma inline_recursion (on)** . Pomocí direktivy pragma jsou rekurzivní funkce vloženy do výchozí hloubky 16 volání. Chcete-li zmenšit hloubku vkládání, použijte direktivu pragma [inline_depth](../preprocessor/inline-depth.md) .

- Funkce je virtuální a je volána virtuálně. Přímá volání virtuálních funkcí mohou být vložená.

- Program přebere adresu funkce a volání se provádí prostřednictvím ukazatele na funkci. Přímá volání funkcí, jejichž adresa byla odebrána, mohou být vložená.

- Funkce je také označena s modifikátorem [holého](../cpp/naked-cpp.md) [__declspec](../cpp/declspec.md) .

Pokud kompilátor nemůže vložit funkci deklarovanou pomocí **__forceinline**, vygeneruje upozornění úrovně 1, s výjimkou případů, kdy:

- Funkce je kompilována pomocí/od nebo/Ob0. V těchto případech se neočekává žádné vkládání.

- Funkce je definována externě, v zahrnuté knihovně nebo jiné jednotce překladu, nebo je cílem virtuálního volání nebo nepřímým cílem volání. Kompilátor nemůže identifikovat nevložený kód, který nemůže najít v aktuální jednotce překladu.

Rekurzivní funkce mohou být nahrazeny vložením do hloubky určené direktivou [inline_depth](../preprocessor/inline-depth.md) pragma až do maximálního počtu 16 volání. Následně jsou hluboké rekurzivní funkce považovány za volání instance funkce.  Hloubka, do které jsou pomocí heuristiky vložení rekurzivní funkce prozkoumány, nesmí překročit 16. Direktiva pragma [inline_recursion](../preprocessor/inline-recursion.md) řídí vložené rozšíření funkce aktuálně pod rozšířením. Další informace najdete v tématu [rozšíření vložené funkce](../build/reference/ob-inline-function-expansion.md) (/ob) pro související informace.

**Specifické pro konec Microsoftu**

Další informace o použití **vloženého** specifikátoru naleznete zde:

- [Vložené členské funkce třídy](../cpp/inline-functions-cpp.md)

- [Definování vložených funkcí jazyka C++ příkazy dllexport a dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>Kdy použít vložené funkce

Vložené funkce je nejvhodnější používat pro malé funkce, například přístup k soukromým datovým členům. Hlavním účelem těchto „přístupových“ funkcí s jedním nebo dvěma řádky je vrátit stavové informace o objektech. Krátké funkce jsou citlivé na režii spojenou s voláním funkcí. Delší funkce stráví sekvencemi volání a vrácení poměrově méně času a jejich vkládání přináší menší užitek.

Třídu `Point` lze definovat následujícím způsobem:

```cpp
// when_to_use_inline_functions.cpp
class Point
{
public:
    // Define "accessor" functions as
    //  reference types.
    unsigned& x();
    unsigned& y();
private:
    unsigned _x;
    unsigned _y;
};

inline unsigned& Point::x()
{
    return _x;
}
inline unsigned& Point::y()
{
    return _y;
}
int main()
{
}
```

Za předpokladu, že manipulace se souřadnicemi jsou relativně běžné operace v klientovi takové třídy, určením dvou přístupových funkcí (`x` a `y` v předchozím příkladu), jak je **vloženo** obvykle ukládá režii na:

- Volání funkcí (včetně předávání parametrů a ukládání adresy objektu do zásobníku)

- Zachování rámce zásobníku volajícího

- Nové nastavení rámce zásobníku

- Komunikace návratové hodnoty

- Obnovení původního rámce zásobníku

- Výsledek

## <a name="inline-functions-vs-macros"></a>Vložené funkce vs. makra

Přestože jsou vložené funkce podobné makrům (protože je kód funkce rozbalen v místě volání v době kompilace), vložené funkce jsou analyzovány pomocí kompilátoru, kdežto makra jsou analyzována pomocí preprocesoru. V důsledku toho existuje několik důležitých rozdílů:

- Vložené funkce následují všechny protokoly bezpečnosti typů vynucené normálními funkcemi.

- Vložené funkce jsou zadány pomocí stejné syntaxe jako jakákoli jiná funkce s tím rozdílem, že obsahují klíčové slovo **inline** v deklaraci funkce.

- Výrazy předané jako argumenty vložených funkcí jsou vyhodnoceny jednou. V některých případech mohou být výrazy, které jsou předány jako argumenty makrům, vyhodnoceny více než jednou.

Následující příklad ukazuje makro, které převádí malá písmena na velká písmena:

```cpp
// inline_functions_macro.c
#include <stdio.h>
#include <conio.h>

#define toupper(a) ((a) >= 'a' && ((a) <= 'z') ? ((a)-('a'-'A')):(a))

int main() {
   char ch;
   printf_s("Enter a character: ");
   ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
//  Sample Input:  xyz
// Sample Output:  Z
```

Záměrem výrazu `toupper(getc(stdin))` je, že by měl být znak čten ze zařízení konzoly (`stdin`) a v případě potřeby převeden na velká písmena.

Z důvodu implementace tohoto makra je funkce `getc` provedena jednou pro určení, zda je znak větší než nebo roven znaku „a“, a poté jednou pro rozhodnutí, zda je menší než nebo roven znaku „z“. Pokud je v tomto rozsahu, je funkce `getc` zavolána znovu pro převedení znaku na velká písmena. To znamená, že program čeká na dva nebo tři znaky, když v ideálním případě by měl čekat pouze na jeden znak.

Vložené funkce výše popsaný problém napravují:

```cpp
// inline_functions_inline.cpp
#include <stdio.h>
#include <conio.h>

inline char toupper( char a ) {
   return ((a >= 'a' && a <= 'z') ? a-('a'-'A') : a );
}

int main() {
   printf_s("Enter a character: ");
   char ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
```

```Output
Sample Input: a
Sample Output: A
```

## <a name="see-also"></a>Viz také:

[noinline](../cpp/noinline.md)<br/>
[auto_inline](../preprocessor/auto-inline.md)