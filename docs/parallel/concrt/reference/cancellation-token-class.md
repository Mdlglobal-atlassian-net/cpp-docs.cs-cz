---
title: cancellation_token – třída | Microsoft Docs
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
ms.openlocfilehash: 5d8741763295e96f3d0c221b687c8ef62fbfc55c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695938"
---
# <a name="cancellationtoken-class"></a>cancellation_token – třída
`cancellation_token` Třída reprezentuje schopnosti určit, zda byla vyžádána některé operace zrušení. Daný token dají přidružit `task_group`, `structured_task_group`, nebo `task` zajistit implicitní zrušení. Můžete ho také dotazování pro zrušení nebo zpětné volání pro registrováno Pokud a při přidruženého `cancellation_token_source` je zrušená.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class cancellation_token;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[cancellation_token](#ctor)||  
|[~ cancellation_token – destruktor](#dtor)||  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[deregister_callback](#deregister_callback)|Odebere zpětné volání dříve registrován prostřednictvím `register` metoda na základě `cancellation_token_registration` objekt byl vrácen v době registrace.|  
|[is_cancelable –](#is_cancelable)|Vrátí údaj o tom, zda lze tento token zrušit nebo ne.|  
|[is_canceled](#is_canceled)|Vrátí `true` Pokud token byla zrušena.|  
|[None](#none)|Vrátí token zrušení, který může být nikdy předmětem zrušení.|  
|[register_callback](#register_callback)|Zaregistruje funkci zpětného volání s tokenem. Pokud token je zrušená, budou provedeny zpětné volání. Všimněte si, že pokud token je zrušena již v okamžiku, kdy tato metoda je volána, zpětné volání budou provedeny, okamžitě a synchronně.|  
  
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
  
##  <a name="dtor"></a> ~ cancellation_token 

```
~cancellation_token();
```  
  
##  <a name="ctor"></a> cancellation_token 

```
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
##  <a name="deregister_callback"></a> deregister_callback – 

 Odebere zpětné volání dříve registrován prostřednictvím `register` metoda na základě `cancellation_token_registration` objekt byl vrácen v době registrace.  
  
```
void deregister_callback(const cancellation_token_registration& _Registration) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Registration`  
 `cancellation_token_registration` Objekt odpovídající zpětného volání k se zrušila. Tento token musí mít byla předtím vrátila volání `register` metoda.  
  
##  <a name="is_cancelable"></a> is_cancelable – 

 Vrátí údaj o tom, zda lze tento token zrušit nebo ne.  
  
```
bool is_cancelable() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Údaj o tom, zda lze tento token zrušit nebo ne.  
  
##  <a name="is_canceled"></a> is_canceled – 

 Vrátí `true` Pokud token byla zrušena.  
  
```
bool is_canceled() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota `true` Pokud token bylo zrušené; jinak hodnota `false`.  
  
##  <a name="none"></a> None 

 Vrátí token zrušení, který může být nikdy předmětem zrušení.  
  
```
static cancellation_token none();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Token zrušení, který nelze zrušit.  
  
##  <a name="operator_neq"></a> Operator! = 

```
bool operator!= (const cancellation_token& _Src) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="operator_eq"></a> operátor = 

```
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="operator_eq_eq"></a> Operator == 

```
bool operator== (const cancellation_token& _Src) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="register_callback"></a> register_callback – 

 Zaregistruje funkci zpětného volání s tokenem. Pokud token je zrušená, budou provedeny zpětné volání. Všimněte si, že pokud token je zrušena již v okamžiku, kdy tato metoda je volána, zpětné volání budou provedeny, okamžitě a synchronně.  
  
```
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ objektu funkce, která bude volána při zálohování to `cancellation_token` je zrušená.  
  
 `_Func`  
 Funkce objektu, která bude volána při zálohování to `cancellation_token` je zrušená.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `cancellation_token_registration` objekt, který můžete použít v `deregister` metodu zrušení registrace dříve zaregistrovaný zpětného volání a zabránit prováděné. Vyvolá metodu [invalid_operation](invalid-operation-class.md) výjimka, pokud je volána na `cancellation_token` objekt, který byl vytvořen pomocí [cancellation_token::none –](#none) metoda.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
