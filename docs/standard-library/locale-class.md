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
ms.openlocfilehash: 551bca93a30bee52dc4c838864df28cb747d91df
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856496"
---
# <a name="locale-class"></a>locale – třída

Třída, která popisuje místní objekt, který zapouzdří informace specifické pro jazykovou verzi jako sadu omezujících vlastností, jež společně definují určité lokalizované prostředí.

## <a name="syntax"></a>Syntaxe

```cpp
class locale;
```

## <a name="remarks"></a>Poznámky

Omezující vlastnost je ukazatel na objekt třídy odvozené od třídy [omezující vlastnost](#facet_class) , která má veřejný objekt formuláře:

```cpp
static locale::id id;
```

Můžete definovat neuzavřenou množinu těchto omezujících vlastností. Můžete také sestavit objekt národního prostředí, který určuje libovolný počet omezujících vlastností.

Předdefinované skupiny těchto omezujících vlastností reprezentují [kategorie národního prostředí](#category) tradičně spravované v standardní knihovně jazyka C funkcí `setlocale`.

Kategorie `collate` (LC_COLLATE) obsahuje omezující vlastnosti:

```cpp
collate<char>
collate<wchar_t>
```

Kategorie `ctype` (LC_CTYPE) obsahuje omezující vlastnosti:

```cpp
ctype<char>
ctype<wchar_t>
codecvt<char, char, mbstate_t>
codecvt<wchar_t, char, mbstate_t>
codecvt<char16_t, char, mbstate_t>
codecvt<char32_t, char, mbstate_t>
```

Kategorie `monetary` (LC_MONETARY) obsahuje omezující vlastnosti:

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

Kategorie `numeric` (LC_NUMERIC) obsahuje omezující vlastnosti:

```cpp
num_get<char, istreambuf_iterator<char>>
num_get<wchar_t, istreambuf_iterator<wchar_t>>
num_put<char, ostreambuf_iterator<char>>
num_put<wchar_t, ostreambuf_iterator<wchar_t>>
numpunct<char>
numpunct<wchar_t>
```

Kategorie `time` (LC_TIME) obsahuje omezující vlastnosti:

```cpp
time_get<char, istreambuf_iterator<char>>
time_get<wchar_t, istreambuf_iterator<wchar_t>>
time_put<char, ostreambuf_iterator<char>>
time_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

Kategorie `messages` (LC_MESSAGES) obsahuje omezující vlastnosti:

```cpp
messages<char>
messages<wchar_t>
```

(Poslední kategorie vyžaduje POSIX, ale ne Standard C.)

Některé z těchto předdefinovaných omezujících vlastností jsou používány třídami `iostream` pro řízení převodu číselných hodnot do sekvence textu a z nich.

Objekt národního prostředí třídy také ukládá název národního prostředí jako objekt [řetězce](../standard-library/string-typedefs.md#string)třídy. Použití neplatného názvu národního prostředí k vytvoření omezující vlastnosti národního prostředí nebo objektu národního prostředí vyvolá objekt třídy [runtime_error](../standard-library/runtime-error-class.md). Uložený název národního prostředí je `"*"`, pokud objekt národního prostředí nemůže být jistý, že národní prostředí ve stylu jazyka C odpovídá přesně jednomu reprezentovanému objektem. V opačném případě můžete vytvořit vyhovující národní prostředí v rámci standardní knihovny jazyka C pro některý objekt národního prostředí `locale_object`voláním `setlocale(LC_ALL , locale_object.`[name](#name)`().c_str())`.

V této implementaci můžete také volat statickou členskou funkci:

```cpp
static locale empty();
```

k vytvoření objektu národního prostředí, který nemá žádné omezující vlastnosti Je to také transparentní národní prostředí. Pokud funkce šablony [has_facet](../standard-library/locale-functions.md#has_facet) a [use_facet](../standard-library/locale-functions.md#use_facet) nenalezne požadovanou omezující vlastnost v transparentním národním prostředí, požádejte nejprve o globální národní prostředí a potom, pokud je transparentní, klasické národní prostředí. Můžete tedy napsat:

```cpp
cout.imbue(locale::empty());
```

Následná vložení do [`cout`](../standard-library/iostream.md#cout) jsou vyzpůsobena aktuálním stavem globálního národního prostředí. Lze dokonce psát:

```cpp
locale loc(locale::empty(),
    locale::classic(),
    locale::numeric);

cout.imbue(loc);
```

Pravidla formátování čísel pro další vložení do `cout` zůstanou stejná jako v národním prostředí C, i když globální národní prostředí poskytuje měnící se pravidla pro vkládání dat a peněžních částek.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[jazyka](#locale)|Vytvoří národní prostředí nebo kopii národního prostředí či kopii národního prostředí, kde byla omezující vlastnost nebo kategorie nahrazena omezující vlastností nebo kategorií z jiného národního prostředí.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[kategorií](#category)|Typ integer, který poskytuje hodnoty bitové masky pro skupiny standardních omezujících vlastností.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[spojen](#combine)|Vloží omezující vlastnost ze zadaného národního prostředí do cílového národního prostředí.|
|[Jméno](#name)|Vrátí název uloženého národního prostředí.|

### <a name="static-functions"></a>Statické funkce

|||
|-|-|
|[standardním](#classic)|Statická funkce členu vrátí objekt národního prostředí, který představuje klasické národní prostředí jazyka C.|
|[global](#global)|Obnoví výchozí národní prostředí pro program.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí národní prostředí.|
|[operator!=](#op_neq)|Testuje dvě národní prostředí na nerovnost.|
|[operator () – operátor](#op_call)|Porovná dva objekty `basic_string`.|
|[operator = = – operátor](#op_eq_eq)|Testuje dvě národní prostředí na rovnost.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[facet](#facet_class)|Třída, která slouží jako základní třída pro všechny omezující vlastnosti národního prostředí.|
|[`id`](#id_class)|Třída členu poskytuje jedinečnou identifikaci omezující podmínky, která se používá jako index při vyhledávání omezujících vlastností v národním prostředí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Obor názvů:** std

## <a name="category"></a>locale:: Category

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

Typ je synonymum pro typ **int** , který může představovat skupinu různých prvků typu maskování Local do národního prostředí třídy nebo může být použita k reprezentaci kterékoli z odpovídajících kategorií národního prostředí jazyka C. Prvky jsou:

- `collate`odpovídající kategorii C LC_COLLATE

- `ctype`odpovídající kategorii C LC_CTYPE

- `monetary`odpovídající kategorii C LC_MONETARY

- `numeric`odpovídající kategorii C LC_NUMERIC

- `time`odpovídající kategorii C LC_TIME

- `messages`odpovídající kategorii POSIX LC_MESSAGES

Dvě užitečnější hodnoty jsou:

- `none`odpovídající žádné kategorii C

- `all`odpovídající sjednocení jazyka C u všech kategorií LC_ALL

Můžete znázornit libovolnou skupinu kategorií pomocí `OR` s těmito konstantami, jako v `monetary` &#124; `time`.

## <a name="classic"></a>locale:: Classic

Statická funkce členu vrátí objekt národního prostředí, který představuje klasické národní prostředí jazyka C.

```cpp
static const locale& classic();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na národní prostředí jazyka C.

### <a name="remarks"></a>Poznámky

Klasické národní prostředí jazyka C je národní prostředí ASCII anglické abecedy v rámci standardní knihovny jazyka C. Jedná se o národní prostředí, které se implicitně používá v aplikacích, které nejsou mezinárodní.

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

## <a name="combine"></a>locale:: kombinovat

Vloží omezující vlastnost ze zadaného národního prostředí do cílového národního prostředí.

```cpp
template <class Facet>
locale combine(const locale& source_locale) const;
```

### <a name="parameters"></a>Parametry

*source_locale*\
Národní prostředí obsahující omezující vlastnost, která má být vložena do cílového národního prostředí.

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí objekt národního prostředí, který nahradí nebo přidá **\*tuto** omezující vlastnost `Facet` uvedena v *source_locale*.

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

## <a name="facet_class"></a>Face – třída

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

Nelze kopírovat ani přiřadit objekt třídy `facet`. Můžete vytvářet a zničit objekty odvozené z třídy `locale::facet` ale nikoli objekty základní třídy. Obvykle vytváříte objekt `_Myfac` odvozený z `facet` při vytváření `locale`, jako v `locale loc(locale::classic(), new _Myfac);`

V takových případech má konstruktor pro základní třídu `facet` mít nulový argument *REFERENCES* . Když objekt již není potřeba, je odstraněn, takže zadáte nenulový argument *odkazy* pouze ve výjimečných případech, kde potrváte za dobu života objektu.

## <a name="global"></a>locale:: Global

Obnoví výchozí národní prostředí programu. Toto volání má vliv na globální národní prostředí pro C C++i.

```cpp
static locale global(const locale& new_default_locale);
```

### <a name="parameters"></a>Parametry

*new_default_locale*\
Národní prostředí, které má program použít jako výchozí národní prostředí.

### <a name="return-value"></a>Návratová hodnota

Předchozí národní prostředí před resetováním výchozího národního prostředí.

### <a name="remarks"></a>Poznámky

Při spuštění programu je globální národní prostředí stejné jako klasické národní prostředí. Funkce `global()` volá `setlocale( LC_ALL, loc.name. c_str())` k vytvoření odpovídajícího národního prostředí ve standardní knihovně jazyka C.

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

## <a name="id_class"></a>ID – třída

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

Třída member popisuje statický členský objekt vyžadovaný jednotlivými jedinečnými omezujícími vlastnostmi národního prostředí. Nelze kopírovat ani přiřadit objekt třídy `id`.

## <a name="locale"></a>locale:: locale

Vytvoří národní prostředí nebo kopii národního prostředí či kopii národního prostředí, kde byla omezující vlastnost nebo kategorie nahrazena omezující vlastností nebo kategorií z jiného národního prostředí. Zahrnuje také destruktor.

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
Národní prostředí, které se má zkopírovat při vytváření nového národního prostředí.

*Jiné*\
Národní prostředí, ze kterého se má vybrat kategorie

*new_category*\
Kategorie, která má být nahrazena vytvořeným národním prostředím.

*new_facet*\
Omezující vlastnost, která má být nahrazena vytvořeným národním prostředím.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje objekt tak, aby odpovídal globálnímu národnímu prostředí. Druhý a třetí konstruktor inicializuje všechny kategorie národního prostředí, aby měly chování konzistentní s názvem národního prostředí *locale_name*. Zbývající konstruktory kopírují *from_locale*s zaznamenanými výjimkami:

`locale(const locale& from_locale, const locale& Other, category new_category);`

nahrazuje *jinou* omezující vlastnost, která odpovídá kategorii c, pro kterou je c & *new_category* nenulové.

`locale(const locale& from_locale, const char* locale_name, category new_category);`

`locale(const locale& from_locale, const string& locale_name, category new_category);`

nahradí z `locale(locale_name, all)` charakteristiky odpovídající *replace_category* kategorie, pro které `replace_category & new_category` není nula.

`template<class Facet> locale(const locale& from_locale, Facet* new_facet);`

nahradí v (nebo přidá do) *from_locale* omezující vlastnost *new_facet*, pokud *new_facet* ukazatel na hodnotu null.

Pokud je název národního prostředí *locale_name* ukazatel s hodnotou null nebo jinak neplatný, funkce vyvolá [runtime_error](../standard-library/runtime-error-class.md).

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

## <a name="name"></a>locale:: Name

Vrátí název uloženého národního prostředí.

```cpp
string name() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec udávající název národního prostředí.

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

## <a name="op_eq"></a>locale:: operator =

Přiřadí národní prostředí.

```cpp
const locale& operator=(const locale& other) noexcept;
```

## <a name="op_neq"></a>locale:: operator! =

Testuje dvě národní prostředí na nerovnost.

```cpp
bool operator!=(const locale& right) const;
```

### <a name="parameters"></a>Parametry

*pravé*\
Jedna z národních prostředí, která mají být testována na nerovnost.

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která má **hodnotu true** , pokud národní prostředí nejsou kopie stejného národního prostředí. Je **false** , pokud jsou místní kopie stejného národního prostředí.

### <a name="remarks"></a>Poznámky

Dvě národní prostředí se rovnají, pokud se shodují se stejným národním prostředím, pokud je jedna z kopií druhé, nebo pokud mají stejné názvy.

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

## <a name="op_call"></a>locale:: operator () – operátor ()

Porovná dva objekty `basic_string`.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right) const;
```

### <a name="parameters"></a>Parametry

*levý*\
Levý řetězec.

*pravé*\
Pravý řetězec.

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí:

- -1, pokud první sekvence porovná méně než druhou sekvenci.

- \+ 1, pokud druhá sekvence porovnává méně než první sekvence.

- 0, pokud jsou sekvence ekvivalentní.

### <a name="remarks"></a>Poznámky

Členská funkce se efektivně spustí:

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

## <a name="op_eq_eq"></a>locale:: operator = = – operátor

Testuje dvě národní prostředí na rovnost.

```cpp
bool operator==(const locale& right) const;
```

### <a name="parameters"></a>Parametry

*pravé*\
Jedna z národních prostředí, která mají být testována pro rovnost.

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která má **hodnotu true** , pokud jsou místní kopie stejného národního prostředí. Je **false** , pokud nejsou místní kopie stejného národního prostředí.

### <a name="remarks"></a>Poznámky

Dvě národní prostředí se rovnají, pokud se shodují se stejným národním prostředím, pokud je jedna z kopií druhé, nebo pokud mají stejné názvy.

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

[\<> národního prostředí](../standard-library/locale.md)\
[Znakové stránky](../c-runtime-library/code-pages.md)\
[Názvy národních prostředí, jazyky a řetězce země/oblasti](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
