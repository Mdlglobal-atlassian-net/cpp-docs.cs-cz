---
title: "numpunct – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocnum/std::numpunct
- xlocnum/std::numpunct::char_type
- xlocnum/std::numpunct::string_type
- xlocnum/std::numpunct::decimal_point
- xlocnum/std::numpunct::do_decimal_point
- xlocnum/std::numpunct::do_falsename
- xlocnum/std::numpunct::do_grouping
- xlocnum/std::numpunct::do_thousands_sep
- xlocnum/std::numpunct::do_truename
- xlocnum/std::numpunct::falsename
- xlocnum/std::numpunct::grouping
- xlocnum/std::numpunct::thousands_sep
- xlocnum/std::numpunct::truename
dev_langs: C++
helpviewer_keywords:
- std::numpunct [C++]
- std::numpunct [C++], char_type
- std::numpunct [C++], string_type
- std::numpunct [C++], decimal_point
- std::numpunct [C++], do_decimal_point
- std::numpunct [C++], do_falsename
- std::numpunct [C++], do_grouping
- std::numpunct [C++], do_thousands_sep
- std::numpunct [C++], do_truename
- std::numpunct [C++], falsename
- std::numpunct [C++], grouping
- std::numpunct [C++], thousands_sep
- std::numpunct [C++], truename
ms.assetid: 73fb93cc-ac11-4c98-987c-bfa6267df596
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7cd59fec5d8b5b2a6a05634242e0506688422f81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="numpunct-class"></a>numpunct – třída
Třídu šablony, která popisuje objekt, který může sloužit jako místní omezující vlastnosti pro popis pořadí typu `CharType` používá k reprezentování informace o formátování a interpunkce výrazy číselné a logická hodnota.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class CharType>  
class numpunct : public locale::facet;  
```  
  
#### <a name="parameters"></a>Parametry  
 `CharType`  
 Typ používaný v rámci programu ke kódování znaků v národním prostředí.  
  
## <a name="remarks"></a>Poznámky  
 Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. Ukládá jedinečné kladnou hodnotu v první pokus o přístup k jeho uložené hodnoty **id.**  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[numpunct –](#numpunct)|V konstruktoru pro objekty typu `numpunct`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type –](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|  
|[STRING_TYPE](#string_type)|Typ, který popisuje řetězec obsahující znaky typu `CharType`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[decimal_point –](#decimal_point)|Vrátí prvek specifický pro národní prostředí, který se použije jako desetinná čárka.|  
|[do_decimal_point –](#do_decimal_point)|Chráněná virtuální členská funkce, která je volána k vrácení prvku specifického pro národní prostředí, který se použije jako desetinná čárka.|  
|[do_falsename –](#do_falsename)|Chráněný člen virtuální funkce, která je volána vrátit řetězec, který bude použit jako textovou reprezentaci hodnoty A `false`.|  
|[do_grouping –](#do_grouping)|Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí k určení způsobu seskupení číslic vlevo od desetinné čárky.|  
|[do_thousands_sep –](#do_thousands_sep)|Chráněná virtuální členská funkce, která je volána k vrácení prvku specifického pro národní prostředí, který se použije jako oddělovač tisíců.|  
|[do_truename –](#do_truename)|Chráněný člen virtuální funkce, která je volána vrátit řetězec, který bude použit jako textovou reprezentaci hodnoty A `true`.|  
|[falsename –](#falsename)|Vrátí řetězec, který bude použit jako textovou reprezentaci hodnoty `false`.|  
|[seskupení](#grouping)|Vrátí pravidlo specifické pro národní prostředí určující způsob seskupení číslic nalevo od desetinné čárky.|  
|[thousands_sep –](#thousands_sep)|Vrátí prvek specifický pro národní prostředí, který se použije jako oddělovač tisíců.|  
|[truename –](#truename)|Vrátí řetězec, který bude použit jako textovou reprezentaci hodnoty `true`.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<národní prostředí >  
  
 **Namespace:** – std  
  
##  <a name="char_type"></a>numpunct::char_type  
 Typ, který se používá k popisu znaku používaného národním prostředním.  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **CharType.**  
  
##  <a name="decimal_point"></a>numpunct::decimal_point  
 Vrátí prvek specifický pro národní prostředí, který se použije jako desetinná čárka.  
  
```  
CharType decimal_point() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Element specifická pro národní prostředí pro použití jako desetinné čárky.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_decimal_point –](#do_decimal_point).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// numpunct_decimal_point.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const numpunct <char> &npunct =   
   use_facet <numpunct <char> >( loc);  
   cout << loc.name( ) << " decimal point "<<   
   npunct.decimal_point( ) << endl;  
   cout << loc.name( ) << " thousands separator "   
   << npunct.thousands_sep( ) << endl;  
};  
```  
  
```Output  
German_Germany.1252 decimal point ,  
German_Germany.1252 thousands separator .  
```  
  
##  <a name="do_decimal_point"></a>numpunct::do_decimal_point  
 Chráněná virtuální členská funkce, která je volána k vrácení prvku specifického pro národní prostředí, který se použije jako desetinná čárka.  
  
```  
virtual CharType do_decimal_point() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Element specifická pro národní prostředí pro použití jako desetinné čárky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [decimal_point –](#decimal_point), kde je volána funkce člena virtuální `decimal_point`.  
  
##  <a name="do_falsename"></a>numpunct::do_falsename  
 Chráněný člen virtuální funkce vrátí hodnotu pořadí, které chcete použít jako textovou reprezentaci hodnoty **false**.  
  
```  
virtual string_type do_falsename() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Řetězec obsahující pořadí, které chcete použít jako textovou reprezentaci hodnoty **false**.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí řetězec "false" představují hodnotu **false** ve všech národních prostředí.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [falsename –](#falsename), kde je volána funkce člena virtuální `falsename`.  
  
##  <a name="do_grouping"></a>numpunct::do_grouping  
 Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí k určení způsobu seskupení číslic vlevo od desetinné čárky.  
  
```  
virtual string do_grouping() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pravidlo specifické pro národní prostředí pro určení, jak jsou seskupené číslic nalevo od všech desetinné čárky.  
  
### <a name="remarks"></a>Poznámky  
 Chráněná virtuální členská funkce, která vrátí pravidlo specifické pro národní prostředí k určení způsobu seskupení číslic vlevo od desetinné čárky. Kódování je stejný jako u **lconv::grouping**.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [seskupení](#grouping), kde je volána funkce člena virtuální **seskupení**.  
  
##  <a name="do_thousands_sep"></a>numpunct::do_thousands_sep  
 Chráněná virtuální členská funkce, která je volána k vrácení prvku specifického pro národní prostředí, který se použije jako oddělovač tisíců.  
  
```  
virtual CharType do_thousands_sep() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí prvek specifický pro národní prostředí, který se použije jako oddělovač tisíců.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce vrátí specifická pro národní prostředí element typu **CharType** chcete použít jako oddělovač skupin nalevo od všech desetinné čárky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [thousands_sep –](#thousands_sep), kde je volána funkce člena virtuální `thousands_sep`.  
  
##  <a name="do_truename"></a>numpunct::do_truename  
 Chráněný člen virtuální funkce, která je volána vrátit řetězec, který bude použit jako textovou reprezentaci hodnoty A **true**.  
  
```  
virtual string_type do_truename() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Řetězec, který chcete použít jako textovou reprezentaci hodnoty **true**.  
  
 Všechna národní prostředí vrátí řetězec "true" představující hodnotu **true**.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [truename –](#truename), kde je volána funkce člena virtuální `truename`.  
  
##  <a name="falsename"></a>numpunct::falsename  
 Vrátí řetězec, který bude použit jako textovou reprezentaci hodnoty **false**.  
  
```  
string_type falsename() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Řetězec obsahující posloupnost **CharType**s chcete použít jako textovou reprezentaci hodnoty **false**.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí řetězec "false" představují hodnotu **false** ve všech národních prostředí.  
  
 Členské funkce vrátí hodnotu [do_falsename –](#do_falsename).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// numpunct_falsename.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "English" );  
  
   const numpunct <char> &npunct = use_facet <numpunct <char> >( loc );  
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;  
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;  
  
   locale loc2( "French" );  
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >(loc2);  
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;  
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;  
}  
```  
  
```Output  
English_United States.1252 truename true  
English_United States.1252 falsename false  
French_France.1252 truename true  
French_France.1252 falsename false  
```  
  
##  <a name="grouping"></a>numpunct::Grouping  
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
// numpunct_grouping.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany");  
  
   const numpunct <char> &npunct =   
       use_facet < numpunct <char> >( loc );  
   for (unsigned int i = 0; i < npunct.grouping( ).length( ); i++)  
   {  
      cout << loc.name( ) << " international grouping:\n the "  
           << i <<"th group to the left of the radix character "  
           << "is of size " << (int)(npunct.grouping ( )[i])   
           << endl;  
   }  
}  
```  
  
```Output  
German_Germany.1252 international grouping:  
 the 0th group to the left of the radix character is of size 3  
```  
  
##  <a name="numpunct"></a>numpunct::numpunct  
 V konstruktoru pro objekty typu `numpunct`.  
  
```  
explicit numpunct(size_t _Refs = 0);
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
  
 Konstruktor inicializuje jeho základní objekt s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)( `_Refs`).  
  
##  <a name="string_type"></a>numpunct::STRING_TYPE  
 Typ, který popisuje řetězec obsahující znaky typu **CharType**.  
  
```  
typedef basic_string<CharType, Traits, Allocator> string_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [basic_string](../standard-library/basic-string-class.md) jejichž objekty může ukládat kopie pořadí interpunkce.  
  
##  <a name="thousands_sep"></a>numpunct::thousands_sep  
 Vrátí prvek specifický pro národní prostředí, který se použije jako oddělovač tisíců.  
  
```  
CharType thousands_sep() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Element specifická pro národní prostředí pro použití jako tisíců oddělovače.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_thousands_sep –](#do_thousands_sep).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// numpunct_thou_sep.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const numpunct <char> &npunct =   
   use_facet < numpunct < char > >( loc );  
   cout << loc.name( ) << " decimal point "<<   
   npunct.decimal_point( ) << endl;  
   cout << loc.name( ) << " thousands separator "   
   << npunct.thousands_sep( ) << endl;  
};  
```  
  
```Output  
German_Germany.1252 decimal point ,  
German_Germany.1252 thousands separator .  
```  
  
##  <a name="truename"></a>numpunct::truename  
 Vrátí řetězec, který bude použit jako textovou reprezentaci hodnoty **true**.  
  
```  
string_type falsename() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Řetězec, který chcete použít jako textovou reprezentaci hodnoty **true**.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_truename –](#do_truename).  
  
 Všechna národní prostředí vrátí řetězec "true" představující hodnotu **true**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// numpunct_truename.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "English" );  
  
   const numpunct < char> &npunct = use_facet <numpunct <char> >( loc );  
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;  
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;  
  
   locale loc2("French");  
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >( loc2 );  
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;  
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;  
}  
```  
  
```Output  
English_United States.1252 truename true  
English_United States.1252 falsename false  
French_France.1252 truename true  
French_France.1252 falsename false  
```  
  
## <a name="see-also"></a>Viz také  
 [\<národní prostředí >](../standard-library/locale.md)   
 [facet – třída](../standard-library/locale-class.md#facet_class)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

