---
title: "codecvt – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocale/std::codecvt
- xlocale/std::codecvt::extern_type
- xlocale/std::codecvt::intern_type
- xlocale/std::codecvt::state_type
- xlocale/std::codecvt::always_noconv
- xlocale/std::codecvt::do_always_noconv
- xlocale/std::codecvt::do_encoding
- xlocale/std::codecvt::do_in
- xlocale/std::codecvt::do_length
- xlocale/std::codecvt::do_max_length
- xlocale/std::codecvt::do_out
- xlocale/std::codecvt::do_unshift
- xlocale/std::codecvt::encoding
- xlocale/std::codecvt::in
- xlocale/std::codecvt::length
- xlocale/std::codecvt::max_length
- xlocale/std::codecvt::out
- xlocale/std::codecvt::unshift
dev_langs: C++
helpviewer_keywords:
- std::codecvt [C++]
- std::codecvt [C++], extern_type
- std::codecvt [C++], intern_type
- std::codecvt [C++], state_type
- std::codecvt [C++], always_noconv
- std::codecvt [C++], do_always_noconv
- std::codecvt [C++], do_encoding
- std::codecvt [C++], do_in
- std::codecvt [C++], do_length
- std::codecvt [C++], do_max_length
- std::codecvt [C++], do_out
- std::codecvt [C++], do_unshift
- std::codecvt [C++], encoding
- std::codecvt [C++], in
- std::codecvt [C++], length
- std::codecvt [C++], max_length
- std::codecvt [C++], out
- std::codecvt [C++], unshift
ms.assetid: 37d3efa1-2b7f-42b6-b04f-7a972c8c2c86
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 36631c1a23c90b875d2a2fba8a1cec23b97c2400
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="codecvt-class"></a>codecvt – třída
Třída šablony popisující objekt, který může sloužit jako podmínka národního prostředí. Dokáže řídit převody mezi sekvencí hodnot používanou ke kódování znaků v rámci programu a sekvencí hodnot používanou ke kódování znaků mimo program.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class CharType, class Byte, class StateType>  
class codecvt : public locale::facet, codecvt_base;  
```  
  
#### <a name="parameters"></a>Parametry  
 `CharType`  
 Typ používaný v rámci programu ke kódování znaků.  
  
 `Byte`  
 Typ použitý ke kódování znaků mimo program.  
  
 `StateType`  
 Typ, který lze použít k reprezentaci průběžných stavů převodu mezi interními a externími typy znázornění znaků.  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje objekt, který může sloužit jako [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class), řídit převody mezi pořadí hodnot typu `CharType` a pořadí hodnot typu `Byte`. Třída `StateType` charakterizuje transformaci – a třída objektu `StateType` ukládá žádné informace o stavu potřebné při převodu.  
  
 Interní kódování používá znázornění s pevný počet bajtů za znak, obvykle buď zadejte `char` nebo typ `wchar_t`.  
  
 Stejně jako u jakékoli omezující vlastnost národního prostředí je statický objekt `id` uložil počáteční hodnota nula. Ukládá jedinečné kladnou hodnotu v první pokus o přístup k jeho uložené hodnoty `id`.  
  
 Verze šablony [do_in –](#do_in) a [do_out –](#do_out) vždy vrátí `codecvt_base::noconv`.  
  
 Standardní knihovna C++ definuje několik explicitní specializací:  
  
 `template<>`  
  
 `codecvt<wchar_t, char, mbstate_t>`  
  
 Převede mezi `wchar_t` a `char` pořadí.  
  
 `template<>`  
  
 `codecvt<char16_t, char, mbstate_t>`  
  
 Převede mezi `char16_t` pořadí kódovaná jako UTF-16 a `char` pořadí kódovaná jako UTF-8.  
  
 `template<>`  
  
 `codecvt<char32_t, char, mbstate_t>`  
  
 Převede mezi `char32_t` pořadí kódovaná jako znakové sady UTF-32 (UCS-4) a `char` pořadí kódovaná jako UTF-8.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[codecvt –](#codecvt)|V konstruktoru pro objekty třídy `codecvt` sloužícím jako omezující vlastnost národního prostředí pro zpracování převody.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[extern_type –](#extern_type)|Typ znaku, který se používá pro externí reprezentace.|  
|[intern_type –](#intern_type)|Typ znaku, který se používá pro interní reprezentace.|  
|[state_type –](#state_type)|Typ znaku, který se používá k reprezentaci průběžných stavů během převodu mezi interními a externími znázorněními.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[always_noconv –](#always_noconv)|Ověřuje, zda je nutné provést nějaké převody.|  
|[do_always_noconv –](#do_always_noconv)|Virtuální funkce volaná k ověření, zda je nutné provést nějaké převody.|  
|[do_encoding –](#do_encoding)|Virtuální funkce, který testuje, pokud kódování `Byte` datový proud je stavu závislé, jestli poměr mezi `Byte`, která se používá a `CharType`s vytvořeného konstantní a pokud ano, určuje hodnotu tohoto poměru.|  
|[do_in –](#do_in)|Virtuální funkce volána převést posloupnost interní `Byte`s do pořadí externí `CharType`s.|  
|[do_length –](#do_length)|Virtuální funkce, která určuje, kolik `Byte`s z daného posloupnost externí `Byte`sad s více než zadaný počet interní `CharType`s a vrátí počet `Byte`s.|  
|[do_max_length –](#do_max_length)|Virtuální funkce, která vrátí maximální počet bajtů externí nezbytné k vytvoření jeden interní `CharType`.|  
|[do_out –](#do_out)|Virtuální funkce volána převést posloupnost interní `CharType`s pořadí externí bajtů.|  
|[do_unshift –](#do_unshift)|Virtuální funkce volána zajistit `Byte`během převodu stavu závislé potřebný pro dokončení jeho poslední znak v sekvenci s `Byte`s.|  
|[kódování](#encoding)|Testy Pokud kódování `Byte` datový proud je stavu závislé, jestli poměr mezi `Byte`, která se používá a `CharType`s vytvořeného konstantní a pokud ano, určuje hodnotu tohoto poměru.|  
|[in](#in)|Převede externí zobrazení posloupnosti `Byte`s do interního vyjádření posloupnosti `CharType`s.|  
|[Délka](#length)|Určuje, kolik `Byte`s z daného posloupnost externí `Byte`sad s více než zadaný počet interní `CharType`s a vrátí počet `Byte`s.|  
|[max_length](#max_length)|Vrátí maximální počet externí `Byte`s nezbytné k vytvoření jeden interní `CharType`.|  
|[out](#out)|Převede posloupnost interní `CharType`s do pořadí externí `Byte`s.|  
|[unshift –](#unshift)|Poskytuje externí `Byte`s během převodu stavu závislé potřebný pro dokončení jeho poslední znak v pořadí `Byte`s.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<národní prostředí >  
  
 **Namespace:** – std  
  
##  <a name="always_noconv"></a>codecvt::always_noconv  
 Ověřuje, zda je nutné provést nějaké převody.  
  
```  
bool always_noconv() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Logická hodnota, která je **true** Pokud žádné převody nutné provést; **false** je alespoň jeden je potřeba udělat.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_always_noconv –](#do_always_noconv).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// codecvt_always_noconv.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = use_facet<codecvt<char, char, mbstate_t> >   
      ( loc ).always_noconv( );  
  
   if ( result1 )  
      cout << "No conversion is needed." << endl;  
   else  
      cout << "At least one conversion is required." << endl;  
  
   bool result2 = use_facet<codecvt<wchar_t, char, mbstate_t> >   
      ( loc ).always_noconv( );  
  
   if ( result2 )  
      cout << "No conversion is needed." << endl;  
   else  
      cout << "At least one conversion is required." << endl;  
}  
```  
  
```Output  
No conversion is needed.  
At least one conversion is required.  
```  
  
##  <a name="codecvt"></a>codecvt::codecvt  
 Konstruktor pro objekty codecvt – třída, která slouží jako omezující vlastnost národního prostředí pro zpracování převody.  
  
```  
explicit codecvt(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `_Refs`  
 Celočíselná hodnota určuje typ správy paměti pro objekt.  
  
### <a name="remarks"></a>Poznámky  
 Možné hodnoty `_Refs` parametrů a jejich významu jsou:  
  
-   0: doba života objektu spravuje národní prostředí, které je obsahují.  
  
-   1: doba života objektu, se musí ručně spravovat.  
  
-   \>1: tyto hodnoty nejsou definovány.  
  
 Konstruktor inicializuje jeho `locale::facet` základní objekt s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)(`_Refs`).  
  
##  <a name="do_always_noconv"></a>codecvt::do_always_noconv  
 Virtuální funkce volaná k ověření, zda je nutné provést nějaké převody.  
  
```  
virtual bool do_always_noconv() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Chráněný člen virtuální funkce vrátí hodnotu **true** pouze v případě každé volání [do_in –](#do_in) nebo [do_out –](#do_out) vrátí **noconv**.  
  
 Verze šablony vždy vrátí hodnotu **true**.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [always_noconv –](#always_noconv), který volá `do_always_noconv`.  
  
##  <a name="do_encoding"></a>codecvt::do_encoding  
 Virtuální funkce, který testuje, pokud kódování **bajtů** datový proud je stavu závislé, jestli poměr mezi **bajtů**, která se používá a **CharType**s vytvořeného je konstantní a pokud ano, určuje hodnotu tohoto poměru.  
  
```  
virtual int do_encoding() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Chráněný člen virtuální funkce vrátí hodnotu:  
  
-   -1, pokud kódování pořadí typu `extern_type` je stav závislé.  
  
-   0, pokud kódování zahrnuje pořadí různých délek.  
  
- *N*, pokud kódování zahrnuje pouze pořadí délky *N*  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [kódování](#encoding), který volá `do_encoding`.  
  
##  <a name="do_in"></a>codecvt::do_in  
 Virtuální funkce volána převést posloupnost externí **bajtů**s pořadím interní **CharType**s.  
  
```  
virtual result do_in(
    StateType& _State,  
    const Byte* first1,   
    const Byte* last1,   
    const Byte*& next1,  
    CharType* first2,  
    CharType* last2,  
    CharType*& next2,) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_State`  
 Převod stavu, který se spravuje mezi volání členské funkce.  
  
 `first1`  
 Ukazatel na začátek pořadí má být převeden.  
  
 `last1`  
 Ukazatel na konci pořadí má být převeden.  
  
 `next1`  
 Ukazatel přesahuje za konec sekvenci převedený na první nepřevedeném znak.  
  
 `first2`  
 Ukazatel na začátek převedený pořadí.  
  
 `last2`  
 Ukazatel na konec převedený pořadí.  
  
 `next2`  
 Ukazatel na **CharType** dodávaný po poslední převést **CharType**, první znak beze změny v cílovém pořadí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí, která udává úspěch, částečný úspěch nebo selhání operace. Funkce vrátí hodnotu:  
  
- **codecvt_base::Error** vytvořen. Pokud zdrojové sekvence je chybný.  
  
- `codecvt_base::noconv`Pokud funkce provádí žádný převod.  
  
- **codecvt_base::OK** Pokud je převod úspěšný.  
  
- **codecvt_base::partial** Pokud zdroj je nedostatečné nebo pokud cíl není dostatečně velký pro převod úspěšný.  
  
### <a name="remarks"></a>Poznámky  
 `_State`musí reprezentovat stav počáteční převod na začátku nového pořadí zdroje. Funkce mění jeho uložené hodnoty podle potřeby tak, aby odrážela aktuální stav převodu z úspěšné. Jeho uložené hodnoty je jinak neurčené.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [v](#in), který volá `do_in`.  
  
##  <a name="do_length"></a>codecvt::do_length  
 Virtuální funkce, která určuje, kolik **bajtů**s z daného posloupnost externí **bajtů**sad s více než zadaný počet interní **CharType**s a vrací, které počet **bajtů**s.  
  
```  
virtual int do_length(
    const StateType& _State,  
    const Byte* first1,   
    const Byte* last1,  
    size_t _Len2) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_State`  
 Převod stavu, který se spravuje mezi volání členské funkce.  
  
 `first1`  
 Ukazatel na začátek externí pořadí.  
  
 `last1`  
 Ukazatel na konec externí pořadí.  
  
 `_Len2`  
 Maximální počet **bajtů**s, který může být vrácen – členská funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo představující počet převody, není větší než maximální počet `_Len2`, určené pořadí externího zdroje v [ `first1`, `last1`).  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce efektivně volá `do_in`( `_State`, `first1`, `last1`, `next1`, `_Buf`, `_Buf`  +  `_Len2`, `next2`) pro `_State` (kopie stavu), některé vyrovnávací paměti `_Buf`a ukazatele `next1`a `next2`.  
  
 Pak vrátí `next2`  -  **buf**. Proto počítá převody, není větší než maximální počet `_Len2`, určené zdrojové sekvence v [ `first1`, `last1`).  
  
 Verze šablony vždy vrátí hodnotu menší z `last1`  -  `first1` a `_Len2`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [délka](#length), který volá **do_length –**.  
  
##  <a name="do_max_length"></a>codecvt::do_max_length  
 Virtuální funkce, která vrátí maximální počet externí **bajtů**s nezbytné k vytvoření jeden interní **CharType**.  
  
```  
virtual int do_max_length() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální počet **bajtů**s nezbytné k vytvoření jeden **CharType**.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce vrátí největší povolenou hodnotu, která může být vrácen pouze [do_length –](#do_length)( `first1`, `last1`, 1) pro libovolný platný hodnoty `first1` a `last1`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [max_length](#max_length), který volá `do_max_length`.  
  
##  <a name="do_out"></a>codecvt::do_out  
 Virtuální funkce volána převést posloupnost interní **CharType**s do pořadí externí **bajtů**s.  
  
```  
virtual result do_out(
    StateType& _State,  
    const CharType* first1,   
    const CharType* last1,  
    const CharType*& next1,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_State`  
 Převod stavu, který se spravuje mezi volání členské funkce.  
  
 `first1`  
 Ukazatel na začátek pořadí má být převeden.  
  
 `last1`  
 Ukazatel na konci pořadí má být převeden.  
  
 `next1`  
 Odkaz na ukazatel na první nepřevedený **CharType**, za poslední **CharType** převést.  
  
 `first2`  
 Ukazatel na začátek převedený pořadí.  
  
 `last2`  
 Ukazatel na konec převedený pořadí.  
  
 `next2`  
 Odkaz na ukazatel na první nepřevedený **bajtů**, za poslední **bajtů** převést.  
  
### <a name="return-value"></a>Návratová hodnota  
 Funkce vrátí hodnotu:  
  
- **codecvt_base::Error** vytvořen. Pokud zdrojové sekvence je chybný.  
  
- `codecvt_base::noconv`Pokud funkce provádí žádný převod.  
  
- **codecvt_base::OK** Pokud je převod úspěšný.  
  
- **codecvt_base::partial** Pokud zdroj je nedostatečné nebo pokud cíl není dostatečně velký pro převod úspěšný.  
  
### <a name="remarks"></a>Poznámky  
 `_State`musí reprezentovat stav počáteční převod na začátku nového pořadí zdroje. Funkce mění jeho uložené hodnoty podle potřeby tak, aby odrážela aktuální stav převodu z úspěšné. Jeho uložené hodnoty je jinak neurčené.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [out](#out), který volá `do_out`.  
  
##  <a name="do_unshift"></a>codecvt::do_unshift  
 Virtuální funkce volána zajistit **bajtů**během převodu stavu závislé potřebný pro dokončení jeho poslední znak v sekvenci s **bajtů**s.  
  
```  
virtual result do_unshift(
    StateType& _State,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_State`  
 Převod stavu, který se spravuje mezi volání členské funkce.  
  
 `first2`  
 Ukazatel na první pozici v cílové oblasti.  
  
 `last2`  
 Ukazatel na poslední pozice v cílové oblasti.  
  
 `next2`  
 Ukazatel na prvním elementem beze změny v cílovém pořadí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Funkce vrátí hodnotu:  
  
- **codecvt_base::Error** Pokud _ *stavu* představuje neplatném stavu  
  
- `codecvt_base::noconv`Pokud funkce provádí žádný převod  
  
- **codecvt_base::OK** Pokud převod úspěšné  
  
- **codecvt_base::partial** Pokud cíl není dostatečně velký pro převod úspěšný  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce se snaží převést source element **CharType**(0) k určení pořadí, které ukládají v rámci [ `first2`, `last2`), s výjimkou ukončující element **bajtů** (0). Vždy ukládá v `next2` ukazatel na prvním elementem beze změny v cílovém pořadí.  
  
 _ *Stavu* musí reprezentovat stav počáteční převod na začátku nového pořadí zdroje. Funkce mění jeho uložené hodnoty podle potřeby tak, aby odrážela aktuální stav převodu z úspěšné. Obvykle převádění source element **CharType**(0) zůstane ve stavu počáteční převod aktuální stav.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [unshift](#unshift), který volá `do_unshift`.  
  
##  <a name="encoding"></a>codecvt::Encoding  
 Testuje, pokud kódování **bajtů** datový proud je stavu závislé, jestli poměr mezi **bajtů**, která se používá a **CharType**s vytvořeného konstantní a pokud ano, určuje Hodnota této poměr.  
  
```  
int encoding() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je kladné návratovou hodnotu, pak tuto hodnotu je stálého počtu **bajtů** znaků požadovaných k vytvoření **CharType** znak.  
  
 Chráněný člen virtuální funkce vrátí hodnotu:  
  
-   -1, pokud kódování pořadí typu `extern_type` je stav závislé.  
  
-   0, pokud kódování zahrnuje pořadí různých délek.  
  
- *N*, pokud kódování zahrnuje pouze pořadí délky *N.*  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_encoding –](#do_encoding).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// codecvt_encoding.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   int result1 = use_facet<codecvt<char, char, mbstate_t> > ( loc ).encoding ( );  
   cout << result1 << endl;  
   result1 = use_facet<codecvt<wchar_t, char, mbstate_t> > ( loc ).encoding( );  
   cout << result1 << endl;  
   result1 = use_facet<codecvt<char, wchar_t, mbstate_t> > ( loc ).encoding( );  
   cout << result1 << endl;  
}  
```  
  
```Output  
1  
1  
1  
```  
  
##  <a name="extern_type"></a>codecvt::extern_type  
 Typ znaku, který se používá pro externí reprezentace.  
  
```  
typedef Byte extern_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **bajtů**.  
  
##  <a name="in"></a>codecvt::in  
 Převede externí zobrazení posloupnosti **bajtů**s do interního vyjádření posloupnosti **CharType**s.  
  
```  
result in(
    StateType& _State,  
    const Byte* first1,   
    const Byte* last1,   
    const Byte*& next1,  
    CharType* first2,  
    CharType* last2,  
    CharType*& next2,) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_State`  
 Převod stavu, který se spravuje mezi volání členské funkce.  
  
 `first1`  
 Ukazatel na začátek pořadí má být převeden.  
  
 `last1`  
 Ukazatel na konci pořadí má být převeden.  
  
 `next1`  
 Ukazatel přesahuje za konec sekvenci převedený na první nepřevedeném znak.  
  
 `first2`  
 Ukazatel na začátek převedený pořadí.  
  
 `last2`  
 Ukazatel na konec převedený pořadí.  
  
 `next2`  
 Ukazatel na **CharType** dodávaný po poslední převést **Chartype** na první znak beze změny v cílovém pořadí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí, která udává úspěch, částečný úspěch nebo selhání operace. Funkce vrátí hodnotu:  
  
- **codecvt_base::Error** vytvořen. Pokud zdrojové sekvence je chybný.  
  
- `codecvt_base::noconv`Pokud funkce provádí žádný převod.  
  
- **codecvt_base::OK** Pokud je převod úspěšný.  
  
- **codecvt_base::partial** Pokud zdroj je nedostatečné nebo pokud cíl není dostatečně velký pro převod úspěšný.  
  
### <a name="remarks"></a>Poznámky  
 `_State`musí reprezentovat stav počáteční převod na začátku nového pořadí zdroje. Funkce mění uložené hodnoty, podle potřeby tak, aby odrážela aktuální stav převodu z úspěšné. Po převodu z částečné `_State` musí být nastaven tak, aby převod na pokračovat, až bude doručen nové znaků.  
  
 Členské funkce vrátí hodnotu [do_in –](#do_in)( `_State`, _ *First1 Příjmení1, next1, First2, _Llast2, next2*).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// codecvt_in.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
using namespace std;  
#define LEN 90  
int main( )     
{  
   char* pszExt = "This is the string to be converted!";  
   wchar_t pwszInt [LEN+1];  
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));  
   const char* pszNext;  
   wchar_t* pwszNext;  
   mbstate_t state = {0};  
   locale loc("C");//English_Britain");//German_Germany  
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
     ( loc ).in( state,  
          pszExt, &pszExt[strlen(pszExt)], pszNext,  
          pwszInt, &pwszInt[strlen(pszExt)], pwszNext );  
   pwszInt[strlen(pszExt)] = 0;  
   wcout << ( (res!=codecvt_base::error)  L"It worked! " : L"It didn't work! " )  
   << L"The converted string is:\n ["  
   << &pwszInt[0]  
   << L"]" << endl;  
   exit(-1);  
}  
```  
  
```Output  
It worked! The converted string is:  
 [This is the string to be converted!]  
```  
  
##  <a name="intern_type"></a>codecvt::intern_type  
 Typ znaku, který se používá pro interní reprezentace.  
  
```  
typedef CharType intern_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **CharType**.  
  
##  <a name="length"></a>codecvt::length  
 Určuje, kolik **bajtů**s z daného posloupnost externí **bajtů**sad s více než zadaný počet interní **CharType**s a vrátí počet **Bajtů**s.  
  
```  
int length(
    const StateType& _State,  
    const Byte* first1,   
    const Byte* last1,  
    size_t _Len2) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_State`  
 Převod stavu, který se spravuje mezi volání členské funkce.  
  
 `first1`  
 Ukazatel na začátek externí pořadí.  
  
 `last1`  
 Ukazatel na konec externí pořadí.  
  
 `_Len2`  
 Maximální počet bajtů, které může být vrácené funkcí člen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo představující počet převody, není větší než maximální počet `_Len2`, určené pořadí externího zdroje v [ `first1`, `last1`).  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_length –](#do_length)( *_State first1*, `last1`, `_Len2`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// codecvt_length.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
using namespace std;  
#define LEN 90  
int main( )     
{  
   char* pszExt = "This is the string whose length is to be measured!";  
   mbstate_t state = {0};  
   locale loc("C");//English_Britain");//German_Germany  
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
     ( loc ).length( state,  
          pszExt, &pszExt[strlen(pszExt)], LEN );  
   cout << "The length of the string is: ";  
   wcout << res;  
   cout << "." << endl;  
   exit(-1);  
}  
```  
  
```Output  
The length of the string is: 50.  
```  
  
##  <a name="max_length"></a>codecvt::max_length  
 Vrátí maximální počet externí **bajtů**s nezbytné k vytvoření jeden interní **CharType**.  
  
```  
int max_length() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální počet **bajtů**s nezbytné k vytvoření jeden **CharType**.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [do_max_length –](#do_max_length).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// codecvt_max_length.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc( "C");//English_Britain" );//German_Germany  
   int res = use_facet<codecvt<char, char, mbstate_t> >  
     ( loc ).max_length( );  
   wcout << res << endl;  
}  
```  
  
```Output  
1  
```  
  
##  <a name="out"></a>codecvt::Out  
 Převede posloupnost interní **CharType**s do pořadí externí **bajtů**s.  
  
```  
result out(
    StateType& _State,  
    const CharType* first1,   
    const CharType* last1,  
    const CharType*& next1,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_State`  
 Převod stavu, který se spravuje mezi volání členské funkce.  
  
 `first1`  
 Ukazatel na začátek pořadí má být převeden.  
  
 `last1`  
 Ukazatel na konci pořadí má být převeden.  
  
 `next1`  
 Odkaz na ukazatel na první nepřevedený **CharType** za poslední **CharType** převést.  
  
 `first2`  
 Ukazatel na začátek převedený pořadí.  
  
 `last2`  
 Ukazatel na konec převedený pořadí.  
  
 `next2`  
 Odkaz na ukazatel na první nepřevedený **bajtů** po poslední převést **bajtů**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Členské funkce vrátí hodnotu [do_out –](#do_out)( `_State`, `first1`, `last1`, `next1`, `first2`, `last2`, `next2`).  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [codecvt::do_out](#do_out).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// codecvt_out.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
#include <wchar.h>  
using namespace std;  
#define LEN 90  
int main( )     
{  
   char pszExt[LEN+1];  
   wchar_t *pwszInt = L"This is the wchar_t string to be converted.";  
   memset( &pszExt[0], 0, ( sizeof( char ) )*( LEN+1 ) );  
   char* pszNext;  
   const wchar_t* pwszNext;  
   mbstate_t state;  
   locale loc("C");//English_Britain");//German_Germany  
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
      ( loc ).out( state,  
      pwszInt, &pwszInt[wcslen( pwszInt )], pwszNext ,  
      pszExt, &pszExt[wcslen( pwszInt )], pszNext );  
   pszExt[wcslen( pwszInt )] = 0;  
   cout << ( ( res!=codecvt_base::error )  "It worked: " : "It didn't work: " )  
   << "The converted string is:\n ["  
   << &pszExt[0]  
   << "]" << endl;  
}  
```  
  
```Output  
It worked: The converted string is:  
 [This is the wchar_t string to be converted.]  
```  
  
##  <a name="state_type"></a>codecvt::state_type  
 Typ znaku, který se používá k reprezentaci průběžných stavů během převodu mezi interními a externími znázorněními.  
  
```  
typedef StateType state_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **StateType**.  
  
##  <a name="unshift"></a>codecvt::unshift  
 Poskytuje **bajtů**během převodu stavu závislé potřebný pro dokončení jeho poslední znak v sekvenci s **bajtů**s.  
  
```  
result unshift(
    StateType& _State,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_State`  
 Převod stavu, který se spravuje mezi volání členské funkce.  
  
 `first2`  
 Ukazatel na první pozici v cílové oblasti.  
  
 `last2`  
 Ukazatel na poslední pozice v cílové oblasti.  
  
 `next2`  
 Ukazatel na prvním elementem beze změny v cílovém pořadí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Funkce vrátí hodnotu:  
  
- **codecvt_base::Error** Pokud stavu představuje neplatném stavu.  
  
- `codecvt_base::noconv`Pokud funkce provádí žádný převod.  
  
- **codecvt_base::OK** Pokud je převod úspěšný.  
  
- **codecvt_base::partial** Pokud cíl není dostatečně velký pro převod úspěšný.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce se snaží převést source element **CharType**(0) k určení pořadí, které ukládají v rámci [ `first2`, `last2`), s výjimkou ukončující element **bajtů** (0). Vždy ukládá v `next2` ukazatel na prvním elementem beze změny v cílovém pořadí.  
  
 `_State`musí reprezentovat stav počáteční převod na začátku nového pořadí zdroje. Funkce mění uložené hodnoty, podle potřeby tak, aby odrážela aktuální stav převodu z úspěšné. Obvykle převádění source element **CharType**(0) zůstane ve stavu počáteční převod aktuální stav.  
  
 Členské funkce vrátí hodnotu [do_unshift –](#do_unshift)( `_State`, `first2`, `last2`, `next2` ).  
  
## <a name="see-also"></a>Viz také  
 [\<národní prostředí >](../standard-library/locale.md)   
 [Znakové stránky](../c-runtime-library/code-pages.md)   
 [Názvy národních prostředí, jazyků a řetězce zemí/oblastí](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

