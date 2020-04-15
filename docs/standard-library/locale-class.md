---
title: locale – třída
ms.date: 03/19/2019
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
ms.openlocfilehash: 2581c5cdacc9e542f5d911860128dcf5526621ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367318"
---
# <a name="locale-class"></a>locale – třída

Třída, která popisuje místní objekt, který zapouzdří informace specifické pro jazykovou verzi jako sadu omezujících vlastností, jež společně definují určité lokalizované prostředí.

## <a name="syntax"></a>Syntaxe

```cpp
class locale;
```

## <a name="remarks"></a>Poznámky

Omezující faset je ukazatel na objekt třídy odvozené z [omezující název](#facet_class) třídy, který má veřejný objekt formuláře:

```cpp
static locale::id id;
```

Můžete definovat neuzavřenou množinu těchto omezujících vlastností. Můžete také sestavit objekt národního prostředí, který určuje libovolný počet omezujících vlastností.

Předdefinované skupiny těchto omezujících stran představují [kategorie národního prostředí](#category) tradičně `setlocale`spravované v knihovně Standard C funkcí .

Kategorie `collate` (LC_COLLATE) zahrnuje fazety:

```cpp
collate<char>
collate<wchar_t>
```

Kategorie `ctype` (LC_CTYPE) zahrnuje fazety:

```cpp
ctype<char>
ctype<wchar_t>
codecvt<char, char, mbstate_t>
codecvt<wchar_t, char, mbstate_t>
codecvt<char16_t, char, mbstate_t>
codecvt<char32_t, char, mbstate_t>
```

Kategorie `monetary` (LC_MONETARY) zahrnuje omezující aspekty:

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

Kategorie `numeric` (LC_NUMERIC) zahrnuje fazety:

```cpp
num_get<char, istreambuf_iterator<char>>
num_get<wchar_t, istreambuf_iterator<wchar_t>>
num_put<char, ostreambuf_iterator<char>>
num_put<wchar_t, ostreambuf_iterator<wchar_t>>
numpunct<char>
numpunct<wchar_t>
```

Kategorie `time` (LC_TIME) zahrnuje fazety:

```cpp
time_get<char, istreambuf_iterator<char>>
time_get<wchar_t, istreambuf_iterator<wchar_t>>
time_put<char, ostreambuf_iterator<char>>
time_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

Kategorie `messages` (LC_MESSAGES) zahrnuje omezující aspekty:

```cpp
messages<char>
messages<wchar_t>
```

(Poslední kategorie je vyžadována POSIX, ale ne Standard C.)

Některé z těchto předdefinovaných omezujících `iostream` položek jsou používány třídami k řízení převodu číselných hodnot do a z textových sekvencí.

Objekt národního prostředí třídy také ukládá název národního prostředí jako objekt [řetězce](../standard-library/string-typedefs.md#string)třídy . Použití neplatného názvu národního prostředí k vytvoření omezující znak národního prostředí nebo objektu národního prostředí vyvolá objekt [třídy runtime_error](../standard-library/runtime-error-class.md). Název uloženého národního prostředí je, `"*"` pokud objekt národního prostředí nemůže být jistý, že národní prostředí ve stylu C přesně odpovídá národnímu prostředí reprezentovanému objektem. V opačném případě můžete vytvořit odpovídající národní prostředí v knihovně `locale_object`Standard `setlocale(LC_ALL , locale_object.`C pro některé objekty národního prostředí [pomocí](#name)`().c_str())`názvu .

V této implementaci můžete také volat statickou členskou funkci:

```cpp
static locale empty();
```

k vytvoření objektu národního prostředí, který nemá žádné omezující vlastnosti Je to také transparentní národní prostředí. Pokud šablona funguje [has_facet](../standard-library/locale-functions.md#has_facet) a [use_facet](../standard-library/locale-functions.md#use_facet) nemůže najít požadovanou omezující vlastnost v průhledném národním prostředí, nejprve konzultují globální národní prostředí a pak, pokud je to transparentní, klasické národní prostředí. Takže můžete napsat:

```cpp
cout.imbue(locale::empty());
```

Následné vložení do [`cout`](../standard-library/iostream.md#cout) jsou zprostředkovány aktuální stav globální národní prostředí. Lze dokonce psát:

```cpp
locale loc(locale::empty(),
    locale::classic(),
    locale::numeric);

cout.imbue(loc);
```

Číselná pravidla formátování pro následné vložení `cout` zůstanou stejná jako v národním prostředí C, a to i přesto, že globální národní prostředí poskytuje měnící se pravidla pro vkládání kalendářních dat a peněžních částek.

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
|[combine](#combine)|Vloží omezující vlastnost ze zadaného národního prostředí do cílového národního prostředí.|
|[Jméno](#name)|Vrátí název uloženého národního prostředí.|

### <a name="static-functions"></a>Statické funkce

|||
|-|-|
|[Klasické](#classic)|Statická funkce členu vrátí objekt národního prostředí, který představuje klasické národní prostředí jazyka C.|
|[Globální](#global)|Obnoví výchozí národní prostředí pro program.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí národní prostředí.|
|[operátor!=](#op_neq)|Testuje dvě národní prostředí na nerovnost.|
|[operátor( )](#op_call)|Porovná dva `basic_string` objekty.|
|[operátor==](#op_eq_eq)|Testuje dvě národní prostředí na rovnost.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[omezující vlastnost](#facet_class)|Třída, která slouží jako základní třída pro všechny omezující vlastnosti národního prostředí.|
|[`id`](#id_class)|Třída členu poskytuje jedinečnou identifikaci omezující podmínky, která se používá jako index při vyhledávání omezujících vlastností v národním prostředí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> národního prostředí

**Obor názvů:** std

## <a name="localecategory"></a><a name="category"></a>národní prostředí::kategorie

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

Typ je synonymum pro typ **int,** který může představovat skupinu odlišných prvků typu bitmask místní do národního prostředí třídy nebo lze použít k reprezentaci libovolné odpovídající kategorie národního prostředí C. Prvky jsou:

- `collate`, který odpovídá LC_COLLATE kategorie C

- `ctype`, který odpovídá LC_CTYPE kategorie C

- `monetary`, který odpovídá LC_MONETARY kategorie C

- `numeric`, který odpovídá LC_NUMERIC kategorie C

- `time`, který odpovídá LC_TIME kategorie C

- `messages`, který odpovídá LC_MESSAGES kategorie POSIX

Další dvě užitečné hodnoty jsou:

- `none`, která neodpovídá žádné z kategorií C

- `all`, který odpovídá sjednocení C všech kategorií LC_ALL

Můžete reprezentovat libovolnou skupinu kategorií `OR` pomocí těchto konstant, `monetary` `time`jako v &#124; .

## <a name="localeclassic"></a><a name="classic"></a>národní prostředí::klasické

Statická funkce členu vrátí objekt národního prostředí, který představuje klasické národní prostředí jazyka C.

```cpp
static const locale& classic();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na národní prostředí C.

### <a name="remarks"></a>Poznámky

Klasické národní prostředí C je národní prostředí ASCII v americké angličtině v knihovně Standard C. Je to národní prostředí, které se používá implicitně v programech, které nejsou internacionalizované.

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

## <a name="localecombine"></a><a name="combine"></a>národní prostředí::kombinovat

Vloží omezující vlastnost ze zadaného národního prostředí do cílového národního prostředí.

```cpp
template <class Facet>
locale combine(const locale& source_locale) const;
```

### <a name="parameters"></a>Parametry

*source_locale*\
Národní prostředí obsahující omezující slohou, která má být vložena do cílového národního prostředí.

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí objekt národního prostředí, který nahradí `Facet` nebo přidá do ** \*tohoto** omezující ho saznece uvedeného v *source_locale*.

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

## <a name="facet-class"></a><a name="facet_class"></a>fazeta třídy

Třída, která slouží jako základní třída pro všechny omezující vlastnosti národního prostředí.

```cpp
class facet {
protected:
    explicit facet(size_t references = 0);
    virtual ~facet();
private:
    facet(const facet&) // not defined
    void operator=(const facet&) // not defined
};
```

### <a name="remarks"></a>Poznámky

Objekt třídy `facet`nelze kopírovat ani přiřazovat. Můžete vytvořit a zničit objekty `locale::facet` odvozené z třídy, ale ne objekty vlastní základní třídy. Objekt `_Myfac` odvozený z `facet` objektu `locale`, který je obvykle odvozen, se obvykle vytváří jako v`locale loc(locale::classic(), new _Myfac);`

V takových případech by měl mít `facet` konstruktor pro základní třídu argument s nulovými *odkazy.* Pokud objekt již není potřeba, je odstraněn, takže zadáte argument *nenulové odkazy* pouze v těch výjimečných případech, kdy převezmete odpovědnost za životnost objektu.

## <a name="localeglobal"></a><a name="global"></a>národní prostředí::globální

Obnoví výchozí národní prostředí programu. Toto volání ovlivňuje globální národní prostředí pro C i C++.

```cpp
static locale global(const locale& new_default_locale);
```

### <a name="parameters"></a>Parametry

*new_default_locale*\
Národní prostředí, které má být programem použito jako výchozí národní prostředí.

### <a name="return-value"></a>Návratová hodnota

Předchozí národní prostředí před obnovením výchozího národního prostředí.

### <a name="remarks"></a>Poznámky

Při spuštění programu je globální národní prostředí stejné jako klasické národní prostředí. Funkce `global()` volá `setlocale( LC_ALL, loc.name. c_str())` vytvořit odpovídající národní prostředí v knihovně Standard C.

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

## <a name="id-class"></a><a name="id_class"></a>třída id

Třída členu poskytuje jedinečnou identifikaci omezující podmínky, která se používá jako index při vyhledávání omezujících vlastností v národním prostředí.

```cpp
class id
{
   protected:    id();
   private:      id(const id&)
   void operator=(const id&)  // not defined
};
```

### <a name="remarks"></a>Poznámky

Třída členů popisuje statický objekt člena vyžadované ho každého jedinečného omezujícího vlastnosti národního prostředí. Objekt třídy `id`nelze kopírovat ani přiřazovat.

## <a name="localelocale"></a><a name="locale"></a>národní prostředí::národní prostředí

Vytvoří národní prostředí nebo kopii národního prostředí či kopii národního prostředí, kde byla omezující vlastnost nebo kategorie nahrazena omezující vlastností nebo kategorií z jiného národního prostředí. Obsahuje také destruktor.

```cpp
locale();

explicit locale(const char* locale_name, category new_category = all);
explicit locale(const string& locale_name);
locale(const locale& from_locale);
locale(const locale& from_locale, const locale& Other, category new_category);
locale(const locale& from_locale, const char* locale_name, category new_category);

template <class Facet>
locale(const locale& from_locale, const Facet* new_facet);

~locale();
```

### <a name="parameters"></a>Parametry

*locale_name*\
Název národního prostředí.

*from_locale*\
Národní prostředí, které má být zkopírováno při vytváření nového národního prostředí.

*Další*\
Národní prostředí, ze kterého chcete vybrat kategorii.

*new_category*\
Kategorie, která má být nahrazena do vytvořeného národního prostředí.

*new_facet*\
Omezující stařec, který má být nahrazen do vytvořeného národního prostředí.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje objekt tak, aby odpovídal globálnímu národnímu prostředí. Druhý a třetí konstruktory inicializovat všechny kategorie národního prostředí mít chování konzistentní s název národního prostředí *locale_name*. Zbývající konstruktory kopírují *from_locale*s uvedenou výjimkou:

`locale(const locale& from_locale, const locale& Other, category new_category);`

nahrazuje z *ostatních* fasety odpovídající kategorii C, pro kterou je C & *new_category* nenulová.

`locale(const locale& from_locale, const char* locale_name, category new_category);`

`locale(const locale& from_locale, const string& locale_name, category new_category);`

nahradí z `locale(locale_name, all)` těchto omezujících stran *odpovídajících* replace_category `replace_category & new_category` kategorie, pro kterou je nenulová.

`template<class Facet> locale(const locale& from_locale, Facet* new_facet);`

nahradí v (nebo *přidá) from_locale* *omezující*new_facet , pokud *new_facet* není ukazatel null.

Pokud název národního prostředí *locale_name* je ukazatel null nebo jinak neplatné, funkce vyvolá [runtime_error](../standard-library/runtime-error-class.md).

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

## <a name="localename"></a><a name="name"></a>národní prostředí::název

Vrátí název uloženého národního prostředí.

```cpp
string name() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec s názvem národního prostředí.

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

## <a name="localeoperator"></a><a name="op_eq"></a>národní prostředí::operátor=

Přiřadí národní prostředí.

```cpp
const locale& operator=(const locale& other) noexcept;
```

## <a name="localeoperator"></a><a name="op_neq"></a>národní prostředí::operátor!=

Testuje dvě národní prostředí na nerovnost.

```cpp
bool operator!=(const locale& right) const;
```

### <a name="parameters"></a>Parametry

*Právo*\
Jeden z národních prostředí, které mají být testovány na nerovnost.

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která je **true,** pokud národní prostředí nejsou kopie stejného národního prostředí. Je **false,** pokud národní prostředí jsou kopie stejného národního prostředí.

### <a name="remarks"></a>Poznámky

Dvě národní prostředí jsou stejné, pokud jsou stejné národní prostředí, pokud jeden je kopie druhé, nebo pokud mají stejné názvy.

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

## <a name="localeoperator"></a><a name="op_call"></a>národní prostředí::operator()

Porovná dva `basic_string` objekty.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right) const;
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Levý řetězec.

*Právo*\
Správný řetězec.

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí:

- -1, pokud první sekvence porovnává méně než druhá sekvence.

- +1, pokud druhá sekvence porovnává méně než první sekvenci.

- 0, pokud jsou sekvence rovnocenné.

### <a name="remarks"></a>Poznámky

Členská funkce efektivně provádí:

```cpp
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```

To znamená, že můžete použít objekt národního prostředí jako objekt funkce.

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

## <a name="localeoperator"></a><a name="op_eq_eq"></a>národní prostředí::operator==

Testuje dvě národní prostředí na rovnost.

```cpp
bool operator==(const locale& right) const;
```

### <a name="parameters"></a>Parametry

*Právo*\
Jedno z národních prostředí, které mají být testovány na rovnost.

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která je **true,** pokud národní prostředí jsou kopie stejného národního prostředí. Je **nepravdivé,** pokud národní prostředí nejsou kopie stejné hojné prostředí.

### <a name="remarks"></a>Poznámky

Dvě národní prostředí jsou stejné, pokud jsou stejné národní prostředí, pokud jeden je kopie druhé, nebo pokud mají stejné názvy.

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

[\<>národního prostředí](../standard-library/locale.md)\
[Znakové stránky](../c-runtime-library/code-pages.md)\
[Názvy národních prostředí, jazyky a řetězce zemí nebo oblastí](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
