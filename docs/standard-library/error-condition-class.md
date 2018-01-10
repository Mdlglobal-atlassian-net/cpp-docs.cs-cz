---
title: "error_condition – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- system_error/std::error_condition
- system_error/std::error_condition::value_type
- system_error/std::error_condition::assign
- system_error/std::error_condition::category
- system_error/std::error_condition::clear
- system_error/std::error_condition::message
- system_error/std::error_condition::operator bool
dev_langs: C++
helpviewer_keywords:
- std::error_condition
- std::error_condition::value_type
- std::error_condition::assign
- std::error_condition::category
- std::error_condition::clear
- std::error_condition::message
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eaf36a6f078fd41eee75788a2adbbb5efed7f5d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="errorcondition-class"></a>error_condition – třída
Představuje uživatelem definované chybové kódy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class error_condition;
```  
  
## <a name="remarks"></a>Poznámky  
 Objekt typu `error_condition` ukládá chybovou hodnotu kód a ukazatele na objekt, který představuje [kategorie](../standard-library/error-category-class.md) kódů chyb používá pro hlášené chyby definované uživatelem.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[error_condition –](#error_condition)|Vytvoří objekt typu `error_condition`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[value_type](#value_type)|Typ, který představuje hodnotu kódu uložené chyby.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[přiřazení](#assign)|Přiřadí hodnotu kódu chyby a kategorie chybový stav.|  
|[kategorie](#category)|Vrátí kategorie chyby.|  
|[Vymazat](#clear)|Vymaže hodnotu kódu chyby a kategorie.|  
|[message](#message)|Vrací název kód chyby.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[Operator ==](#op_eq_eq)|Testování rovnosti mezi `error_condition` objekty.|  
|[operator!=](#op_neq)|Testy nerovnost mezi `error_condition` objekty.|  
|[operátor <](#op_lt)|Testuje, pokud `error_condition` objekt je menší než `error_code` objekt předaná pro porovnání.|  
|[operátor =](#op_eq)|Přiřadí novou hodnotu výčtu k `error_condition` objektu.|  
|[operátor bool](#op_bool)|Vrhá proměnné typu `error_condition`.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<system_error – >  
  
 **Namespace:** – std  
  
##  <a name="assign"></a>error_condition::Assign  
 Přiřadí hodnotu kódu chyby a kategorie chybový stav.  
  
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
  
##  <a name="category"></a>error_condition::category  
 Vrátí kategorie chyby.  
  
```
const error_category& category() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na kategorie uložené chyby  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="clear"></a>error_condition::clear  
 Vymaže hodnotu kódu chyby a kategorie.  
  
```
clear();
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce ukládá nulová hodnota kódu chyby a odkazy [generic_category](../standard-library/system-error-functions.md#generic_category) objektu.  
  
##  <a name="error_condition"></a>error_condition::error_condition  
 Vytvoří objekt typu `error_condition`.  
  
```
error_condition();

error_condition(value_type val, const error_category& _Cat);

template <class _Enum>
error_condition(_Enum _Errcode,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_code>::type* = 0);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`val`|Hodnotu kód chyby pro ukládání `error_condition`.|  
|`_Cat`|Chyba kategorii, kterou chcete uložit `error_condition`.|  
|`_Errcode`|Hodnota výčtu pro ukládání `error_condition`.|  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor ukládá nulová hodnota kódu chyby a odkazy [generic_category](../standard-library/system-error-functions.md#generic_category).  
  
 Druhý konstruktor úložiště `val` jako hodnotu kódu chyby a ukazatel na [error_category](http://msdn.microsoft.com/en-us/6fe57a15-63a1-4e79-8af4-6738e43e19c8).  
  
 Třetí úložiště konstruktor `(value_type)_Errcode` jako hodnotu kódu chyby a odkazy [generic_category](../standard-library/system-error-functions.md#generic_category).  
  
##  <a name="message"></a>error_condition::Message  
 Vrací název kód chyby.  
  
```
string message() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `string` představující název kód chyby.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `category().message(value())`.  
  
##  <a name="op_eq_eq"></a>error_condition::Operator ==  
 Testování rovnosti mezi `error_condition` objekty.  
  
```
bool operator==(const error_condition& right) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`right`|Ojbect má být testována rovnosti.|  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud objekty jsou stejné; **false** Pokud objekty nejsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Vrací člena operátor `category() == right.category() && value == right.value()`.  
  
##  <a name="op_neq"></a>error_condition::Operator! =  
 Testy nerovnost mezi `error_condition` objekty.  
  
```
bool operator!=(const error_condition& right) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`right`|Objekt, který má být testována nerovnost.|  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud `error_condition` objekt není rovno `error_condition` objekt předaný v `right`; v opačném případě **false**.  
  
### <a name="remarks"></a>Poznámky  
 Vrací člena operátor `!(*this == right)`.  
  
##  <a name="op_lt"></a>error_condition::Operator&lt;  
 Testuje, pokud `error_condition` objekt je menší než `error_code` objekt předaná pro porovnání.  
  
```
bool operator<(const error_condition& right) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`right`|`error_condition` Objekt, který má být porovnána.|  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud `error_condition` objekt je menší než `error_condition` objekt předaná pro porovnání; V opačném **false**.  
  
### <a name="remarks"></a>Poznámky  
 Vrací člena operátor `category() < right.category() || category() == right.category() && value < right.value()`.  
  
##  <a name="op_eq"></a>error_condition::Operator =  
 Přiřadí novou hodnotu výčtu k `error_condition` objektu.  
  
```
template <class _Enum>
error_condition(_Enum error,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_condition>::type&
 operator=(Enum _Errcode);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`_Errcode`|Hodnota výčtu přiřadit `error_condition` objektu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `error_condition` objekt, který je právě přiřazován nová hodnota výčtu člen funkce.  
  
### <a name="remarks"></a>Poznámky  
 Úložiště operátor člen `(value_type)error` jako hodnotu kódu chyby a odkazy [generic_category](../standard-library/system-error-functions.md#generic_category). Vrátí `*this`.  
  
##  <a name="op_bool"></a>error_condition::Operator bool  
 Vrhá proměnné typu `error_condition`.  
  
```
explicit operator bool() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Logická hodnota `error_condition` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí hodnotu převoditelné na operátor `true` pouze v případě [hodnota](#value) není rovna hodnotě nula. Návratový typ je převést pouze na `bool`, nikoli k `void *` nebo jiné známé Skalární typy.  
  
##  <a name="value"></a>error_condition::Value  
 Vrátí hodnotu kódu uložené chyby.  
  
```
value_type value() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota kódu uložené chyba typu [value_type](#value_type).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="value_type"></a>error_condition::value_type  
 Typ, který představuje hodnotu kódu uložené chyby.  
  
```
typedef int value_type;
```  
  
### <a name="remarks"></a>Poznámky  
 Definice typu je synonymum pro `int`.  
  
## <a name="see-also"></a>Viz také  
 [error_category – třída](../standard-library/error-category-class.md)   
 [<system_error>](../standard-library/system-error.md)



