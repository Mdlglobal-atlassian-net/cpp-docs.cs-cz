---
title: Vložené funkce (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __forceinline_cpp
- __inline_cpp
- inline_cpp
dev_langs:
- C++
helpviewer_keywords:
- inline functions [C++], class members
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6661996669e454e655d0149f1dbb1df505116469
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="inline-functions-c"></a>Vložené funkce (C++)
Funkce definovaná v těle deklarace třídy je vloženou funkcí.  
  
## <a name="example"></a>Příklad  
 V následující deklaraci třídy je konstruktor `Account` vloženou funkcí. Členské funkce `GetBalance`, `Deposit`, a `Withdraw` nejsou zadány jako **vložené** , ale může být implementováno jako vložené funkce.  
  
```  
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
>  V deklaraci třídy funkce bylo deklarováno bez **vložené** – klíčové slovo. **Vložené** – klíčové slovo lze zadat v deklaraci třídy; výsledek je stejný.  
  
 Jedna vložená členská funkce musí být deklarována ve všech jednotkách kompilace stejně. Vlivem tohoto omezení se vložené funkce chovají stejně, jako by šlo o funkce s instancí. Kromě toho musí být vložená funkce definována právě jednou.  
  
 Členské funkce tříd výchozí externí propojení, pokud obsahuje definici pro tuto funkci **vložené** specifikátor. Předchozí příklad ukazuje, že tyto funkce nemusí být explicitně deklarovat s **vložené** specifikátor; pomocí **vložené** ve funkci definice způsobí, že bude vložená funkce. Je však neplatný redeclare funkce jako **vložené** po volání této funkce.  
  
## <a name="inline-inline-and-forceinline"></a>Vložené, __inline, a \__forceinline  
 Specifikátory `inline` a `__inline` dávají pokyn kompilátoru k vložení kopie těla funkce na každé místo, odkud je funkce volána.  
  
 Vložení (též vložené rozšíření nebo vkládání) nastane pouze v případě, že se analýza nákladů a přínosů kompilátoru jeví jako zisková. Vložené rozšíření řeší nároky volání funkce případných nákladů obsáhlejšího kódu.  
  
 Klíčové slovo `__forceinline` přepíše analýzy nákladů a přínosů a místo toho spoléhá na posouzení programátorem. Při používání klíčového slova `__forceinline` je třeba postupovat opatrně. Nerozlišení `__forceinline` může vést k obsáhlejšímu kódu s pouze minimálním ziskem výkonu nebo dokonce v některých případech i ke ztrátě výkonu (například v důsledku zvýšeného stránkování obsáhlejšího spustitelného souboru).  
  
 Pomocí vložených funkcí lze program urychlit, protože tyto funkce odstraňují režii spojenou s voláním funkcí. Vložené rozšířené funkce jsou předmětem optimalizace kódu nedostupným pro běžné funkce.  
  
 Kompilátor zpracovává možnosti vloženého rozšíření a klíčová slova jako návrhy. Není zaručeno, že budou funkce vloženy. Nelze provést vynucení vložení funkce pomocí kompilátoru ani při použití klíčového slova `__forceinline`. Při kompilaci s **/CLR**, kompilátor není vložené funkce Pokud existují zabezpečení atributy použité na funkce.  
  
 **Vložené** – klíčové slovo je k dispozici pouze v jazyce C++. Klíčová slova `__inline` a `__forceinline` jsou k dispozici v jazycích C a C++. Pro kompatibilitu s předchozími verzemi **_inline** se jedná o synonymum `__inline`.  
  
 **Vložené** – klíčové slovo říká kompilátoru, že je upřednostňováno vložené rozšíření. Kompilátor však může vytvořit samostatnou instanci funkce (vytvoření instance) a může vytvořit standardní spojení volání namísto vložení kódu. Jsou dva případy, kdy tato situace může nastat:  
  
-   Rekurzivní funkce.  
  
-   Funkce, které jsou v jednotce překladu označovány prostřednictvím ukazatele jinam.  
  
 Z těchto důvodů může narušovat vložené, *jako ostatní může*, uvážení kompilátoru; nesmí závisí na **vložené** specifikátor způsobí funkce, která má být vložená.  
  
 Stejně jako u běžných funkcí neexistuje pořadí vyhodnocování argumentů vložené funkce. Ve skutečnosti může být odlišné od pořadí, ve kterém jsou vyhodnoceny argumenty při předávání pomocí protokolu volání normální funkce.  
  
 [/Ob](../build/reference/ob-inline-function-expansion.md) Optimalizace – možnost kompilátoru vám pomůže určit, zda má být vložené funkce rozšíření ve skutečnosti provedena.  
  
 [/ LTCG](../build/reference/ltcg-link-time-code-generation.md) provede cross-module vložené bez ohledu na to, zda byla vyžádána ve zdrojovém kódu.  
  
### <a name="example-1"></a>Příklad 1  
  
```  
// inline_keyword1.cpp  
// compile with: /c  
inline int max( int a , int b ) {  
   if( a > b )   
      return a;  
   return b;  
}  
```  
  
 Funkce člena třídy a lze deklarovat vložené buď pomocí **vložené** – klíčové slovo nebo tím, že v definici funkce v definici třídy.  
  
### <a name="example-2"></a>Příklad 2  
  
```  
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
 `__inline` – Klíčové slovo je ekvivalentní **vložené**.  
  
 Dokonce ani s pomocí příkazu `__forceinline` nemůže kompilátor provést vložení kódu za všech okolností. Kompilátor nemůže provést vložení funkce, pokud:  
  
-   Funkce nebo její volající je zkompilován pomocí příkazu /Ob0 (výchozí možnost sestavení pro ladění).  
  
-   Funkce a volající používají různé druhy zpracování výjimek (zpracování výjimek jazyka C++ ve funkci, strukturované zpracování výjimek u volajícího).  
  
-   Funkce má proměnný seznam argumentů.  
  
-   Funkce používá vložené sestavení, dokud není zkompilována pomocí /Og, /Ox, /O1 nebo /O2.  
  
-   Funkce je rekurzivní a není společně **#pragma inline_recursion(on)**. Pomocí direktivy pragma jsou rekurzivní funkce vloženy do výchozí hloubky 16 volání. Chcete-li snížit vložené hloubku, použijte [inline_depth –](../preprocessor/inline-depth.md) – Direktiva pragma.  
  
-   Funkce je virtuální a je volána virtuálně. Přímá volání virtuálních funkcí mohou být vložená.  
  
-   Program přebere adresu funkce a volání se provádí prostřednictvím ukazatele na funkci. Přímá volání funkcí, jejichž adresa byla odebrána, mohou být vložená.  
  
-   Funkce je také označené [holé](../cpp/naked-cpp.md) [__declspec](../cpp/declspec.md) modifikátor.  
  
 Pokud kompilátor nelze vložené funkce deklarovat s `__forceinline`, vygeneruje upozornění úrovně 1, s výjimkou případů, kdy:
  
-   Funkce je zkompilovat pomocí /Od nebo /Ob0. Ne vložené v těchto případech se očekává.     
  
-   Funkce je součástí knihovny nebo jiné jednotce překlad externě, definované nebo je cíl virtuální volání nebo nepřímé volání cíl. Kompilátor nemůže identifikovat-vložená kód, který nebyl nalezen v aktuální jednotce překlad.  
  
 Rekurzivní funkce mohou být nahrazovanou vložené do hloubky určeného [inline_depth –](../preprocessor/inline-depth.md) – Direktiva pragma maximálně 16 volání. Následně jsou hluboké rekurzivní funkce považovány za volání instance funkce.  Hloubka, do které jsou pomocí heuristiky vložení rekurzivní funkce prozkoumány, nesmí překročit 16. [Inline_recursion –](../preprocessor/inline-recursion.md) – Direktiva pragma ovládací prvky vložené rozšíření funkce aktuálně pod rozšíření. Najdete v článku [vložená funkce rozšíření](../build/reference/ob-inline-function-expansion.md) (nebo Ob) – možnost kompilátoru související informace.  
  
**Konkrétní Microsoft END**  
 Další informace o používání **vložené** specifikátor, najdete v části:  
  
-   [Vložené funkce člena třídy](../cpp/inline-functions-cpp.md)  
  
-   [Definování vložených funkcí jazyka C++ příkazy dllexport a dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)  
  
## <a name="when-to-use-inline-functions"></a>Kdy použít vložené funkce  
 Vložené funkce je nejvhodnější používat pro malé funkce, například přístup k soukromým datovým členům. Hlavním účelem těchto „přístupových“ funkcí s jedním nebo dvěma řádky je vrátit stavové informace o objektech. Krátké funkce jsou citlivé na režii spojenou s voláním funkcí. Delší funkce stráví sekvencemi volání a vrácení poměrově méně času a jejich vkládání přináší menší užitek.  
  
 A `Point` třídy lze definovat následujícím způsobem:  
  
```  
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
  
 Za předpokladu, že souřadnic manipulaci je poměrně běžné operace v klientovi této třídy, zadání dvě funkce přístupového objektu (`x` a `y` v předchozím příkladu) jako **vložené** obvykle ukládá Režijní náklady na:  
  
-   Volání funkcí (včetně předávání parametrů a ukládání adresy objektu do zásobníku)  
  
-   Zachování rámce zásobníku volajícího  
  
-   Nové nastavení rámce zásobníku  
  
-   Komunikace návratové hodnoty  
  
-   Obnovení původního rámce zásobníku  
  
-   Vrátí  
  
## <a name="inline-functions-vs-macros"></a>Vložené funkce oproti makrům  
 Přestože jsou vložené funkce podobné makrům (protože je kód funkce rozbalen v místě volání v době kompilace), vložené funkce jsou analyzovány pomocí kompilátoru, kdežto makra jsou analyzována pomocí preprocesoru. V důsledku toho existuje několik důležitých rozdílů:  
  
-   Vložené funkce následují všechny protokoly bezpečnosti typů vynucené normálními funkcemi.  
  
-   Vložené funkce jsou určeny pomocí stejnou syntaxi jako jakékoli jiné funkce s tím rozdílem, že obsahují **vložené** – klíčové slovo v deklaraci funkce.  
  
-   Výrazy předané jako argumenty vložených funkcí jsou vyhodnoceny jednou. V některých případech mohou být výrazy, které jsou předány jako argumenty makrům, vyhodnoceny více než jednou.  
  
 Následující příklad ukazuje makro, které převádí malá písmena na velká písmena:  
  
```  
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
  
 Záměr výrazu `toupper(getc(stdin))` je, že byste si měli přečíst znak z konzoly zařízení (`stdin`) a v případě potřeby převeden na velká písmena.  
  
 Z důvodu implementace tohoto makra je funkce `getc` provedena jednou pro určení, zda je znak větší než nebo roven znaku „a“, a poté jednou pro rozhodnutí, zda je menší než nebo roven znaku „z“. Pokud je v tomto rozsahu, je funkce `getc` zavolána znovu pro převedení znaku na velká písmena. To znamená, že program čeká na dva nebo tři znaky, když v ideálním případě by měl čekat pouze na jeden znak.  
  
 Vložené funkce výše popsaný problém napravují:  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [noinline](../cpp/noinline.md)   
 [auto_inline](../preprocessor/auto-inline.md)