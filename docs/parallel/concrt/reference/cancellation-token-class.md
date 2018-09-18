---
title: cancellation_token – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::deregister_callback
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_cancelable
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_canceled
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::none
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::register_callback
dev_langs:
- C++
helpviewer_keywords:
- cancellation_token class
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 125d08def4a1fb801cb1b6c911d8c8c9c154c296
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037960"
---
# <a name="cancellationtoken-class"></a>cancellation_token – třída
`cancellation_token` Třída představuje možnost zjistit, zda některé operace požadují zrušení. Daný token lze přidružit `task_group`, `structured_task_group`, nebo `task` a poskytnout implicitní zrušení. Také ho můžete testovat na zrušení nebo mít registrace zpětného volání pro případ přidružený `cancellation_token_source` se zruší.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class cancellation_token;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[cancellation_token –](#ctor)||  
|[~ cancellation_token – destruktor](#dtor)||  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[deregister_callback](#deregister_callback)|Odebere zpětné volání dříve registrované `register` metoda na základě `cancellation_token_registration` vrácen objekt v době registrace.|  
|[is_cancelable –](#is_cancelable)|Vrací údaj o Určuje, zda tento token může být zrušený nebo nikoliv.|  
|[is_canceled](#is_canceled)|Vrátí `true` Pokud token byl zrušen.|  
|[None](#none)|Vrátí token zrušení, který nemůže být nikdy předmětem zrušení.|  
|[register_callback](#register_callback)|Zaregistruje funkci zpětného volání s tokenem. Pokud je token zrušen, bude proveden zpětného volání. Všimněte si, že pokud je token již zrušen v místě, kde tato metoda je volána, zpětné volání bude provedeno, okamžitě a synchronně.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operator!=](#operator_neq)||  
|[operátor =](#operator_eq)||  
|[operator==](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `cancellation_token`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** pplcancellation_token.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a> ~ cancellation_token – 

```
~cancellation_token();
```  
  
##  <a name="ctor"></a> cancellation_token – 

```
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
*_Src*<br/>
Cancellation_token – zkopírovat nebo přesunout.
  
##  <a name="deregister_callback"></a> deregister_callback – 

 Odebere zpětné volání dříve registrované `register` metoda na základě `cancellation_token_registration` vrácen objekt v době registrace.  
  
```
void deregister_callback(const cancellation_token_registration& _Registration) const;
```  
  
### <a name="parameters"></a>Parametry  
*_Registration*<br/>
`cancellation_token_registration` Odpovídající zpětnému volání pro zrušení registrace objektu. Tento token musí být nejprve navrácen z volání `register` metody.  
  
##  <a name="is_cancelable"></a> is_cancelable – 

 Vrací údaj o Určuje, zda tento token může být zrušený nebo nikoliv.  
  
```
bool is_cancelable() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Označení, zda tento token může být zrušený nebo nikoliv.  
  
##  <a name="is_canceled"></a> is_canceled – 

 Vrátí `true` Pokud token byl zrušen.  
  
```
bool is_canceled() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota `true` Pokud token byl zrušené; v opačném případě hodnota `false`.  
  
##  <a name="none"></a> None 

 Vrátí token zrušení, který nemůže být nikdy předmětem zrušení.  
  
```
static cancellation_token none();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Token zrušení, který nemůže být zrušen.  
  
##  <a name="operator_neq"></a> Operator! = 

```
bool operator!= (const cancellation_token& _Src) const;
```  
  
### <a name="parameters"></a>Parametry  
*_Src*<br/>
`cancellation_token` k porovnání.

### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="operator_eq"></a> operátor = 

```
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
*_Src*<br/>
`cancellation_token` Přiřadit.
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="operator_eq_eq"></a> Operator == 

```
bool operator== (const cancellation_token& _Src) const;
```  
  
### <a name="parameters"></a>Parametry  
*_Src*<br/>
`cancellation_token` k porovnání.
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="register_callback"></a> register_callback – 

 Zaregistruje funkci zpětného volání s tokenem. Pokud je token zrušen, bude proveden zpětného volání. Všimněte si, že pokud je token již zrušen v místě, kde tato metoda je volána, zpětné volání bude provedeno, okamžitě a synchronně.  
  
```
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```  
  
### <a name="parameters"></a>Parametry  
*_Function*<br/>
Typ objektu funkce, která bude volána zpět, když to `cancellation_token` se zruší.  
  
*_Func*<br/>
Objekt funkce, která bude volána zpět, když to `cancellation_token` se zruší.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `cancellation_token_registration` objekt, který lze využít v `deregister` metodu zrušení registrace již registrovaného zpětného volání a zabránit prováděné. Metoda vyvolá výjimku [invalid_operation –](invalid-operation-class.md) výjimku, pokud je volán na `cancellation_token` objekt, který byl vytvořen pomocí [cancellation_token::none](#none) metoda.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
