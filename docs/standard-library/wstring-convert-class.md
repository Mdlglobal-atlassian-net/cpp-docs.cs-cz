---
title: "wstring_convert – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- wstring/stdext::cvt::wstring_convert
- locale/std::wstring_convert::byte_string
- locale/std::wstring_convert::wide_string
- locale/std::wstring_convert::state_type
- locale/std::wstring_convert::int_type
- locale/std::wstring_convert::from_bytes
- locale/std::wstring_convert::to_bytes
- locale/std::wstring_convert::converted
- locale/std::wstring_convert::state
dev_langs: C++
helpviewer_keywords:
- stdext::cvt [C++], wstring_convert
- std::wstring_convert [C++], byte_string
- std::wstring_convert [C++], wide_string
- std::wstring_convert [C++], state_type
- std::wstring_convert [C++], int_type
- std::wstring_convert [C++], from_bytes
- std::wstring_convert [C++], to_bytes
- std::wstring_convert [C++], converted
- std::wstring_convert [C++], state
ms.assetid: e34f5b65-d572-4bdc-ac69-20778712e376
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7753e2be6699bc789417d8afe9e9f49e55af7010
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="wstringconvert-class"></a>wstring_convert – třída
Šablony třídy `wstring_convert` provádí převody mezi řetězec bajtové a široké řetězec.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```  
  
#### <a name="parameters"></a>Parametry  
 Codecvt –  
 [Národního prostředí](../standard-library/locale-class.md) omezující vlastnosti, který představuje objekt převod.  
  
 Elem  
 Typ elementu široká charakterová.  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje objekt, který řídí převody mezi široké řetězec objekty třídy `std::basic_string<Elem>` a bajtů řetězce objekty třídy `std::basic_string<char>` (také označované jako `std::string`). Šablony třídy definuje typy `wide_string` a `byte_string` jako synonyma pro tyto dva typy. Převod mezi posloupnost `Elem` hodnoty (uložené v `wide_string` objekt) a vícebajtové pořadí (uložené v `byte_string` objektu) se provádí v objektu třídy `Codecvt<Elem, char, std::mbstate_t>`, který splňuje požadavky standardu omezující vlastnost kódu převod `std::codecvt<Elem, char, std::mbstate_t>`.  
  
 Tato třída šablony objektu ukládá:  
  
-   Byte řetězec k zobrazení o chybách  
  
-   Široké řetězec k zobrazení o chybách  
  
-   Ukazatel na objekt přidělené převodu (což je uvolněno při zničena objekt wbuffer_convert)  
  
-   Objekt stavu převodu typu [state_type –](#state_type)  
  
-   Počet převod  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[wstring_convert –](#wstring_convert)|Vytvoří objekt typu `wstring_convert`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[byte_string –](#byte_string)|Typ, který představuje řetězec bajtů.|  
|[wide_string –](#wide_string)|Typ, který představuje široké řetězec.|  
|[state_type –](#state_type)|Typ, který představuje stav převodu.|  
|[int_type –](#int_type)|Typ, který představuje celé číslo.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[from_bytes –](#from_bytes)|Převede řetězec bajtů na řetězec široké.|  
|[to_bytes –](#to_bytes)|Převede široké řetězec na řetězec bajtů.|  
|[převést](#converted)|Vrátí počet úspěšné převody.|  
|[Stav](#state)|Vrátí objekt představující stav převodu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<národní prostředí >  
  
 **Namespace:** – std  
  
##  <a name="byte_string"></a>wstring_convert::byte_string  
 Typ, který představuje řetězec bajtů.  
  
```
typedef std::basic_string<char> byte_string;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ se jedná o synonymum `std::basic_string<char>`.  
  
##  <a name="converted"></a>wstring_convert::converted  
 Vrátí počet úspěšné převody.  
  
```
size_t converted() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet úspěšně převody.  
  
### <a name="remarks"></a>Poznámky  
 Počet úspěšně převody jsou uloženy v objektu počet převod.  
  
##  <a name="from_bytes"></a>wstring_convert::from_bytes  
 Převede řetězec bajtů na řetězec široké.  
  
```
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Byte`|Pořadí bajtů jeden element má být převeden.|  
|`ptr`|C – styl, ukončené hodnotou null posloupnost znaků, který má být převeden.|  
|`Bstr`|[Byte_string –](#byte_string) má být převeden.|  
|`first`|První znak v rozsah znaků, které má být převeden.|  
|`last`|Poslední znak v rozsah znaků, které má být převeden.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt string široké vyplývající z převodu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud [převodu stavu](../standard-library/wstring-convert-class.md) objekt byl `not` zkonstruovat s explicitní hodnotu, je nastavený na jeho výchozí hodnota (stav počáteční převod) před zahájením převodu. V opačném případě je ponechán beze změny.  
  
 Počet úspěšně převést elementy vstupu je uložen v objektu počet převod. Pokud nedojde k žádné chybě převodu, – členská funkce vrátí řetězec převedený široké. Jinak hodnota pokud objekt byl vytvořen pomocí inicializátoru celou řetězec chybové zprávy, – členská funkce vrátí objekt zpráva Chyba celou řetězce. V opačném – členská funkce vyvolá objekt třídy [range_error](../standard-library/range-error-class.md).  
  
##  <a name="int_type"></a>wstring_convert::int_type  
 Typ, který představuje celé číslo.  
  
```
typedef typename wide_string::traits_type::int_type int_type;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ se jedná o synonymum `wide_string::traits_type::int_type`.  
  
##  <a name="state"></a>wstring_convert::State  
 Vrátí objekt představující stav převodu.  
  
```
state_type state() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 [Převodu stavu](../standard-library/wstring-convert-class.md) objekt, který reprezentuje stav převodu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="state_type"></a>wstring_convert::state_type  
 Typ, který představuje stav převodu.  
  
```
typedef typename Codecvt::state_type state_type;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje objekt, který může představovat převod stavu. Typ se jedná o synonymum `Codecvt::state_type`.  
  
##  <a name="to_bytes"></a>wstring_convert::to_bytes  
 Převede široké řetězec na řetězec bajtů.  
  
```
byte_string to_bytes(Elem Char);
byte_string to_bytes(const Elem* Wptr);
byte_string to_bytes(const wide_string& Wstr);
byte_string to_bytes(const Elem* first, const Elem* last);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Char`|Široké znak, který má být převeden.|  
|`Wptr`|C – styl, ukončené hodnotou null pořadí, počínaje na `wptr`, má být převeden.|  
|`Wstr`|[Wide_string –](#wide_string) má být převeden.|  
|`first`|Prvním elementem v rozsahu prvků, které má být převeden.|  
|`last`|Posledním prvkem v rozsahu prvků, které má být převeden.|  
  
### <a name="remarks"></a>Poznámky  
 Pokud [převodu stavu](../standard-library/wstring-convert-class.md) objekt byl `not` zkonstruovat s explicitní hodnotu, je nastavený na jeho výchozí hodnota (stav počáteční převod) před zahájením převodu. V opačném případě je ponechán beze změny.  
  
 Počet úspěšně převést elementy vstupu je uložen v objektu počet převod. Pokud nedojde k žádné chybě převodu, – členská funkce vrátí řetězec převedený bajtů. Jinak hodnota pokud objekt byl vytvořen pomocí inicializátoru bajtů řetězec chybové zprávy, – členská funkce vrátí objekt zpráva bajtů řetězec chyby. V opačném – členská funkce vyvolá objekt třídy [range_error](../standard-library/range-error-class.md).  
  
##  <a name="wide_string"></a>wstring_convert::wide_string  
 Typ, který představuje široké řetězec.  
  
```
typedef std::basic_string<Elem> wide_string;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ se jedná o synonymum `std::basic_string<Elem>`.  
  
##  <a name="wstring_convert"></a>wstring_convert::wstring_convert  
 Vytvoří objekt typu `wstring_convert`.  
  
```
wstring_convert(Codecvt *Pcvt = new Codecvt);
wstring_convert(Codecvt *Pcvt, state_type _State);
wstring_convert(const byte_string& _Berr, const wide_string& Werr = wide_string());
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`*Pcvt`|Objekt typu `Codecvt` provést převod.|  
|`_State`|Objekt typu [state_type –](#state_type) reprezentující stav převodu.|  
|`_Berr`|[Byte_string –](#byte_string) zobrazíte na chyby.|  
|`Werr`|[Wide_string –](#wide_string) zobrazíte na chyby.|  
  
### <a name="remarks"></a>Poznámky  
 První úložiště konstruktor *Pcvt_arg* v [převod objektu](../standard-library/wstring-convert-class.md)
