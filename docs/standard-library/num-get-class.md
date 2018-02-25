---
title: "num_get – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
dev_langs:
- C++
helpviewer_keywords:
- std::num_get [C++]
- std::num_get [C++], char_type
- std::num_get [C++], iter_type
- std::num_get [C++], do_get
- std::num_get [C++], get
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 205bd19d1c051f00a90b45d42997a5d8a1d5eb0f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="numget-class"></a>num_get – třída
Třídu šablony, která popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převody pořadí typu `CharType` do číselných hodnot.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>  
class num_get : public locale::facet;
```  
  
#### <a name="parameters"></a>Parametry  
 `CharType`  
 Typ používaný v rámci programu ke kódování znaků v národním prostředí.  
  
 `InputIterator`  
 Typ iterátoru, ze kterého číselné funkce get čtou svůj vstup.  
  
## <a name="remarks"></a>Poznámky  
 Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. Ukládá jedinečné kladnou hodnotu v první pokus o přístup k jeho uložené hodnoty **id.**  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[num_get](#num_get)|V konstruktoru pro objekty typu `num_get` , se používají k získání číselné hodnoty z pořadí.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|  
|[iter_type](#iter_type)|Typ, který popisuje vstupní iterátor.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[do_get](#do_get)|Virtuální funkce volaná k extrakci číselné hodnoty nebo logické hodnoty ze sekvence znaků.|  
|[get](#get)|Extrahuje ze sekvence znaků číselnou nebo logickou hodnotu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<národní prostředí >  
  
 **Namespace:** – std  
  
##  <a name="char_type"></a>  num_get::char_type  
 Typ, který se používá k popisu znaku používaného národním prostředním.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **CharType**.  
  
##  <a name="do_get"></a>  num_get::do_get  
 Virtuální funkce volaná k extrakci číselné hodnoty nebo logické hodnoty ze sekvence znaků.  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
    
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Začátek rozsahu znaků, z kterého se mají číst číslo.  
  
 `last`  
 Konec rozsahu znaků, z kterého se mají číst číslo.  
  
 `_Iosbase`  
 [Ios_base](../standard-library/ios-base-class.md) jejichž příznaky jsou používány převod.  
  
 `_State`  
 Stavu, na které failbit (viz [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) je přidána při selhání.  
  
 `val`  
 Hodnota, která byla načtena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator po hodnota byl načten.  
  
### <a name="remarks"></a>Poznámky  
 První funkci virtuální chráněného člena  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
```  
  
 odpovídá sekvenční elementy začínající na `first` v pořadí `[first, last)` dokud má rozpoznána úplná, neprázdná celé číslo vstupní pole. Pokud úspěšné, převede ji toto pole na ekvivalentní hodnotu jako typ `long`a ukládá výsledky v `val`. Vrátí iterovat určení první prvek nad rámec číselné vstupní pole. Jinak funkce ukládá ustanovení v `val` a nastaví `ios_base::failbit` v `state`. Vrátí iterovat určení první prvek nad rámec všechny předpony vstupní pole platné celé číslo. V obou případech, pokud se rovná návratovou hodnotu `last`, nastaví funkce `ios_base::eofbit` v `state`.  
  
 Vstupní pole celé číslo je převedeno stejné pravidly používané funkce kontroly pro porovnávání a převody řadu `char` elementy ze souboru. (Každý například `char` element se předpokládá, že k mapování na ekvivalentní element typu `Elem` pomocí jednoduchého typu 1: 1, mapování.) Specifikace převod ekvivalentní kontroly je stanoven následujícím způsobem:  
  
 Pokud `iosbase.` [ios_base::flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), je specifikace převod `lo`.  
  
 Pokud `iosbase.flags() & ios_base::basefield == ios_base::` [šestnáctkových](../standard-library/ios-functions.md#hex), je specifikace převod `lx`.  
  
 Pokud `iosbase.flags() & ios_base::basefield == 0`, je specifikace převod `li`.  
  
 Jinak je specifikace převod `ld`.  
  
 Formát vstupního pole celé číslo je dáno Další [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class) `fac` volání vráceny [use_facet](../standard-library/locale-functions.md#use_facet) `<` [numpunct](../standard-library/numpunct-class.md) `<Elem>(iosbase.` [ios_base::getloc](../standard-library/ios-base-class.md#getloc)`())`. Konkrétně:  
  
 `fac.` [numpunct::Grouping](../standard-library/numpunct-class.md#grouping) `()` určuje způsob seskupení číslic nalevo od všech desetinné čárky  
  
 `fac.` [numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` určuje pořadí, který odděluje skupiny číslic nalevo od všech desetinné čárky.  
  
 Pokud žádné instance `fac.thousands_sep()` ke kterým došlo v číselné vstupní pole, je nevyžaduje žádné omezení seskupení. Jinak, nevyžaduje žádná omezení seskupení `fac.grouping()` prosazují a oddělovačů jsou odebrány, než dojde k převodu kontroly.  
  
 Čtvrtý chráněného člena virtuální funkce:  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```  
  
 se chová stejně jako první, s tím rozdílem, že se nahradí převod specifikaci `ld` s `lu`. Pokud úspěšné převádí číselné vstupní pole na hodnotu typu `unsigned long` a uloží tuto hodnotu v `val`.  
  
 Funkci páté virtuální chráněného člena:  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;
```  
  
 se chová stejně jako první, s tím rozdílem, že se nahradí převod specifikaci `ld` s `lld`. Pokud úspěšné převádí číselné vstupní pole na hodnotu typu `long long` a uloží tuto hodnotu v `val`.  
  
 Šesté chráněného člena virtuální funkce:  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;
```  

 se chová stejně jako první, s tím rozdílem, že se nahradí převod specifikaci `ld` s `llu`. Pokud úspěšné převádí číselné vstupní pole na hodnotu typu `unsigned long long` a uloží tuto hodnotu v `val`.  
  
 Funkci sedmého virtuální chráněného člena:  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;
```  
  
 Kromě toho, že ho endeavors tak, aby odpovídaly dokončení, neprázdná s plovoucí desetinnou čárkou vstupní pole se chová stejně jako první. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` určuje pořadí, který odděluje číslic celé číslo od zlomek číslic. Specifikátor převod ekvivalentní kontroly je `lf`.  
  
 Funkci osmého virtuální chráněného člena:  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```  
  
 Kromě toho, že ho endeavors tak, aby odpovídaly dokončení, neprázdná s plovoucí desetinnou čárkou vstupní pole se chová stejně jako první. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` určuje pořadí, který odděluje číslic celé číslo od zlomek číslic. Specifikátor převod ekvivalentní kontroly je `lf`.  
  
 Funkci deváté virtuální chráněného člena:  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```  
  
 se chová stejně jako osmou, s tím rozdílem, že je specifikátor převod ekvivalentní kontroly `Lf`.  
  
 Funkci desetinu virtuální chráněného člena:  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
 se chová stejně první, s tím rozdílem, že je specifikátor převod ekvivalentní kontroly `p`.  
  
 Poslední chráněného člena (eleventh) virtuální funkce:  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
 Kromě toho, že ho endeavors tak, aby odpovídaly dokončení, neprázdná logické vstupní pole se chová stejně jako první. Pokud úspěšné převede ji logické vstupní pole na hodnotu typu `bool` a uloží tuto hodnotu v `val`.  
  
 Logická hodnota vstupní pole má dvě formy. Pokud `iosbase.flags() & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) je nastavena hodnota false, s tím rozdílem, že převedená hodnota musí být buď 0 (false) nebo 1 (pravda) je stejný jako celé číslo vstupní pole. Pořadí, jinak hodnota musí odpovídat buď `fac.` [numpunct::falsename](../standard-library/numpunct-class.md#falsename) `()` (pro false), nebo `fac.` [numpunct::truename](../standard-library/numpunct-class.md#truename) `()` (pro true).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [získat](#get), kde je volána funkce člena virtuální `do_get`.  
  
##  <a name="get"></a>  num_get::Get  
 Extrahuje ze sekvence znaků číselnou nebo logickou hodnotu.  
  
```
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Začátek rozsahu znaků, z kterého se mají číst číslo.  
  
 `last`  
 Konec rozsahu znaků, z kterého se mají číst číslo.  
  
 `_Iosbase`  
 [Ios_base](../standard-library/ios-base-class.md) jejichž příznaky jsou používány převod.  
  
 `_State`  
 Stavu, na které failbit (viz [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) je přidána při selhání.  
  
 `val`  
 Hodnota, která byla načtena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator po hodnota byl načten.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí všechny členské funkce [do_get –](#do_get)( `first`, `last`, `_Iosbase`, `_State`, `val`).  
  
 První virtuální chráněného člena funkce se pokusí vyhledat sekvenční elementy začínající na první v pořadí [ `first`, `last`) dokud má rozpoznána úplná, neprázdná celé číslo vstupní pole. Pokud úspěšné, převede ji toto pole na ekvivalentní hodnotu jako typ **dlouho** a ukládá výsledky v `val`. Vrátí iterovat určení první prvek nad rámec číselné vstupní pole. Jinak funkce ukládá ustanovení v `val` a nastaví `ios_base::failbit` v _ *stavu*. Vrátí iterovat určení první prvek nad rámec všechny předpony vstupní pole platné celé číslo. V obou případech, pokud se rovná návratovou hodnotu **poslední**, nastaví funkce `ios_base::eofbit` v `_State`.  
  
 Vstupní pole celé číslo je převedeno stejné pravidly používané funkce kontroly pro porovnávání a převody řadu `char` elementy ze souboru. Každý například `char` element se předpokládá, že k mapování na ekvivalentní element typu **CharType** mapováním jednoduchý, 1: 1. Specifikace převod ekvivalentní kontroly je stanoven následujícím způsobem:  
  
-   Pokud **iosbase**. [příznaky](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct), je specifikace převod **u**.  
  
-   Pokud **iosbase.flags** & **ios_base::basefield** == `ios_base::`[šestnáctkových](../standard-library/ios-functions.md#hex), je specifikace převod **lx** .  
  
-   Pokud **iosbase.flags** & **ios_base::basefield** == 0, je specifikace převod `li`.  
  
-   Jinak je specifikace převod **ld**.  
  
 Formát vstupního pole celé číslo je dáno Další [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class)**fac** volání vráceny [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct ](../standard-library/numpunct-class.md) \< **Elem**> ( **iosbase**. [getloc –](../standard-library/ios-base-class.md#getloc)). Konkrétně:  
  
- **fac**. [seskupování](../standard-library/numpunct-class.md#grouping) určuje způsob seskupení číslic nalevo od všech desetinné čárky.  
  
- **fac**. [thousands_sep –](../standard-library/numpunct-class.md#thousands_sep) určuje pořadí, který odděluje skupiny číslic nalevo od všech desetinné čárky.  
  
 Pokud žádné instance **fac**. `thousands_sep` ve číselné vstupní pole, je nevyžaduje žádné omezení seskupení. Jinak, nevyžaduje žádná omezení seskupení **fac**. **seskupování** je vynucená a oddělovačů jsou odebrány, než dojde k převodu kontroly.  
  
 Druhý virtuální chráněného člena funkce:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```  
  
 se chová stejně jako první, s tím rozdílem, že se nahradí převod specifikaci **ld** s **lu**. Pokud úspěšné, převede ji číselné vstupní pole na hodnotu typu `unsigned long` a uloží tuto hodnotu v `val`.  
  
 Třetí virtuální chráněného člena funkce:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```  
  
 Kromě toho, že se pokouší vyhledat dokončení, neprázdná s plovoucí desetinnou čárkou vstupní pole se chová stejně jako první. **fac**. [decimal_point –](../standard-library/numpunct-class.md#decimal_point) určuje pořadí, který odděluje číslic celé číslo od zlomek číslic. Specifikátor převod ekvivalentní kontroly je **lf**.  
  
 Čtvrtý chráněného člena virtuální funkce:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```  
  
 se chová stejně třetí, s tím rozdílem, že je specifikátor převod ekvivalentní kontroly **Lf**.  
  
 Funkci páté virtuální chráněného člena:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
 se chová stejně první, s tím rozdílem, že je specifikátor převod ekvivalentní kontroly **p**.  
  
 Šesté chráněného člena virtuální funkce:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
 Kromě toho, že se pokouší vyhledat dokončení, neprázdná logické vstupní pole se chová stejně jako první. Pokud úspěšné převede ji logické vstupní pole na hodnotu typu `bool` a uloží tuto hodnotu v `val`.  
  
 Logická hodnota vstupní pole má dvě formy. Pokud **iosbase**. **příznaky** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) je **false**, s tím rozdílem, že převedená hodnota musí být buď 0 je stejný jako celé číslo vstupní pole (pro **false** ) nebo 1 (pro **true**). Pořadí, jinak hodnota musí odpovídat buď **fac**. [falsename –](../standard-library/numpunct-class.md#falsename) (pro **false**), nebo **fac**. [truename –](../standard-library/numpunct-class.md#truename) (pro **true**).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// num_get_get.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   basic_stringstream<char> psz, psz2;  
   psz << "-1000,56";  
  
   ios_base::iostate st = 0;  
   long double fVal;  
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;  
  
   psz.imbue( loc );  
   use_facet <num_get <char> >  
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),  
           basic_istream<char>::_Iter(0), psz, st, fVal );  
  
   if ( st & ios_base::failbit )  
      cout << "money_get( ) FAILED" << endl;  
   else  
      cout << "money_get( ) = " << fVal << endl;  
}  
```  
  
##  <a name="iter_type"></a>  num_get::iter_type  
 Typ, který popisuje vstupní iterátor.  
  
```
typedef InputIterator iter_type;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **InputIterator**.  
  
##  <a name="num_get"></a>  num_get::num_get  
 V konstruktoru pro objekty typu `num_get` , se používají k získání číselné hodnoty z pořadí.  
  
```
explicit num_get(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `_Refs`  
 Celočíselná hodnota určuje typ správy paměti pro objekt.  
  
### <a name="remarks"></a>Poznámky  
 Možné hodnoty `_Refs` parametrů a jejich významu jsou:  
  
-   0: doba života objektu spravuje národní prostředí, které je obsahují.  
  
-   1: doba života objektu, se musí ručně spravovat.  
  
-   \> 1: tyto hodnoty nejsou definovány.  
  
 Žádné přímé příklady je možné, protože je chráněn destruktoru.  
  
 Konstruktor inicializuje jeho základní objekt s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)( `_Refs`).  
  
## <a name="see-also"></a>Viz také  
 [\<národní prostředí >](../standard-library/locale.md)   
 [facet – třída](../standard-library/locale-class.md#facet_class)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



