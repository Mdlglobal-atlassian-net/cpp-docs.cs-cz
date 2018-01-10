---
title: "money_put – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocmon/std::money_put
- xlocmon/std::money_put::char_type
- xlocmon/std::money_put::iter_type
- xlocmon/std::money_put::string_type
- xlocmon/std::money_put::do_put
- xlocmon/std::money_put::put
dev_langs: C++
helpviewer_keywords:
- std::money_put [C++]
- std::money_put [C++], char_type
- std::money_put [C++], iter_type
- std::money_put [C++], string_type
- std::money_put [C++], do_put
- std::money_put [C++], put
ms.assetid: f439fd56-c9b1-414c-95e1-66c918c6eee6
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bd47afe55f1e2625dfe216afd6ef98cbcba7b21f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="moneyput-class"></a>money_put – třída
Šablony třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převody hodnot peněžní pořadí typu `CharType`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class CharType,  
    class OutputIterator = ostreambuf_iterator<CharType>>  
class money_put : public locale::facet;  
```  
  
#### <a name="parameters"></a>Parametry  
 `CharType`  
 Typ používaný v rámci programu ke kódování znaků v národním prostředí.  
  
 `OutputIterator`  
 Typ iterátoru, do kterého finanční funkce zapisují svůj výstup.  
  
## <a name="remarks"></a>Poznámky  
 Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. Ukládá jedinečné kladnou hodnotu v první pokus o přístup k jeho uložené hodnoty **id.**  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[money_put –](#money_put)|V konstruktoru pro objekty typu `money_put`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type –](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|  
|[iter_type –](#iter_type)|Typ, který popisuje výstupní iterátor.|  
|[STRING_TYPE](#string_type)|Typ, který popisuje řetězec obsahující znaky typu `CharType`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[do_put –](#do_put)|Virtuální funkce volaná k převodu buď čísla, nebo řetězce na sekvenci znaků, která představuje finanční hodnotu.|  
|[PUT](#put)|Převede buď číslo, nebo řetězec na sekvenci znaků, která představuje finanční hodnotu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<národní prostředí >  
  
 **Namespace:** – std  
  
##  <a name="char_type"></a>money_put::char_type  
 Typ, který se používá k popisu znaku používaného národním prostředním.  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **CharType**.  
  
##  <a name="do_put"></a>money_put::do_put  
 Virtuální funkce volaná k převodu buď čísla, nebo řetězce na sekvenci znaků, která představuje finanční hodnotu.  
  
```  
virtual iter_type do_put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,   
    const string_type& val) const;

 
virtual iter_type do_put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,  
    long double val) const;
```  
  
### <a name="parameters"></a>Parametry  
 `next`  
 Iterace adresování první prvek vložené řetězce.  
  
 `_Intl`  
 Logická hodnota označující typ symbolu měny v sekvenci byl očekáván: **true** pokud mezinárodní, **false** Pokud příslušné.  
  
 `_Iosbase`  
 Příznak formátu, který při sadu označuje, že symbolu měny je volitelná. jinak je požadováno  
  
 `_Fill`  
 Znak, který se používá k vytvoření mezer.  
  
 `val`  
 Objekt string má být převeden.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup vytváří jeden pozice za posledním elementem adresy.  
  
### <a name="remarks"></a>Poznámky  
 První virtuální chráněného člena funkce generuje sekvenční elementy začínající na `next` k vytvoření pole peněžní výstup z [string_type](#string_type) objekt `val`. Pořadí řízené `val` musí začínat jeden nebo více desetinných míst, volitelně znaménkem minus (-), které představují velikost. Funkce vrátí hodnotu iterovat určení první prvek nad rámec pole generovaný peněžní výstup.  
  
 Druhý virtuální chráněného člena funkce se chová stejně jako první, s výjimkou to efektivně první převede `val` pořadí čísel desítkové soustavy, volitelně před sebou znaménkem minus následně převádí tohoto pořadí jako výše.  
  
 Formát peněžní výstup pole je dáno [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class) fac (skutečná) volání vráceny [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **mezinárodní**>> ( **iosbase**. [getloc –](../standard-library/ios-base-class.md#getloc)).  
  
 Konkrétně:  
  
- **FAC**. [pos_format –](../standard-library/moneypunct-class.md#pos_format) určuje pořadí, ve které jsou součástí pole vygenerované nezáporná hodnota.  
  
- **FAC**. [neg_format –](../standard-library/moneypunct-class.md#neg_format) určuje pořadí, ve které jsou součástí pole vygenerované zápornou hodnotu.  
  
- **FAC**. [curr_symbol –](../standard-library/moneypunct-class.md#curr_symbol) určuje pořadí elementů generovat pro symbolu měny.  
  
- **FAC**. [positive_sign –](../standard-library/moneypunct-class.md#positive_sign) určuje pořadí elementů generovat pro kladné znaménko.  
  
- **FAC**. [negative_sign –](../standard-library/moneypunct-class.md#negative_sign) určuje pořadí elementů generovat pro znaménkem záporné.  
  
- **FAC**. [seskupování](../standard-library/moneypunct-class.md#grouping) určuje způsob seskupení číslic nalevo od všech desetinné čárky.  
  
- **FAC**. [thousands_sep –](../standard-library/moneypunct-class.md#thousands_sep) určuje element, který odděluje skupiny číslic nalevo od všech desetinné čárky.  
  
- **FAC**. [decimal_point –](../standard-library/moneypunct-class.md#decimal_point) určuje elementu, který odděluje číslic celé číslo od všech zlomek číslic.  
  
- **FAC**. [frac_digits –](../standard-library/moneypunct-class.md#frac_digits) určuje počet číslic významné zlomek napravo od všech desetinné čárky.  
  
 Pokud řetězec přihlašovací ( **fac**. `negative_sign`nebo **fac**. `positive_sign`) má více než jeden element pouze první prvek se vygeneruje kde rovna element **money_base::sign** se zobrazí ve formátu vzoru ( **fac**. `neg_format`nebo **fac**. `pos_format`). Všechny zbývající elementy jsou generovány na konci tohoto pole peněžní výstup.  
  
 Pokud **iosbase**. [příznaky](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) nenulový, řetězec **fac**. `curr_symbol`kde se vygeneruje rovna element **money_base::symbol** se zobrazí ve formátu vzoru. Jinak se generuje bez symbolu měny.  
  
 Pokud se nevyžaduje žádná omezení seskupení **fac**. **seskupování** (jeho první prvek má hodnotu char_max –), pak žádné instance **fac**. `thousands_sep`jsou generovány, v části hodnotu pole peněžní výstup (kde rovna element **money_base::value** se zobrazí ve formátu vzoru). Pokud **fac**. `frac_digits`je nulové pak žádné instance **fac**. `decimal_point`Generuje se po desetinných míst. Jinak hodnota pole výsledný výstup peněžní umístí nejnižší **fac**. `frac_digits`desetinných číslic vpravo od desetinné čárky.  
  
 Jako u jakékoli číselné výstup pole, s výjimkou, že pokud dojde k odsazení **iosbase**. **příznaky** & **iosbase**. [interní](../standard-library/ios-functions.md#internal) je nenulové hodnoty, všechny interní odsazení se vygeneruje kde rovna element **money_base::space** se zobrazí ve formátu vzoru, pokud se zobrazí. Interní odsazení, jinak dojde před generovaným pořadí. Znak odsazení je **výplně**.  
  
 Volání funkcí **iosbase**. **Šířka**(0) k šířce pole nastaven na hodnotu nula.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [put](#put), kde je volána funkce člena virtuální **put**.  
  
##  <a name="iter_type"></a>money_put::iter_type  
 Typ, který popisuje výstupní iterátor.  
  
```  
typedef OutputIterator iter_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **OutputIterator.**  
  
##  <a name="money_put"></a>money_put::money_put  
 V konstruktoru pro objekty typu `money_put`.  
  
```  
explicit money_put(size_t _Refs = 0);
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
  
##  <a name="put"></a>money_put::Put  
 Převede buď číslo, nebo řetězec na sekvenci znaků, která představuje finanční hodnotu.  
  
```  
iter_type put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,   
    const string_type& val) const;

 
iter_type put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,  
    long double val) const;
```  
  
### <a name="parameters"></a>Parametry  
 `next`  
 Iterace adresování první prvek vložené řetězce.  
  
 `_Intl`  
 Logická hodnota označující typ symbolu měny v sekvenci byl očekáván: **true** pokud mezinárodní, **false** Pokud příslušné.  
  
 `_Iosbase`  
 Příznak formátu, který při sadu označuje, že symbolu měny je volitelná. jinak je požadováno  
  
 `_Fill`  
 Znak, který se používá k vytvoření mezer.  
  
 `val`  
 Objekt string má být převeden.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup vytváří jeden pozice za posledním elementem adresy.  
  
### <a name="remarks"></a>Poznámky  
 Obě členské funkce vrátí [do_put –](#do_put)( `next`, `_Intl`, `_Iosbase`, `_Fill`, `val`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// money_put_put.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
//   locale loc( "german_germany" );  
   locale loc( "english_canada" );  
   basic_stringstream<char> psz, psz2;  
   ios_base::iostate st = 0;  
  
   psz2.imbue( loc );  
   psz2.flags( psz2.flags( )|ios_base::showbase ); // force the printing of the currency symbol  
   use_facet < money_put < char > >(loc).put(basic_ostream<char>::_Iter( psz2.rdbuf( ) ), true, psz2, st, 100012);  
   if (st & ios_base::failbit)  
      cout << "money_put( ) FAILED" << endl;  
   else  
      cout << "money_put( ) = \"" << psz2.rdbuf( )->str( ) <<"\""<< endl;     
  
   st = 0;  
};  
```  
  
```Output  
money_put( ) = "CAD1,000.12"  
```  
  
##  <a name="string_type"></a>money_put::STRING_TYPE  
 Typ, který popisuje řetězec obsahující znaky typu **CharType**.  
  
```  
typedef basic_string<CharType, Traits, Allocator> string_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [basic_string](../standard-library/basic-string-class.md) jejichž objekty může ukládat pořadí prvků z zdrojové sekvence.  
  
## <a name="see-also"></a>Viz také  
 [\<národní prostředí >](../standard-library/locale.md)   
 [facet – třída](../standard-library/locale-class.md#facet_class)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

