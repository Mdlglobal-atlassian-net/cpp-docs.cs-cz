---
title: Locale – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocale/std::locale
- xlocale/std::locale::category
- xlocale/std::locale::combine
- xlocale/std::locale::name
- xlocale/std::locale::classic
- xlocale/std::locale::global
- xlocale/std::locale::operator( )
- xlocale/std::locale::facet
- xlocale/std::locale::id
dev_langs:
- C++
helpviewer_keywords:
- std::locale [C++]
- std::locale [C++], category
- std::locale [C++], combine
- std::locale [C++], name
- std::locale [C++], classic
- std::locale [C++], global
- std::locale [C++], facet
- std::locale [C++], id
ms.assetid: 7dd6d271-472d-4750-8fb5-ea8f55fbef62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0a3f60a4cbcde76a681b33ed9201e81f313bac1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862095"
---
# <a name="locale-class"></a>locale – třída

Třída, která popisuje místní objekt, který zapouzdří informace specifické pro jazykovou verzi jako sadu omezujících vlastností, jež společně definují určité lokalizované prostředí.

## <a name="syntax"></a>Syntaxe

```cpp
class locale;
```

## <a name="remarks"></a>Poznámky

Omezující vlastnost je ukazatel na objekt třídy odvozené od třídy [omezující vlastnost](#facet_class) s veřejné objekt ve formátu:

```cpp
static locale::id id;
```

Můžete definovat neuzavřenou množinu těchto omezujících vlastností. Můžete také sestavit objekt národního prostředí, který určuje libovolný počet omezujících vlastností.

Předdefinované skupiny tyto omezující vlastnosti představují [kategorie národního prostředí](#category) tradičně spravuje standardní knihovny jazyka C: funkce `setlocale`.

Kategorie collate (LC_COLLATE) obsahuje omezující vlastnosti:

```cpp
collate<char>
collate<wchar_t>
```

Kategorie ctype (LC_CTYPE) obsahuje omezující vlastnosti:

```cpp
ctype<char>
ctype<wchar_t>
codecvt<char, char, mbstate_t>
codecvt<wchar_t, char, mbstate_t>
codecvt<char16_t, char, mbstate_t>
codecvt<char32_t, char, mbstate_t>
```

Kategorie monetary (LC_MONETARY) obsahuje omezující vlastnosti:

```cpp
moneypunct<char, false>
moneypunct<wchar_t, false>
moneypunct<char, true>
moneypunct<wchar_t, true>
money_get<char, istreambuf_iterator<char>>
money_get<wchar_t, istreambuf_iterator<wchar_t>>
money_put<char, ostreambuf_iterator<char>>
money_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

Kategorie numeric (LC_NUMERIC) obsahuje omezující vlastnosti:

```cpp
num_get<char, istreambuf_iterator<char>>
num_get<wchar_t, istreambuf_iterator<wchar_t>>
num_put<char, ostreambuf_iterator<char>>
num_put<wchar_t, ostreambuf_iterator<wchar_t>>
numpunct<char>
numpunct<wchar_t>
```

Kategorie time (LC_TIME) obsahuje omezující vlastnosti:

```cpp
time_get<char, istreambuf_iterator<char>>
time_get<wchar_t, istreambuf_iterator<wchar_t>>
time_put<char, ostreambuf_iterator<char>>
time_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

Kategorie messages (LC_MESSAGES) obsahuje omezující vlastnosti:

```cpp
messages<char>
messages<wchar_t>
```

(Poslední kategorie je vyžadována knihovnou Posix, ale nikoli standardní knihovnou jazyka C.)

Některé z těchto předdefinovaných omezujících vlastností jsou používány třídami iostreams k řízení převodu číselných hodnot z a na sekvence textu.

Název národního prostředí objekt národní prostředí – třída také ukládá jako objekt třídy [řetězec](../standard-library/string-typedefs.md#string). Pomocí názvu objektu neplatné národní prostředí vytvořit národního prostředí omezující vlastnost nebo objekt národního prostředí, vyvolá objekt třídy [runtime_error](../standard-library/runtime-error-class.md). Název uložené národního prostředí je `"*"` Pokud objekt národní prostředí nelze určité přesně na odpovídá C-style národní prostředí, reprezentovaný objektem. Jinak, můžete vytvořit odpovídající národního prostředí v rámci standardní knihovny jazyka C pro objekt národního prostředí `Loc`, voláním `setlocale`(LC_ALL `,` `Loc`. [název](#name)`().c_str()`).

V této implementaci můžete také volat statickou členskou funkci:

```cpp
static locale empty();
```

k vytvoření objektu národního prostředí, který nemá žádné omezující vlastnosti Je také transparentní národního prostředí; Pokud funkce šablon [has_facet](../standard-library/locale-functions.md#has_facet) a [use_facet](../standard-library/locale-functions.md#use_facet) nelze najít požadovaný omezující vlastnost v transparentní národním prostředí, se poraďte se nejprve globální národní prostředí a poté, pokud je transparentní, classic národní prostředí. Lze tedy psát:

```cpp
cout.imbue(locale::empty());
```

Následné vložení do [cout](../standard-library/iostream.md#cout) jsou zprostředkovaného podle aktuálního stavu globální národního prostředí. Lze dokonce psát:

```cpp
locale loc(locale::empty(),
    locale::classic(),
    locale::numeric);

cout.imbue(loc);
```

Pravidla pro následné vložení pro formátování čísel `cout` zůstat stejné jako národní prostředí C, to i v případě změny pravidel pro vkládání a peněžní částky poskytuje globální národní prostředí.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[Národní prostředí](#locale)|Vytvoří národní prostředí nebo kopii národního prostředí či kopii národního prostředí, kde byla omezující vlastnost nebo kategorie nahrazena omezující vlastností nebo kategorií z jiného národního prostředí.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[Kategorie](#category)|Typ integer, který poskytuje hodnoty bitové masky pro skupiny standardních omezujících vlastností.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[kombinování](#combine)|Vloží omezující vlastnost ze zadaného národního prostředí do cílového národního prostředí.|
|[Jméno](#name)|Vrátí název uloženého národního prostředí.|

### <a name="static-functions"></a>Statické funkce

|||
|-|-|
|[Classic](#classic)|Statická funkce členu vrátí objekt národního prostředí, který představuje klasické národní prostředí jazyka C.|
|[global](#global)|Obnoví výchozí národní prostředí pro program.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](#op_neq)|Testuje dvě národní prostředí na nerovnost.|
|[operátor)](#op_call)|Porovná dva `basic_string` objekty.|
|[operator==](#op_eq_eq)|Testuje dvě národní prostředí na rovnost.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[facet](#facet_class)|Třída, která slouží jako základní třída pro všechny omezující vlastnosti národního prostředí.|
|[id](#id_class)|Třída členu poskytuje jedinečnou identifikaci omezující podmínky, která se používá jako index při vyhledávání omezujících vlastností v národním prostředí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** – std

## <a name="category"></a>  locale::category

Typ integer, který poskytuje hodnoty bitové masky pro skupiny standardních omezujících vlastností.

```cpp
typedef int category;
static const int collate = LC_COLLATE;
static const int ctype = LC_CTYPE;
static const int monetary = LC_MONETARY;
static const int numeric = LC_NUMERIC;
static const int time = LC_TIME;
static const int messages = LC_MESSAGES;
static const int all = LC_ALL;
static const int none = 0;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `int` typu, která představuje skupinu různých elementů bitová maska místní pro národní prostředí – třída typu nebo můžete použít k reprezentování žádné odpovídající kategorie národního prostředí C. Elementy jsou:

- **COLLATE**, odpovídající kategorii C lc_collate –

- **ctype**, odpovídající kategorii C LC_CTYPE –

- **peněžní**, odpovídající kategorii C lc_monetary –

- **číselné**, odpovídající kategorii C lc_numeric –

- **čas**, odpovídající kategorii C lc_time –

- **zprávy**, odpovídající kategorii Posix LC_MESSAGES

Kromě toho jsou užitečné dvou hodnot:

- **žádný**, odpovídajících do žádné kategorie C

- **všechny**, odpovídající sjednocení C všechny kategorie LC_ALL –

Může představovat libovolný skupiny kategorie pomocí `OR` s tyto konstanty, jako v **peněžní** &#124; **čas**.

## <a name="classic"></a>  locale::Classic

Statická funkce členu vrátí objekt národního prostředí, který představuje klasické národní prostředí jazyka C.

```cpp
static const locale& classic();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na C národní prostředí.

### <a name="remarks"></a>Poznámky

Národní prostředí classic C je USA Anglickou ASCII národního prostředí v rámci standardní knihovny jazyka C implicitně používaný v programech, které nejsou mezinárodní.

### <a name="example"></a>Příklad

```cpp
// locale_classic.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: " << loc2.name( )
        << "." << endl;
   cout << "The name of the current locale is: " << loc1.name( )
        << "." << endl;

   if (loc2 == locale::classic( ) )
      cout << "The previous locale was classic." << endl;
   else
      cout << "The previous locale was not classic." << endl;

   if (loc1 == locale::classic( ) )
      cout << "The current locale is classic." << endl;
   else
      cout << "The current locale is not classic." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
The previous locale was classic.
The current locale is not classic.
```

## <a name="combine"></a>  locale::Combine

Vloží omezující vlastnost ze zadaného národního prostředí do cílového národního prostředí.

```cpp
template <class Facet>
locale combine(const locale& Loc) const;
```

### <a name="parameters"></a>Parametry

`Loc` Národní prostředí obsahující omezující vlastnosti má být vložen do cílové národní prostředí.

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí objekt národního prostředí, který nahrazuje v nebo ho přidá k  **\*to** omezující vlastnost `Facet` uvedené v `Loc`.

### <a name="example"></a>Příklad

```cpp
// locale_combine.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s; it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   locale loc3 = loc2.combine<collate<_TCHAR> > (loc);
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;
}
```

## <a name="facet_class"></a>  facet – třída

Třída, která slouží jako základní třída pro všechny omezující vlastnosti národního prostředí.

```cpp
class facet {
protected:
    explicit facet(size_t _Refs = 0);
   virtual ~facet();
private:
   facet(const facet&)
   // not defined void operator=(const facet&)
     // not defined
};
```

### <a name="remarks"></a>Poznámky

Všimněte si, že nelze kopírovat a přiřaďte objekt omezující vlastnosti třídy. Můžete vytvořit a zrušení objektů odvozených od třídy `locale::facet` , ale ne objekty správné základní třídy. Obvykle vytvoříte objekt `_Myfac` odvozené od omezující vlastnosti, když vytvoříte v národním prostředí, jako v **localeloc**( `locale::classic`(), **nové**`_Myfac`);

V takových případech by měl mít v konstruktoru pro základní třídu omezující vlastnost nulu `_Refs` argument. Pokud objekt je již nepotřebujete, je odstraněn. Proto je zadat nenulové hodnoty _ *odolný systém souborů* argument pouze v těchto výjimečných případech, kdy převzít odpovědnost za dobu životnosti objektu.

## <a name="global"></a>  locale::Global

Obnoví výchozí národní prostředí pro program. Tato akce ovlivní globální národní prostředí pro C a C++.

```cpp
static locale global(const locale& Loc);
```

### <a name="parameters"></a>Parametry

`Loc` Národní prostředí má být použit jako výchozí národní prostředí program.

### <a name="return-value"></a>Návratová hodnota

Předchozí národního prostředí, než byl resetován výchozí národní prostředí.

### <a name="remarks"></a>Poznámky

Při spuštění programu globální národního prostředí je stejný jako classic národní prostředí. `global()` Volání funkce `setlocale( LC_ALL, loc.name. c_str())` k navázání odpovídající národního prostředí v knihovně standardní C.

### <a name="example"></a>Příklad

```cpp
// locale_global.cpp
// compile by using: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   locale loc1;
   cout << "The initial locale is: " << loc1.name( ) << endl;
   locale loc2 = locale::global ( loc );
   locale loc3;
   cout << "The current locale is: " << loc3.name( ) << endl;
   cout << "The previous locale was: " << loc2.name( ) << endl;
}
```

```Output
The initial locale is: C
The current locale is: German_Germany.1252
The previous locale was: C
```

## <a name="id_class"></a>  ID – třída

Třída členu poskytuje jedinečnou identifikaci omezující podmínky, která se používá jako index při vyhledávání omezujících vlastností v národním prostředí.

id třídy {chráněné: id(); privátní: id(const id&) / / není definována void – operátor =(const id&) / / není definována};

### <a name="remarks"></a>Poznámky

Třída členů popisuje objekt statický člen vyžaduje každý omezující vlastnost jedinečný národního prostředí. Poznámka: nelze kopírovat nebo přiřadit objekt třídy **id**.

## <a name="locale"></a>  locale::Locale

Vytvoří národní prostředí nebo kopii národního prostředí či kopii národního prostředí, kde byla omezující vlastnost nebo kategorie nahrazena omezující vlastností nebo kategorií z jiného národního prostředí.

```cpp
locale();

explicit locale(const char* Locname, category Cat = all);
explicit locale(const string& Locname);
locale( const locale& Loc);
locale(const locale& Loc, const locale& Other, category Cat);
locale(const locale& Loc, const char* Locname, category Cat);

template <class Facet>
locale(const locale& Loc, const Facet* Fac);
```

### <a name="parameters"></a>Parametry

`Locname` Název v národním prostředí.

`Loc` Národní prostředí, která se zkopírují při vytváření nové národní prostředí.

`Other` Národní prostředí ze kterého mají být vyberte kategorii.

`Cat` Kategorii, kterou chcete nahrazena do sestavené národní prostředí.

`Fac` Omezující vlastnost k nahrazena do sestavené národní prostředí.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje objekt, který má odpovídající globální národní prostředí. Druhý a třetí konstruktory inicializovat všechny kategorie národního prostředí tak, aby měl chování, které jsou konzistentní s názvem národní prostředí `Locname`. Zkopírujte zbývající konstruktory `Loc`, s výjimkou uvedeno:

`locale(const locale& Loc, const locale& Other, category Cat);`

nahradí z `Other` těchto omezující vlastnosti odpovídající kategorii C pro které C & `Cat` nenulový.

`locale(const locale& Loc, const char* Locname, category Cat);`

`locale(const locale& Loc, const string& Locname, category Cat);`

nahradí z `locale(Locname, _All)` těchto omezující vlastnosti odpovídající kategorii C pro které C & `Cat` nenulový.

`template<class Facet> locale(const locale& Loc, Facet* Fac);`

nahradí v (nebo ho přidá k) `Loc` omezující vlastnost `Fac`, pokud `Fac` není nulový ukazatel.

Pokud název národního prostředí `Locname` je nulový ukazatel nebo jinak neplatných, funkce vyvolá [runtime_error](../standard-library/runtime-error-class.md).

### <a name="example"></a>Příklad

```cpp
// locale_locale.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( ) {

   // Second constructor
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   // The first (default) constructor
   locale loc2;
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   // Third constructor
   locale loc3 (loc2,loc, _M_COLLATE );
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;

   // Fourth constructor
   locale loc4 (loc2, "German_Germany", _M_COLLATE );
   int result4 = use_facet<collate<_TCHAR> > ( loc4 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc4 ) << result4 << endl;
}
```

## <a name="name"></a>  locale::Name

Vrátí název uloženého národního prostředí.

```cpp
string name() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec, která poskytuje název národního prostředí.

### <a name="example"></a>Příklad

```cpp
// locale_name.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: "
        << loc2.name( ) << "." << endl;
   cout << "The name of the current locale is: "
        << loc1.name( ) << "." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
```

## <a name="op_neq"></a>  locale::Operator! =

Testuje dvě národní prostředí na nerovnost.

```cpp
bool operator!=(const locale& right) const;
```

### <a name="parameters"></a>Parametry

`right` Jeden národních prostředí, které má být testována nerovnost.

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která je **true** Pokud národní prostředí nejsou kopie stejném národním prostředí; **false** Pokud se národní prostředí kopie stejném národním prostředí.

### <a name="remarks"></a>Poznámky

Pokud jsou stejném národním prostředí, pokud je kopie dalších, nebo pokud mají stejné názvy dvou národní prostředí jsou si rovny.

### <a name="example"></a>Příklad

```cpp
// locale_op_ne.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 != loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are equal." << endl;

   if ( loc1 != loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are equal." << endl;
}
```

```Output
locales loc1 (German_Germany.1252) and
 loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252) and
 loc3 (English_United States.1252) are not equal.
```

## <a name="op_call"></a>  locale:: operator()

Porovná dva `basic_string` objekty.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right) const;
```

### <a name="parameters"></a>Parametry

`left` Levé řetězec.

`right` Pravé řetězec.

### <a name="return-value"></a>Návratová hodnota

Členské funkce vrátí hodnotu:

- -1, pokud je první pořadí porovná nižší než druhý pořadí.

- + 1, pokud druhý pořadí porovná nižší než první pořadí.

- 0, pokud odpovídají pořadí.

### <a name="remarks"></a>Poznámky

Členská funkce efektivně provede:

```cpp
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```

Proto můžete objekt národního prostředí jako objekt funkce.

### <a name="example"></a>Příklad

```cpp
// locale_op_compare.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

int main( )
{
   using namespace std;
   wchar_t *sa = L"ztesting";
   wchar_t *sb = L"\0x00DFtesting";
   basic_string<wchar_t> a( sa );
   basic_string<wchar_t> b( sb );

   locale loc( "German_Germany" );
   cout << loc( a,b ) << endl;

   const collate<wchar_t>& fac = use_facet<collate<wchar_t> >( loc );
   cout << ( fac.compare( sa, sa + a.length( ),
       sb, sb + b.length( ) ) < 0) << endl;
}
```

```Output
0
0
```

## <a name="op_eq_eq"></a>  locale::Operator ==

Testuje dvě národní prostředí na rovnost.

```cpp
bool operator==(const locale& right) const;
```

### <a name="parameters"></a>Parametry

`right` Jeden národních prostředí, které má být testována rovnosti.

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která je **true** Pokud se národní prostředí kopie stejném národním prostředí; **false** Pokud národní prostředí nejsou kopie stejném národním prostředí.

### <a name="remarks"></a>Poznámky

Pokud jsou stejném národním prostředí, pokud je kopie dalších, nebo pokud mají stejné názvy dvou národní prostředí jsou si rovny.

### <a name="example"></a>Příklad

```cpp
// locale_op_eq.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 == loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are not equal."
      << endl;

   if ( loc1 == loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are not equal."
      << endl;
}
```

```Output
locales loc1 (German_Germany.1252)
 and loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252)
 and loc3 (English_United States.1252) are not equal.
```

## <a name="see-also"></a>Viz také

[\<národní prostředí >](../standard-library/locale.md)<br/>
[Znakové stránky](../c-runtime-library/code-pages.md)<br/>
[Názvy národních prostředí, jazyků a řetězce zemí/oblastí](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
