---
title: "moneypunct – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocmon/std::moneypunct
- xlocmon/std::moneypunct::char_type
- xlocmon/std::moneypunct::string_type
- xlocmon/std::moneypunct::curr_symbol
- xlocmon/std::moneypunct::decimal_point
- xlocmon/std::moneypunct::do_curr_symbol
- xlocmon/std::moneypunct::do_decimal_point
- xlocmon/std::moneypunct::do_frac_digits
- xlocmon/std::moneypunct::do_grouping
- xlocmon/std::moneypunct::do_neg_format
- xlocmon/std::moneypunct::do_negative_sign
- xlocmon/std::moneypunct::do_pos_format
- xlocmon/std::moneypunct::do_positive_sign
- xlocmon/std::moneypunct::do_thousands_sep
- xlocmon/std::moneypunct::frac_digits
- xlocmon/std::moneypunct::grouping
- xlocmon/std::moneypunct::neg_format
- xlocmon/std::moneypunct::negative_sign
- xlocmon/std::moneypunct::pos_format
- xlocmon/std::moneypunct::positive_sign
- xlocmon/std::moneypunct::thousands_sep
dev_langs: C++
helpviewer_keywords:
- std::moneypunct [C++]
- std::moneypunct [C++], char_type
- std::moneypunct [C++], string_type
- std::moneypunct [C++], curr_symbol
- std::moneypunct [C++], decimal_point
- std::moneypunct [C++], do_curr_symbol
- std::moneypunct [C++], do_decimal_point
- std::moneypunct [C++], do_frac_digits
- std::moneypunct [C++], do_grouping
- std::moneypunct [C++], do_neg_format
- std::moneypunct [C++], do_negative_sign
- std::moneypunct [C++], do_pos_format
- std::moneypunct [C++], do_positive_sign
- std::moneypunct [C++], do_thousands_sep
- std::moneypunct [C++], frac_digits
- std::moneypunct [C++], grouping
- std::moneypunct [C++], neg_format
- std::moneypunct [C++], negative_sign
- std::moneypunct [C++], pos_format
- std::moneypunct [C++], positive_sign
- std::moneypunct [C++], thousands_sep
ms.assetid: cf2650da-3e6f-491c-95d5-23e57f582ee6
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 569aa946ac324c833e651e6b9b74b8cc402a4d04
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="moneypunct-class"></a>moneypunct – třída
Šablony třídy popisuje objekt, který může sloužit jako národní prostředí omezující vlastnost k popisu pořadí typu `CharType` představovat peněžní vstupní pole nebo pole peněžní výstup. Pokud parametr šablony `Intl` je `true`, je možné vysledovat mezinárodními smlouvami.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class CharType, bool Intl>  
class moneypunct;  
```  
  
#### <a name="parameters"></a>Parametry  
 `CharType`  
 Typ používaný v rámci programu ke kódování znaků.  
  
 `Intl`  
 Příznak určující, zda je třeba dodržovat mezinárodní konvence.  
  
## <a name="remarks"></a>Poznámky  
 Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. Ukládá jedinečné kladnou hodnotu v první pokus o přístup k jeho uložené hodnoty **id.**  
  
 Const mezinárodní statický objekt ukládá hodnotu parametru šablony **mezinárodní**.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[moneypunct –](#moneypunct)|Konstruktor objekty typu `moneypunct`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type –](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|  
|[STRING_TYPE](#string_type)|Typ, který popisuje řetězec obsahující znaky typu `CharType`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[curr_symbol –](#curr_symbol)|Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol měny.|  
|[decimal_point –](#decimal_point)|Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol desetinné čárky.|  
|[do_curr_symbol –](#do_curr_symbol)|Chráněná virtuální členská funkce, která vrátí sekvenci prvků specifickou pro národní prostředí, která se použije jako symbol měny.|  
|[do_decimal_point –](#do_decimal_point)|Chráněná virtuální členská funkce, která je volána k vrácení sekvence prvků specifických pro národní prostředí, která se použije jako symbol desetinné čárky.|  
|[do_frac_digits –](#do_frac_digits)|Chráněná virtuální členská funkce, která vrátí počet číslic specifický pro národní prostředí, který se zobrazí vpravo od každé desetinné čárky.|  
|[do_grouping –](#do_grouping)|Chráněná virtuální členská funkce, která vrátí pravidlo specifické pro národní prostředí k určení způsobu seskupení číslic vlevo od desetinné čárky.|  
|[do_neg_format –](#do_neg_format)|Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí pro formátování výstupů se zápornými částkami.|  
|[do_negative_sign –](#do_negative_sign)|Chráněná virtuální členská funkce, která je volána k vrácení sekvence prvků specifických pro národní prostředí, která se použije jako symbol záporného znaménka.|  
|[do_pos_format –](#do_pos_format)|Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí pro formátování výstupů s kladnými částkami.|  
|[do_positive_sign –](#do_positive_sign)|Chráněná virtuální členská funkce, která je volána k vrácení sekvence prvků specifických pro národní prostředí, která se použije jako symbol kladného znaménka.|  
|[do_thousands_sep –](#do_thousands_sep)|Chráněná virtuální členská funkce, která je volána k vrácení sekvence prvků specifických pro národní prostředí, která se použije jako symbol oddělovače tisíců.|  
|[frac_digits –](#frac_digits)|Vrátí počet číslic specifický pro národní prostředí, který se zobrazí vpravo od každé desetinné čárky.|  
|[seskupení](#grouping)|Vrátí pravidlo specifické pro národní prostředí určující způsob seskupení číslic nalevo od desetinné čárky.|  
|[neg_format –](#neg_format)|Vrátí pravidlo specifické pro národní prostředí pro formátování výstupů se zápornými částkami.|  
|[negative_sign –](#negative_sign)|Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol záporného znaménka.|  
|[pos_format –](#pos_format)|Vrátí pravidlo specifické pro národní prostředí pro formátování výstupů s kladnými částkami.|  
|[positive_sign –](#positive_sign)|Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol kladného znaménka.|  
|[thousands_sep –](#thousands_sep)|Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol oddělovače tisíců.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<národní prostředí >  
  
 **Namespace:** – std  
  
##  <a name="char_type"></a>moneypunct::char_type  
 Typ, který se používá k popisu znaku používaného národním prostředním.  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **CharType**.  
  
##  <a name="curr_symbol"></a>moneypunct::curr_symbol  
 Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol měny.  
  
```  
string_type curr_symbol() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Řetězec obsahující symbolu měny.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_curr_symbol –](#do_curr_symbol).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// moneypunct_curr_symbol.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const moneypunct < char, true > &mpunct = use_facet < moneypunct < char, true > >(loc);  
   cout << loc.name( ) << " international currency symbol "<<  mpunct.curr_symbol( ) << endl;  
  
   const moneypunct < char, false> &mpunct2 = use_facet < moneypunct < char, false> >(loc);  
   cout << loc.name( ) << " domestic currency symbol "<<  mpunct2.curr_symbol( ) << endl;  
};  
```  
  
##  <a name="decimal_point"></a>moneypunct::decimal_point  
 Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol desetinné čárky.  
  
```  
CharType decimal_point() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Specifické pro národní prostředí pořadí prvků, které chcete použít jako symbol desetinné čárky.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_decimal_point –](#do_decimal_point).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// moneypunct_decimal_pt.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc("german_germany");  
  
   const moneypunct < char, true > &mpunct = use_facet   
      < moneypunct < char, true > >(loc);  
   cout << loc.name( ) << " international decimal point "  
        << mpunct.decimal_point( ) << endl;  
  
   const moneypunct < char, false> &mpunct2 = use_facet   
      < moneypunct < char, false> >(loc);  
   cout << loc.name( ) << " domestic decimal point "  
        << mpunct2.decimal_point( ) << endl;  
}  
```  
  
```Output  
German_Germany.1252 international decimal point ,  
German_Germany.1252 domestic decimal point ,  
```  
  
##  <a name="do_curr_symbol"></a>moneypunct::do_curr_symbol  
 Chráněná virtuální členská funkce, která vrátí sekvenci prvků specifickou pro národní prostředí, která se použije jako symbol měny.  
  
```  
virtual string_type do_curr_symbol() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Specifické pro národní prostředí pořadí prvků, které chcete použít jako symbol desetinné čárky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [curr_symbol –](#curr_symbol), kde je volána funkce člena virtuální `curr_symbol`.  
  
##  <a name="do_decimal_point"></a>moneypunct::do_decimal_point  
 Chráněný člen virtuální funkce, která vrátí specifická pro národní prostředí pořadí prvků, které chcete použít jako symbol desetinné čárky.  
  
```  
virtual CharType do_decimal_point() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Specifické pro národní prostředí pořadí prvků, které chcete použít jako symbol desetinné čárky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [decimal_point –](#decimal_point), kde je volána funkce člena virtuální `decimal_point`.  
  
##  <a name="do_frac_digits"></a>moneypunct::do_frac_digits  
 Chráněný člen virtuální funkce, která vrátí počet specifická pro národní prostředí počet číslic zobrazíte napravo od všech desetinné čárky.  
  
```  
virtual int do_frac_digits() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Národní prostředí konkrétní počet počet číslic zobrazíte napravo od všech desetinné čárky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [frac_digits –](#frac_digits), kde je volána funkce člena virtuální `frac_digits`.  
  
##  <a name="do_grouping"></a>moneypunct::do_grouping  
 Chráněný člen virtuální funkce, která vrátí pravidlo specifické pro národní prostředí pro určení, jak jsou seskupené číslic nalevo od všech desetinné čárky.  
  
```  
virtual string do_grouping() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pravidlo specifické pro národní prostředí pro určení, jak jsou seskupené číslic nalevo od všech desetinné čárky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [seskupení](#grouping), kde je volána funkce člena virtuální **seskupení**.  
  
##  <a name="do_neg_format"></a>moneypunct::do_neg_format  
 Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí pro formátování výstupů se zápornými částkami.  
  
```  
virtual pattern do_neg_format() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Chráněný člen virtuální funkce vrátí hodnotu pravidlo specifické pro národní prostředí pro určení způsobu generování peněžní výstup pole pro zápornou hodnotu. Všechny čtyři elementů **pattern::field** může mít hodnoty:  
  
- **žádný** odpovídat počtu nula či více mezery nebo nic vygenerování.  
  
- **přihlašovací** odpovídat nebo vygenerování znaménkem kladné a záporné.  
  
- **místo** odpovídat počtu nula či více mezery nebo vygenerování mezerou.  
  
- **symbol** odpovídat nebo vygenerování symbolu měny.  
  
- **Hodnota** odpovídat nebo vygenerování peněžní hodnota.  
  
 Součásti peněžní výstup pole jsou generovány a součástí peněžní vstupní pole se splní v pořadí, v němž jsou tyto prvky v **pattern::field**. Každá z hodnot **přihlašovací**, **symbol**, **hodnotu**a buď **žádné** nebo **místo** potřeba je zadat přesně jednou. Hodnota **žádné** nesmí zobrazit jako první. Místo na hodnotu **musí** nezobrazí první nebo poslední. Pokud **mezinárodní** má hodnotu true, je pořadí **symbol**, **přihlašovací**, **žádné**, pak **hodnotu**.  
  
 Verze šablony `moneypunct` \< **CharType**, **mezinárodní**> vrátí `{` **money_base::symbol**, **money_ Base::Sign**, **money_base::value**, **money_base::none**`}`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [neg_format –](#neg_format), kde je volána funkce člena virtuální `neg_format`.  
  
##  <a name="do_negative_sign"></a>moneypunct::do_negative_sign  
 Chráněná virtuální členská funkce, která je volána k vrácení sekvence prvků specifických pro národní prostředí, která se použije jako symbol záporného znaménka.  
  
```  
virtual string_type do_negative_sign() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Specifické pro národní prostředí pořadí prvků, které chcete použít jako záporné znaménko.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [negative_sign –](#negative_sign), kde je volána funkce člena virtuální `negative_sign`.  
  
##  <a name="do_pos_format"></a>moneypunct::do_pos_format  
 Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí pro formátování výstupů s kladnými částkami.  
  
```  
virtual pattern do_pos_format() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Chráněný člen virtuální funkce vrátí hodnotu pravidlo specifické pro národní prostředí pro určení způsobu generování peněžní výstup pole pro kladnou hodnotu. (Také určuje, jak tak, aby odpovídaly součástí peněžní vstupní pole.) Kódování je stejný jako u [do_neg_format –](#do_neg_format).  
  
 Verze šablony moneypunct\< **CharType**, **Inputlterator**> vrátí `{` **money_base::symbol**, **peníze _base::Sign**, **money_base::value**, **money_base::none**`}`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [pos_format –](#pos_format), kde je volána funkce člena virtuální `pos_format`.  
  
##  <a name="do_positive_sign"></a>moneypunct::do_positive_sign  
 Chráněný člen virtuální funkce, která vrátí specifická pro národní prostředí pořadí prvků, které chcete použít jako kladné znaménko.  
  
```  
virtual string_type do_positive_sign() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Specifické pro národní prostředí pořadí prvků, které chcete použít jako kladné znaménko.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [positive_sign –](#positive_sign), kde je volána funkce člena virtuální `positive_sign`.  
  
##  <a name="do_thousands_sep"></a>moneypunct::do_thousands_sep  
 Chráněný člen virtuální funkce, která vrátí element specifická pro národní prostředí pro použití jako oddělovač skupin nalevo od všech desetinné čárky.  
  
```  
virtual CharType do_thousands_sep() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Element specifická pro národní prostředí pro použití jako oddělovač skupin nalevo od všech desetinné čárky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [thousands_sep –](#thousands_sep), kde je volána funkce člena virtuální `thousands_sep`.  
  
##  <a name="frac_digits"></a>moneypunct::frac_digits  
 Vrátí počet číslic specifický pro národní prostředí, který se zobrazí vpravo od každé desetinné čárky.  
  
```  
int frac_digits() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Národní prostředí konkrétní počet počet číslic zobrazíte napravo od všech desetinné čárky.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_frac_digits –](#do_frac_digits).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// moneypunct_frac_digits.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const moneypunct <char, true> &mpunct =   
       use_facet <moneypunct <char, true> >(loc);  
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )  
   {  
      cout << loc.name( ) << " international grouping:\n the "  
           << i <<"th group to the left of the radix character "  
           << "is of size " << (int)(mpunct.grouping ( )[i])   
           << endl;  
   }  
   cout << loc.name( ) << " international frac_digits\n to the right"  
        << " of the radix character: "  
        << mpunct.frac_digits ( ) << endl << endl;  
  
   const moneypunct <char, false> &mpunct2 =   
       use_facet <moneypunct <char, false> >(loc);  
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )  
   {  
      cout << loc.name( ) << " domestic grouping:\n the "  
           << i <<"th group to the left of the radix character "  
           << "is of size " << (int)(mpunct2.grouping ( )[i])   
           << endl;  
   }  
   cout << loc.name( ) << " domestic frac_digits\n to the right"  
        << " of the radix character: "  
        << mpunct2.frac_digits ( ) << endl << endl;  
}  
```  
  
```Output  
German_Germany.1252 international grouping:  
 the 0th group to the left of the radix character is of size 3  
German_Germany.1252 international frac_digits  
 to the right of the radix character: 2  
  
German_Germany.1252 domestic grouping:  
 the 0th group to the left of the radix character is of size 3  
German_Germany.1252 domestic frac_digits  
 to the right of the radix character: 2  
```  
  
##  <a name="grouping"></a>moneypunct::Grouping  
 Vrátí pravidlo specifické pro národní prostředí určující způsob seskupení číslic nalevo od desetinné čárky.  
  
```  
string grouping() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pravidlo specifické pro národní prostředí pro určení, jak jsou seskupené číslic nalevo od všech desetinné čárky.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_grouping –](#do_grouping).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// moneypunct_grouping.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const moneypunct <char, true> &mpunct =   
       use_facet <moneypunct <char, true> >( loc );  
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )  
   {  
      cout << loc.name( ) << " international grouping:\n the "  
           << i <<"th group to the left of the radix character "  
           << "is of size " << (int)(mpunct.grouping ( )[i])   
           << endl;  
   }  
   cout << loc.name( ) << " international frac_digits\n to the right"  
        << " of the radix character: "  
        << mpunct.frac_digits ( ) << endl << endl;  
  
   const moneypunct <char, false> &mpunct2 =   
       use_facet <moneypunct <char, false> >( loc );  
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )  
   {  
      cout << loc.name( ) << " domestic grouping:\n the "  
           << i <<"th group to the left of the radix character "  
           << "is of size " << (int)(mpunct2.grouping ( )[i])   
           << endl;  
   }  
   cout << loc.name( ) << " domestic frac_digits\n to the right"  
        << " of the radix character: "  
        << mpunct2.frac_digits ( ) << endl << endl;  
}  
```  
  
```Output  
German_Germany.1252 international grouping:  
 the 0th group to the left of the radix character is of size 3  
German_Germany.1252 international frac_digits  
 to the right of the radix character: 2  
  
German_Germany.1252 domestic grouping:  
 the 0th group to the left of the radix character is of size 3  
German_Germany.1252 domestic frac_digits  
 to the right of the radix character: 2  
```  
  
##  <a name="moneypunct"></a>moneypunct::moneypunct  
 Konstruktor objekty typu `moneypunct`.  
  
```  
explicit moneypunct(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `_Refs`  
 Celočíselná hodnota určuje typ správy paměti pro objekt.  
  
### <a name="remarks"></a>Poznámky  
 Možné hodnoty `_Refs` parametrů a jejich významu jsou:  
  
-   0: doba života objektu spravuje národní prostředí, které je obsahují.  
  
-   1: doba života objektu, se musí ručně spravovat.  
  
-   \>1: tyto hodnoty nejsou definovány.  
  
 Žádné přímé příklady je možné, protože je chráněn destruktoru.  
  
 Konstruktor inicializuje jeho základní objekt s [locale::facet](../standard-library/locale-class.md#facet_class)(_ *odolný systém souborů*).  
  
##  <a name="neg_format"></a>moneypunct::neg_format  
 Vrátí pravidlo specifické pro národní prostředí pro formátování výstupů se zápornými částkami.  
  
```  
pattern neg_format() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pravidlo specifické pro národní prostředí pro formátování výstupy s záporné.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_neg_format –](#do_neg_format).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// moneypunct_neg_format.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
  
using namespace std;  
  
int main( ) {  
   locale loc( "german_germany" );  
  
   const moneypunct <char, true> &mpunct =   
      use_facet <moneypunct <char, true > >(loc);  
   cout << loc.name( ) << " international negative number format: "  
        << mpunct.neg_format( ).field[0]   
        << mpunct.neg_format( ).field[1]   
        << mpunct.neg_format( ).field[2]   
        << mpunct.neg_format( ).field[3] << endl;  
  
   const moneypunct <char, false> &mpunct2 =   
      use_facet <moneypunct <char, false> >(loc);  
   cout << loc.name( ) << " domestic negative number format: "  
        << mpunct2.neg_format( ).field[0]   
        << mpunct2.neg_format( ).field[1]   
        << mpunct2.neg_format( ).field[2]   
        << mpunct2.neg_format( ).field[3] << endl;  
}  
```  
  
##  <a name="negative_sign"></a>moneypunct::negative_sign  
 Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol záporného znaménka.  
  
```  
string_type negative_sign() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol záporného znaménka.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_negative_sign –](#do_negative_sign).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// moneypunct_neg_sign.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
  
using namespace std;  
  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const moneypunct <char, true> &mpunct =   
      use_facet <moneypunct <char, true> >(loc);  
   cout << loc.name( ) << " international negative sign: "  
        << mpunct.negative_sign( ) << endl;  
  
   const moneypunct <char, false> &mpunct2 =   
      use_facet <moneypunct <char, false> >(loc);  
   cout << loc.name( ) << " domestic negative sign: "  
        << mpunct2.negative_sign( ) << endl;  
  
   locale loc2( "French" );  
  
   const moneypunct <char, true> &mpunct3 =   
      use_facet <moneypunct <char, true> >(loc2);  
   cout << loc2.name( ) << " international negative sign: "  
        << mpunct3.negative_sign( ) << endl;  
  
   const moneypunct <char, false> &mpunct4 =   
      use_facet <moneypunct <char, false> >(loc2);  
   cout << loc2.name( ) << " domestic negative sign: "  
        << mpunct4.negative_sign( ) << endl;  
};  
```  
  
```Output  
German_Germany.1252 international negative sign: -  
German_Germany.1252 domestic negative sign: -  
French_France.1252 international negative sign: -  
French_France.1252 domestic negative sign: -  
```  
  
##  <a name="pos_format"></a>moneypunct::pos_format  
 Vrátí pravidlo specifické pro národní prostředí pro formátování výstupů s kladnými částkami.  
  
```  
pattern pos_format() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pravidlo specifické pro národní prostředí pro formátování výstupy s kladné objemy.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_pos_format –](#do_pos_format).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// moneypunct_pos_format.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
  
using namespace std;  
  
int main() {  
   locale loc( "german_germany" );  
  
   const moneypunct <char, true> &mpunct =   
      use_facet <moneypunct <char, true> >(loc);  
   cout << loc.name( ) << " international positive number format: "  
        << mpunct.pos_format( ).field[0]   
        << mpunct.pos_format( ).field[1]   
        << mpunct.pos_format( ).field[2]   
        << mpunct.pos_format( ).field[3] << endl;  
  
   const moneypunct <char, false> &mpunct2 =   
      use_facet <moneypunct <char, false> >(loc);  
   cout << loc.name( ) << " domestic positive number format: "  
        << mpunct2.pos_format( ).field[0]   
        << mpunct2.pos_format( ).field[1]   
        << mpunct2.pos_format( ).field[2]   
        << mpunct2.pos_format( ).field[3] << endl;  
}  
```  
  
##  <a name="positive_sign"></a>moneypunct::positive_sign  
 Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol kladného znaménka.  
  
```  
string_type positive_sign() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Specifické pro národní prostředí pořadí elementů, které chcete použít jako symbol kladné znaménko.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_positive_sign –](#do_positive_sign).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// moneypunct_pos_sign.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
  
using namespace std;  
  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const moneypunct <char, true> &mpunct =   
      use_facet <moneypunct <char, true > >(loc);  
   cout << loc.name( ) << " international positive sign:"  
        << mpunct.positive_sign( ) << endl;  
  
   const moneypunct <char, false> &mpunct2 =   
      use_facet <moneypunct <char, false> >(loc);  
   cout << loc.name( ) << " domestic positive sign:"  
        << mpunct2.positive_sign( ) << endl;  
  
   locale loc2( "French" );  
  
   const moneypunct <char, true> &mpunct3 =   
      use_facet <moneypunct <char, true> >(loc2);  
   cout << loc2.name( ) << " international positive sign:"  
        << mpunct3.positive_sign( ) << endl;  
  
   const moneypunct <char, false> &mpunct4 =   
      use_facet <moneypunct <char, false> >(loc2);  
   cout << loc2.name( ) << " domestic positive sign:"  
        << mpunct4.positive_sign( ) << endl;  
};  
```  
  
```Output  
German_Germany.1252 international positive sign:  
German_Germany.1252 domestic positive sign:  
French_France.1252 international positive sign:  
French_France.1252 domestic positive sign:  
```  
  
##  <a name="string_type"></a>moneypunct::STRING_TYPE  
 Typ, který popisuje řetězec obsahující znaky typu **CharType**.  
  
```  
typedef basic_string<CharType, Traits, Allocator> string_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [basic_string](../standard-library/basic-string-class.md) jejichž objekty může ukládat kopie pořadí interpunkce.  
  
##  <a name="thousands_sep"></a>moneypunct::thousands_sep  
 Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol oddělovače tisíců.  
  
```  
CharType thousands_sep() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Specifické pro národní prostředí pořadí prvků, které chcete použít jako tisíců oddělovače  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_thousands_sep –](#do_thousands_sep).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// moneypunct_thou_sep.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const moneypunct <char, true> &mpunct =   
       use_facet <moneypunct <char, true > >(loc);  
   cout << loc.name( ) << " international thousands separator: "  
        << mpunct.thousands_sep( ) << endl;  
  
   const moneypunct <char, false> &mpunct2 =   
      use_facet <moneypunct <char, false> >(loc);  
   cout << loc.name( ) << " domestic thousands separator: "  
        << mpunct2.thousands_sep( ) << endl << endl;  
  
   locale loc2( "english_canada" );  
  
   const moneypunct <char, true> &mpunct3 =   
       use_facet <moneypunct <char, true> >(loc2);  
   cout << loc2.name( ) << " international thousands separator: "  
        << mpunct3.thousands_sep( ) << endl;  
  
   const moneypunct <char, false> &mpunct4 =   
      use_facet <moneypunct <char, false> >(loc2);  
   cout << loc2.name( ) << " domestic thousands separator: "  
        << mpunct4.thousands_sep( ) << endl;  
}  
```  
  
```Output  
German_Germany.1252 international thousands separator: .  
German_Germany.1252 domestic thousands separator: .  
  
English_Canada.1252 international thousands separator: ,  
English_Canada.1252 domestic thousands separator: ,  
```  
  
## <a name="see-also"></a>Viz také  
 [\<národní prostředí >](../standard-library/locale.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

