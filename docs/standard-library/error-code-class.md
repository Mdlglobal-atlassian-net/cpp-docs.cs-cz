---
title: "error_code – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- system_error/std::error_code
- system_error/std::error_code::value_type
- system_error/std::error_code::assign
- system_error/std::error_code::category
- system_error/std::error_code::clear
- system_error/std::error_code::default_error_condition
- system_error/std::error_code::message
- system_error/std::error_code::operator bool
dev_langs: C++
helpviewer_keywords:
- std::error_code
- std::error_code::value_type
- std::error_code::assign
- std::error_code::category
- std::error_code::clear
- std::error_code::default_error_condition
- std::error_code::message
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b2d451de1cacbb9654d7aafeb59cb1c23006dce9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="errorcode-class"></a>error_code – třída
Reprezentuje chyby nízké úrovně systému, které jsou specifické pro implementaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class error_code;
```  
  
## <a name="remarks"></a>Poznámky  
 Objekt typu `error_code` třída ukládá chybovou hodnotu kód a ukazatele na objekt, který představuje [kategorie](../standard-library/error-category-class.md) chyby kódy, které popisují hlášené chyby nízké úrovně systému.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[error_code](#error_code)|Vytvoří objekt typu `error_code`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[value_type](#value_type)|Typ, který představuje hodnotu kódu uložené chyby.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[přiřazení](#assign)|Přiřadí hodnotu kódu chyby a kategorie chybový kód.|  
|[kategorie](#category)|Vrátí kategorie chyby.|  
|[Vymazat](#clear)|Vymaže hodnotu kódu chyby a kategorie.|  
|[default_error_condition –](#default_error_condition)|Vrátí výchozí chybový stav.|  
|[message](#message)|Vrací název kód chyby.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[Operator ==](#op_eq_eq)|Testování rovnosti mezi `error_code` objekty.|  
|[operator!=](#op_neq)|Testy nerovnost mezi `error_code` objekty.|  
|[operátor <](#op_lt)|Testuje, pokud `error_code` objekt je menší než `error_code` objekt předaná pro porovnání.|  
|[operátor =](#op_eq)|Přiřadí novou hodnotu výčtu k `error_code` objektu.|  
|[operátor bool](#op_bool)|Vrhá proměnné typu `error_code`.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<system_error – >  
  
 **Namespace:** – std  
  
##  <a name="assign"></a>error_code::Assign  
 Přiřadí hodnotu kódu chyby a kategorie chybový kód.  
  
```
void assign(value_type val, const error_category& _Cat);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`val`|Hodnotu kód chyby pro ukládání `error_code`.|  
|`_Cat`|Chyba kategorii, kterou chcete uložit `error_code`.|  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce úložiště `val` jako hodnotu kódu chyby a ukazatel na `_Cat`.  
  
##  <a name="category"></a>error_code::category  
 Vrátí kategorie chyby.  
  
```
const error_category& category() const;
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="clear"></a>error_code::clear  
 Vymaže hodnotu kódu chyby a kategorie.  
  
```
clear();
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce ukládá nulová hodnota kódu chyby a odkazy [generic_category](../standard-library/system-error-functions.md#generic_category) objektu.  
  
##  <a name="default_error_condition"></a>error_code::default_error_condition  
 Vrátí výchozí chybový stav.  
  
```
error_condition default_error_condition() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 [Error_condition](../standard-library/error-condition-class.md) specifikace [default_error_condition –](../standard-library/error-category-class.md#default_error_condition).  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `category().default_error_condition(value())`.  
  
##  <a name="error_code"></a>error_code::error_code  
 Vytvoří objekt typu `error_code`.  
  
```
error_code();

error_code(value_type val, const error_category& _Cat);

template <class _Enum>
error_code(_Enum _Errcode,
    typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type* = 0);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`val`|Hodnotu kód chyby pro ukládání `error_code`.|  
|`_Cat`|Chyba kategorii, kterou chcete uložit `error_code`.|  
|`_Errcode`|Hodnota výčtu pro ukládání `error_code`.|  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor ukládá nulová hodnota kódu chyby a odkazy [generic_category](../standard-library/system-error-functions.md#generic_category).  
  
 Druhý konstruktor úložiště `val` jako hodnotu kódu chyby a ukazatel na [error_category](http://msdn.microsoft.com/en-us/6fe57a15-63a1-4e79-8af4-6738e43e19c8).  
  
 Třetí úložiště konstruktor `(value_type)_Errcode` jako hodnotu kódu chyby a odkazy [generic_category](../standard-library/system-error-functions.md#generic_category).  
  
##  <a name="message"></a>error_code::Message  
 Vrací název kód chyby.  
  
```
string message() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `string` představující název kód chyby.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `category().message(value())`.  
  
##  <a name="op_eq_eq"></a>error_code::Operator ==  
 Testování rovnosti mezi `error_code` objekty.  
  
```
bool operator==(const error_code& right) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`right`|Objekt, který má být testována rovnosti.|  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud objekty jsou stejné; **false** Pokud objekty nejsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Vrací člena operátor `category() == right.category() && value == right.value()`.  
  
##  <a name="op_neq"></a>error_code::Operator! =  
 Testy nerovnost mezi `error_code` objekty.  
  
```
bool operator!=(const error_code& right) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`right`|Objekt, který má být testována nerovnost.|  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud `error_code` objekt není rovno `error_code` objekt předaný v `right`; v opačném případě **false**.  
  
### <a name="remarks"></a>Poznámky  
 Vrací člena operátor `!(*this == right)`.  
  
##  <a name="op_lt"></a>error_code::Operator&lt;  
 Testuje, pokud [error_code](http://msdn.microsoft.com/en-us/09c6ef90-b6f8-430a-b584-e168716c7e31) objekt je menší než `error_code` objekt předaná pro porovnání.  
  
```
bool operator<(const error_code& right) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`right`|Error_code objekt, který se má porovnat.|  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud `error_code` objekt je menší než `error_code` objekt předaná pro porovnání; V opačném **false**.  
  
### <a name="remarks"></a>Poznámky  
 Vrací člena operátor `category() < right.category() || category() == right.category() && value < right.value()`.  
  
##  <a name="op_eq"></a>error_code::Operator =  
 Přiřadí novou hodnotu výčtu k [error_code](http://msdn.microsoft.com/en-us/09c6ef90-b6f8-430a-b584-e168716c7e31) objektu.  
  
```
template <class _Enum>
typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type&
 operator=(_Enum _Errcode);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`_Errcode`|Hodnota výčtu přiřadit `error_code` objektu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `error_code` objekt, který je právě přiřazován nová hodnota výčtu člen funkce.  
  
### <a name="remarks"></a>Poznámky  
 Úložiště operátor člen `(value_type)_Errcode` jako hodnotu kódu chyby a odkazy [generic_category](../standard-library/system-error-functions.md#generic_category). Vrátí `*this`.  
  
##  <a name="op_bool"></a>error_code::Operator bool  
 Vrhá proměnné typu `error_code`.  
  
```
explicit operator bool() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Logická hodnota `error_code` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí hodnotu převoditelné na operátor `true` pouze v případě [hodnota](#value) není rovna hodnotě nula. Návratový typ je převést pouze na `bool`, nikoli k `void *` nebo jiné známé Skalární typy.  
  
##  <a name="value"></a>error_code::Value  
 Vrátí hodnotu kódu uložené chyby.  
  
```
value_type value() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota kódu uložené chyba typu [value_type](#value_type).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="value_type"></a>error_code::value_type  
 Typ, který představuje hodnotu kódu uložené chyby.  
  
```
typedef int value_type;
```  
  
### <a name="remarks"></a>Poznámky  
 Definici tohoto typu se jedná o synonymum `int`.  
  
## <a name="see-also"></a>Viz také  
 [error_category – třída](../standard-library/error-category-class.md)   
 [<system_error>](../standard-library/system-error.md)



