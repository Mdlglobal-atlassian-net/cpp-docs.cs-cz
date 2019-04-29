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
ms.openlocfilehash: 55cf598877c2447e0f80e783b53b290699042b8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400588"
---
# <a name="inline-functions-c"></a>Vložené funkce (C++)

Funkce definovaná v těle deklarace třídy je vloženou funkcí.

## <a name="example"></a>Příklad

V následující deklaraci třídy je konstruktor `Account` vloženou funkcí. Členské funkce `GetBalance`, `Deposit`, a `Withdraw` nejsou zadány jako **vložené** , ale je možné implementovat jako vložené funkce.

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
>  V deklaraci třídy byly funkce deklarovány bez **vložené** – klíčové slovo. **Vložené** – klíčové slovo se dá nastavit v deklaraci třídy, výsledek je stejný.

Jedna vložená členská funkce musí být deklarována ve všech jednotkách kompilace stejně. Vlivem tohoto omezení se vložené funkce chovají stejně, jako by šlo o funkce s instancí. Kromě toho musí být vložená funkce definována právě jednou.

Členské funkce třídy výchozí vnější propojení, pokud neobsahuje definici pro tuto funkci **vložené** specifikátor. Předchozí příklad ukazuje, že tyto funkce nemusí být explicitně deklarovány pomocí **vložené** specifikátor; pomocí **vložené** ve funkci definice vede k jejímu vloženou funkci. Je však neplatný zavolání funkce jako **vložené** po volání této funkce.

## <a name="inline-inline-and-forceinline"></a>Inline, __inline, a \__forceinline

**Vložené** a **__inline** specifikátory pokyn kompilátoru k vložení kopie těla funkce na každé místo, tato funkce volána.

Vložení (též vložené rozšíření nebo vkládání) nastane pouze v případě, že se analýza nákladů a přínosů kompilátoru jeví jako zisková. Vložené rozšíření řeší nároky volání funkce případných nákladů obsáhlejšího kódu.

**__Forceinline** – klíčové slovo přepíše analýzy nákladů a přínosů a místo toho spoléhá na posouzení programátora. Opatrní při použití **__forceinline**. Nerozlišení **__forceinline** může mít za následek kódu s pouze minimálním ziskem výkonu zisky, nebo v některých případech i ztráty výkonu (v důsledku zvýšeného stránkování obsáhlejšího spustitelného souboru, například).

Pomocí vložených funkcí lze program urychlit, protože tyto funkce odstraňují režii spojenou s voláním funkcí. Vložené rozšířené funkce jsou předmětem optimalizace kódu nedostupným pro běžné funkce.

Kompilátor zpracovává možnosti vloženého rozšíření a klíčová slova jako návrhy. Není zaručeno, že budou funkce vloženy. Nelze vynutit na kompilátoru k vložení funkce, i s **__forceinline** – klíčové slovo. Při kompilaci s **/CLR**, kompilátor nevloží funkci Pokud nejsou u funkce použity atributy zabezpečení.

**Vložené** – klíčové slovo je k dispozici pouze v jazyce C++. **__Inline** a **__forceinline** klíčová slova jsou k dispozici v obou C a C++. Z důvodu kompatibility s předchozími verzemi **_inline** a **_forceinline** jsou synonyma pro **__inline**, a **__forceinline** Pokud – možnost kompilátoru [/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) určena.

**Vložené** – klíčové slovo sděluje kompilátoru, že je upřednostněno vložené rozšíření upřednostňované. Kompilátor však může vytvořit samostatnou instanci funkce (vytvoření instance) a může vytvořit standardní spojení volání namísto vložení kódu. Jsou dva případy, kdy tato situace může nastat:

- Rekurzivní funkce.

- Funkce, které jsou v jednotce překladu označovány prostřednictvím ukazatele jinam.

Tyto důvody mohou ovlivňovat vkládání, *jako mohou ostatní*, na základě vlastního uvážení kompilátoru neměli spoléhat na **vložené** specifikátor funkce se nedá vložit.

Stejně jako u běžných funkcí neexistuje pořadí vyhodnocování argumentů vložené funkce. Ve skutečnosti může být odlišné od pořadí, ve kterém jsou vyhodnoceny argumenty při předávání pomocí protokolu volání normální funkce.

[/Ob](../build/reference/ob-inline-function-expansion.md) Optimalizace – možnost kompilátoru vám pomůže určit, zda skutečně dojde k rozbalení vložených funkcí.

[/ LTCG](../build/reference/ltcg-link-time-code-generation.md) provede bez ohledu na to, zda tak bylo požadováno ve zdrojovém kódu vkládání napříč moduly.

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

Členské funkce třídy lze deklarovat vložené pomocí **vložené** – klíčové slovo nebo umístěním definice funkce v rámci definice třídy.

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

### <a name="microsoft-specific"></a>Specifické pro Microsoft

**__Inline** – klíčové slovo je ekvivalentní **vložené**.

I přes **__forceinline**, kompilátor nemůže provést vložení kódu za všech okolností. Kompilátor nemůže provést vložení funkce, pokud:

- Funkce nebo její volající je zkompilován pomocí příkazu /Ob0 (výchozí možnost sestavení pro ladění).

- Funkce a volající používají různé druhy zpracování výjimek (zpracování výjimek jazyka C++ ve funkci, strukturované zpracování výjimek u volajícího).

- Funkce má proměnný seznam argumentů.

- Funkce používá vložené sestavení, dokud není zkompilována pomocí /Og, /Ox, /O1 nebo /O2.

- Funkce je rekurzivní a není doplněna direktivou **#pragma inline_recursion(on)**. Pomocí direktivy pragma jsou rekurzivní funkce vloženy do výchozí hloubky 16 volání. Chcete-li snížit hloubku vkládání, použijte [inline_depth](../preprocessor/inline-depth.md) direktivy pragma.

- Funkce je virtuální a je volána virtuálně. Přímá volání virtuálních funkcí mohou být vložená.

- Program přebere adresu funkce a volání se provádí prostřednictvím ukazatele na funkci. Přímá volání funkcí, jejichž adresa byla odebrána, mohou být vložená.

- Funkce je také označena [naked](../cpp/naked-cpp.md) [__declspec](../cpp/declspec.md) modifikátor.

Pokud kompilátor nemůže provést vložení deklarované funkce pomocí **__forceinline**, vygeneruje upozornění úrovně 1, když:

- Funkce je zkompilován s použitím /Od nebo příkazu/ob0. Žádné vložené v těchto případech se očekává.

- Funkce externě, definovaná v zahrnuté knihovny nebo jiné jednotce překladu, nebo je volání virtuální cíl nebo cíl nepřímé volání. Kompilátor nemůže identifikovat-vložit kód, který nejde najít v aktuální překladové jednotce.

Rekurzivní funkce mohou být nahrazeny vložením do hloubky určeného direktivou [inline_depth](../preprocessor/inline-depth.md) – Direktiva pragma, až do maximálního počtu 16 volání. Následně jsou hluboké rekurzivní funkce považovány za volání instance funkce.  Hloubka, do které jsou pomocí heuristiky vložení rekurzivní funkce prozkoumány, nesmí překročit 16. [Inline_recursion](../preprocessor/inline-recursion.md) – Direktiva pragma řídí vložené rozšíření aktuálně rozšiřované funkce. Zobrazit [rozbalení vložené funkce](../build/reference/ob-inline-function-expansion.md) (/ Ob) – možnost kompilátoru související informace.

**Specifické pro END Microsoft**

Další informace o používání **vložené** specifikátor, naleznete v tématu:

- [Vložené členské funkce třídy](../cpp/inline-functions-cpp.md)

- [Definování vložených funkcí jazyka C++ příkazy dllexport a dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>Kdy použít vložené funkce

Vložené funkce je nejvhodnější používat pro malé funkce, například přístup k soukromým datovým členům. Hlavním účelem těchto „přístupových“ funkcí s jedním nebo dvěma řádky je vrátit stavové informace o objektech. Krátké funkce jsou citlivé na režii spojenou s voláním funkcí. Delší funkce stráví sekvencemi volání a vrácení poměrově méně času a jejich vkládání přináší menší užitek.

A `Point` třídy lze definovat takto:

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

Za předpokladu, že souřadnic manipulace se poměrně běžnou operací v klientovi takové třídy, zadání daných dvou přístupových funkcí (`x` a `y` v předchozím příkladu) jako **vložené** obvykle ukládá Režijní náklady na:

- Volání funkcí (včetně předávání parametrů a ukládání adresy objektu do zásobníku)

- Zachování rámce zásobníku volajícího

- Nové nastavení rámce zásobníku

- Komunikace návratové hodnoty

- Obnovení původního rámce zásobníku

- Vrátí

## <a name="inline-functions-vs-macros"></a>Vložené funkce versus makra

Přestože jsou vložené funkce podobné makrům (protože je kód funkce rozbalen v místě volání v době kompilace), vložené funkce jsou analyzovány pomocí kompilátoru, kdežto makra jsou analyzována pomocí preprocesoru. V důsledku toho existuje několik důležitých rozdílů:

- Vložené funkce následují všechny protokoly bezpečnosti typů vynucené normálními funkcemi.

- Vložené funkce jsou zadány pomocí stejné syntaxe jako ostatní funkce s tím rozdílem, že patří mezi ně **vložené** – klíčové slovo v deklaraci funkce.

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

Záměr výrazu `toupper(getc(stdin))` je, že znak měl být přečten z konzolového zařízení (`stdin`) a v případě potřeby převeden na velká písmena.

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