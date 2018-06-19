---
title: accelerator_view – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view:accelerator_view
- AMPRT/Concurrency::accelerator_view:create_marker
- AMPRT/Concurrency::accelerator_view:flush
- AMPRT/Concurrency::accelerator_view:get_accelerator
- AMPRT/Concurrency::accelerator_view:get_is_auto_selection
- AMPRT/Concurrency::accelerator_view:get_is_debug
- AMPRT/Concurrency::accelerator_view:get_queuing_mode
- AMPRT/Concurrency::accelerator_view:get_version
- AMPRT/Concurrency::accelerator_view:wait
- AMPRT/Concurrency::accelerator_view:accelerator
- AMPRT/Concurrency::accelerator_view:is_auto_selection
- AMPRT/Concurrency::accelerator_view:is_debug
- AMPRT/Concurrency::accelerator_view:queuing_mode
- AMPRT/Concurrency::accelerator_view:version
dev_langs:
- C++
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1aa0e365ac531a5e1bb7b87a38fc86fb20032d20
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692714"
---
# <a name="acceleratorview-class"></a>accelerator_view – třída
Představuje virtuální zařízení abstrakce na akcelerátor C++ AMP paralelní data.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
class accelerator_view;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[accelerator_view – konstruktor](#ctor)|Inicializuje novou instanci třídy `accelerator_view` třídy.|  
|[~ accelerator_view – destruktor](#dtor)|Zničí `accelerator_view` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[create_marker](#create_marker)|Vrátí budoucí sledování dokončení všech příkazů odeslání, pokud k tomuto `accelerator_view` objektu.|  
|[Vyprázdnění](#flush)|Odešle všechny čekající příkazy zařazených do fronty `accelerator_view` objekt, který chcete akcelerátor pro spuštění.|  
|[get_accelerator](#get_accelerator)|Vrátí `accelerator` objekt pro `accelerator_view` objektu.|  
|[get_is_auto_selection](#get_is_auto_selection)|Vrátí logickou hodnotu, která určuje, zda modul runtime automaticky vybere odpovídající akcelerátoru při `accelerator_view` předaný objekt [parallel_for_each –](concurrency-namespace-functions-amp.md#parallel_for_each).|  
|[get_is_debug](#get_is_debug)|Vrátí logickou hodnotu, která určuje, zda `accelerator_view` objekt má vrstvě ladění pro rozsáhlé zasílání zpráv o chybách povoleno.|  
|[get_queuing_mode –](#get_queuing_mode)|Vrátí hodnotu režimu front zpráv pro `accelerator_view` objektu.|  
|[get_version –](#get_version)|Vrátí verzi `accelerator_view`.|  
|[Počkej](#wait)|Všechny příkazy odeslané na čeká `accelerator_view` objekt, který chcete dokončit.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operator!=](#operator_neq)|Porovná tato `accelerator_view` objekt s jinou a vrátí `false` případě, že jsou totožné; jinak vrátí `true`.|  
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `accelerator_view` objekt s touto.|  
|[operator==](#operator_eq_eq)|Porovná tato `accelerator_view` objekt s jinou a vrátí `true` případě, že jsou totožné; jinak vrátí `false`.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[akcelerátoru](#accelerator)|Získá `accelerator` objekt pro `accelerator_view` objektu.|  
|[is_auto_selection](#is_auto_selection)|Získá logickou hodnotu, která určuje, zda modul runtime automaticky vybere odpovídající akcelerátoru při `accelerator_view` předaný objekt [parallel_for_each –](concurrency-namespace-functions-amp.md#parallel_for_each).|  
|[is_debug](#is_debug)|Získá logickou hodnotu, která určuje, zda `accelerator_view` objekt má vrstvě ladění pro rozsáhlé zasílání zpráv o chybách povoleno.|  
|[queuing_mode](#queuing_mode)|Získá režim front zpráv pro `accelerator_view` objektu.|  
|[Verze](#version)|Získá verzi akcelerátor.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `accelerator_view`  
  
### <a name="remarks"></a>Poznámky  
 `accelerator_view` Objekt představuje logické a izolované zobrazení akcelerátoru. Jeden fyzické výpočetní zařízení může mít mnoho logické, izolované `accelerator_view` objekty. Každý akcelerátoru má výchozí `accelerator_view` objektu. Další `accelerator_view` objekty mohou být vytvořeny.  
  
 Fyzické zařízení mohou být sdílená mezi mnoha vláken klienta. Vlákna klienta můžete použít spolupráce při stejné `accelerator_view` objektu akcelerátor nebo každý klient může komunikovat s výpočetní zařízení prostřednictvím nezávislou `accelerator_view` objekt pro izolaci od jiných podprocesů klienta.  
  
 `accelerator_view` Objekt může mít jednu ze dvou [queuing_mode – výčet](concurrency-namespace-enums-amp.md#queuing_mode) stavy. Pokud je režim služby Řízení front `immediate`, příkazy, jako `copy` a `parallel_for_each` se odesílají do odpovídající zařízení akcelerátoru co nejrychleji vracejí volajícímu. Pokud je režim služby Řízení front `deferred`, tyto příkazy jsou zařazeny do fronty ve frontě příkaz, který odpovídá `accelerator_view` objektu. Příkazy ve skutečnosti neodešlou do zařízení, dokud `flush()` je volána.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amprt.h  
  
 **Namespace:** souběžnosti  

## <a name="accelerator"></a> akcelerátoru 

Získá objekt akcelerátoru accelerator_view objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
## <a name="ctor"></a> accelerator_view 

Inicializuje novou instanci třídy accelerator_view zkopírováním existující `accelerator_view` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
accelerator_view( const accelerator_view & _Other );  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Objekt, který chcete kopírovat.  
  
## <a name="accelerator_view__create_marker"></a> create_marker 

Vrátí budoucí sledování dokončení všech příkazů odeslání, pokud k tomuto `accelerator_view` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
concurrency::completion_future create_marker();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Budoucí sledování dokončení všech příkazů odeslání, pokud k tomuto `accelerator_view` objektu.  
  
## <a name="flush"></a> Vyprázdnění 

Odešle, že všechny čekající příkazy zařazených do fronty pro accelerator_view objekt, který má akcelerátor pro spuštění.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void flush();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `void`.  

## <a name="accelerator_view__get_accelerator"></a> get_accelerator – 

Vrací objekt akcelerátoru accelerator_view objektu.
### <a name="syntax"></a>Syntaxe
```
accelerator get_accelerator() const;
```
### <a name="return-value"></a>Návratová hodnota
Objekt akcelerátoru accelerator_view objektu.

## <a name="accelerator_view__get_is_auto_selection"></a> get_is_auto_selection 

Vrátí logickou hodnotu, která určuje, zda modul runtime automaticky vybere odpovídající akcelerátoru když je předána accelerator_view [parallel_for_each –](concurrency-namespace-functions-amp.md#parallel_for_each).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool get_is_auto_selection() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud modul runtime automaticky vybere odpovídající akcelerátoru; v opačném `false`.  
  
## <a name="accelerator_view__get_is_debug"></a> get_is_debug – 

Vrátí logickou hodnotu, která označuje, zda má objekt accelerator_view vrstvě ladění pro rozsáhlé zasílání zpráv o chybách povoleno.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool get_is_debug() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Logická hodnota, která určuje, zda `accelerator_view` objekt má vrstvě ladění pro rozsáhlé zasílání zpráv o chybách povoleno.  

## <a name="accelerator_view__get_queuing_mode"></a> get_queuing_mode – 

Vrátí režim řazení do fronty pro objekt accelerator_view.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
queuing_mode get_queuing_mode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Režim řazení do fronty pro `accelerator_view` objektu.  
  
## <a name="accelerator_view__get_version"></a> get_version – 

Vrátí verzi accelerator_view.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
unsigned int get_version() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Verze `accelerator_view`.  
  
## <a name="accelerator_view__is_auto_selection"></a> is_auto_selection 

Získá logickou hodnotu, která určuje, zda modul runtime automaticky vybere odpovídající akcelerátoru když je předána accelerator_view [parallel_for_each –](concurrency-namespace-functions-amp.md#parallel_for_each).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
## <a name="accelerator_view__is_debug"></a> is_debug – 

Získá logickou hodnotu, která označuje, zda má objekt accelerator_view vrstvě ladění pro rozsáhlé zasílání zpráv o chybách povoleno.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
## <a name="accelerator_view__operator_neq"></a> Operator! = 

Porovná tento objekt accelerator_view s jinou a vrátí `false` případě, že jsou totožné; jinak vrátí `true`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator!= (    const accelerator_view & _Other ) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Objekt k porovnání s touto.  
  
### <a name="return-value"></a>Návratová hodnota  
 `false` Pokud dva objekty jsou stejné. v opačném `true`.  
  
## <a name="accelerator_view__operator_eq"></a> operátor = 

S touto zkopíruje obsah zadaného accelerator_view objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
accelerator_view & operator= (    const accelerator_view & _Other );  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Objekt, který chcete zkopírovat z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na upravenou `accelerator_view` objektu.  
  
## <a name="accelerator_view__operator_eq_eq"></a> Operator == 

Porovná tento objekt accelerator_view s jinou a vrátí `true` případě, že jsou totožné; jinak vrátí `false`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator= = (    const accelerator_view & _Other ) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Objekt k porovnání s touto.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud dva objekty jsou stejné. v opačném `false`.  
  
## <a name="accelerator_view__queuing_mode"></a> queuing_mode 

Získá řazení do fronty režim accelerator_view objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
## <a name="accelerator_view__version"></a> Verze 

Získá verzi accelerator_view.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
## <a name="accelerator_view__wait"></a> Počkej 

Čeká se na všechny příkazy odeslané na objekt accelerator_view ukončíte.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void wait();  
```  
  
#### <a name="return-value"></a>Návratová hodnota  
 Vrátí `void`.  
  
#### <a name="remarks"></a>Poznámky  
 Pokud [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) je `immediate`, tato metoda vrátí okamžitě bez blokování.  
  
##  <a name="dtor"></a> ~ accelerator_view 

 Zničí accelerator_view objektu.  
  
#### <a name="syntax"></a>Syntaxe  
  
```  
~accelerator_view();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
 
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
