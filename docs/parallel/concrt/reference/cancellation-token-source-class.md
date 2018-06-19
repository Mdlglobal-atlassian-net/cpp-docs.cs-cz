---
title: cancellation_token_source – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancel
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::create_linked_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::get_token
dev_langs:
- C++
helpviewer_keywords:
- cancellation_token_source class
ms.assetid: 3548b1a0-12b0-4334-95db-4bf57141c066
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 122a60496a92b3844f4e439e40650c429035dc33
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689672"
---
# <a name="cancellationtokensource-class"></a>cancellation_token_source – třída
`cancellation_token_source` Třída reprezentuje možnost zrušit některé možné zrušit operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class cancellation_token_source;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[cancellation_token_source](#ctor)|Přetíženo. Vytvoří nový `cancellation_token_source`. Zdroj lze příznak zrušení některé možné zrušit operaci.|  
|[~ cancellation_token_source – destruktor](#dtor)||  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Zrušit](#cancel)|Zruší token. Všechny `task_group`, `structured_task_group`, nebo `task` která využívá token na toto volání, budou zrušeny a způsobí výjimku na další bod přerušení.|  
|[create_linked_source –](#create_linked_source)|Přetíženo. Vytvoří `cancellation_token_source` po zadaný token se zruší, což je zrušena.|  
|[get_token](#get_token)|Vrátí token zrušení přidružený tento zdroj. Vrácený token pro zrušení se může dotazovat nebo zadejte zpětné volání, pokud dojde k zrušení.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operator!=](#operator_neq)||  
|[operátor =](#operator_eq)||  
|[operator==](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `cancellation_token_source`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** pplcancellation_token.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a> ~ cancellation_token_source 

```
~cancellation_token_source();
```  
  
##  <a name="cancel"></a> Zrušit 

 Zruší token. Všechny `task_group`, `structured_task_group`, nebo `task` která využívá token na toto volání, budou zrušeny a způsobí výjimku na další bod přerušení.  
  
```
void cancel() const;
```  
  
##  <a name="ctor"></a> cancellation_token_source 

 Vytvoří nový `cancellation_token_source`. Zdroj lze příznak zrušení některé možné zrušit operaci.  
  
```
cancellation_token_source();

cancellation_token_source(const cancellation_token_source& _Src);

cancellation_token_source(cancellation_token_source&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
##  <a name="create_linked_source"></a> create_linked_source – 

 Vytvoří `cancellation_token_source` po zadaný token se zruší, což je zrušena.  
  
```
static cancellation_token_source create_linked_source(
    cancellation_token& _Src);

template<typename _Iter>
static cancellation_token_source create_linked_source(_Iter _Begin, _Iter _End);
```  
  
### <a name="parameters"></a>Parametry  
 `_Iter`  
 `_Src`  
 Token, jejichž zrušení způsobí, že zrušení vrácený tokenu zdroje. Všimněte si, že vrácený tokenu zdroje se dají zrušit také nezávisle na zdroji obsažené v tomto parametru.  
  
 `_Begin`  
 Iterace standardní knihovna C++ odpovídající na začátek rozsahu tokeny pro naslouchání pro zrušení.  
  
 `_End`  
 Iterace standardní knihovna C++ odpovídající konec rozsahu tokeny pro naslouchání pro zrušení.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `cancellation_token_source` které se zruší, pokud token poskytovaný `_Src` parametr je zrušená.  
  
##  <a name="get_token"></a> get_token – 

 Vrátí token zrušení přidružený tento zdroj. Vrácený token pro zrušení se může dotazovat nebo zadejte zpětné volání, pokud dojde k zrušení.  
  
```
cancellation_token get_token() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Token zrušení přidružený tento zdroj.  
  
##  <a name="operator_neq"></a> Operator! = 

```
bool operator!= (const cancellation_token_source& _Src) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="operator_eq"></a> operátor = 

```
cancellation_token_source& operator= (const cancellation_token_source& _Src);

cancellation_token_source& operator= (cancellation_token_source&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="operator_eq_eq"></a> Operator == 

```
bool operator== (const cancellation_token_source& _Src) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
### <a name="return-value"></a>Návratová hodnota  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
