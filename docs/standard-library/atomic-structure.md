---
title: "Atomic – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: atomic/std::atomic
dev_langs: C++
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3299f1bad01427723d3fcfabefd7924913d5690f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atomic-structure"></a>atomic – struktura
Popisuje objekt, který provádí atomické operací na uložené hodnoty typu `Ty`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Ty>
struct atomic;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Atomic](http://msdn.microsoft.com/Library/a538c43f-4d48-4308-ae1b-bab1839bccb8)|Vytvoří objekt atomic.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Atomic::Operator Ty – operátor](http://msdn.microsoft.com/Library/a366c700-c7a0-4bcb-8eb4-4b57dfaea065)|Přečte a vrátí uložené hodnoty. ([Atomic::Load –](http://msdn.microsoft.com/Library/05212726-cf8a-46fe-83d2-c16ac2abb7d1))|  
|[Atomic::Operator = – operátor](http://msdn.microsoft.com/Library/fe161d57-47ae-4bad-92bf-ce32ac8d5953)|Zadaná hodnota se používá k nahrazení uložené hodnoty. ([Atomic::Store –](http://msdn.microsoft.com/Library/84759413-d664-47ef-a1f3-a73c5a62007b))|  
|[Atomic::Operator ++ – operátor](http://msdn.microsoft.com/Library/492959e9-1ea8-4e02-a031-82b1b92e91a0)|Zvýší uložené hodnoty. Používat pouze specializací integrální a ukazatel.|  
|[Atomic::Operator += – operátor](http://msdn.microsoft.com/Library/9ec97aa2-c9d7-436b-943d-2989eb2617dd)|Přidá zadanou hodnotu do uložené hodnoty. Používat pouze specializací integrální a ukazatel.|  
|[Atomic::Operator – operátor](http://msdn.microsoft.com/Library/ad7c1ea7-1f6d-4a54-bf26-07630f749864)|Snižuje uložené hodnoty. Používat pouze specializací integrální a ukazatel.|  
|[Atomic::Operator-= – operátor](http://msdn.microsoft.com/Library/902d0d9f-88fd-4500-aa2d-1e50f443e77c)|Odečte zadanou hodnotu z uložené hodnoty. Používat pouze specializací integrální a ukazatel.|  
|[Atomic::Operator & = – operátor](http://msdn.microsoft.com/Library/90e730ac-12e1-4abb-98f5-4eadd6861a89)|Provede bitové `and` na zadanou hodnotu a uložené hodnoty. Používat pouze celočíselné specializací.|  
|[Atomic::Operator &#124; = – operátor](http://msdn.microsoft.com/Library/f105eacc-31a6-4906-abba-f1cf013599b2)|Provede bitové `or` na zadanou hodnotu a uložené hodnoty. Používat pouze celočíselné specializací.|  
|[Atomic::Operator ^ = – operátor](http://msdn.microsoft.com/Library/f2a4da9d-67e8-4249-9161-9998e72a33c2)|Provede bitové `exclusive or` na zadanou hodnotu a uložené hodnoty. Používat pouze celočíselné specializací.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[compare_exchange_strong](http://msdn.microsoft.com/Library/47bbf894-b28c-4ece-959e-67b3863cf4ed)|Provede `atomic_compare_and_exchange` operace na `this` a vrátí výsledek.|  
|[compare_exchange_weak](http://msdn.microsoft.com/Library/e15e421a-f7a3-4272-993a-f487d2242e4f)|Provede `weak_atomic_compare_and_exchange` operace na `this` a vrátí výsledek.|  
|[fetch_add](http://msdn.microsoft.com/Library/c68b91f2-6e8a-4ffa-8991-6bb6d466e1f3)|Přidá zadanou hodnotu do uložené hodnoty.|  
|[fetch_and](http://msdn.microsoft.com/Library/a9c83001-b72c-4085-9640-f63f866714b9)|Provede bitové `and` na zadanou hodnotu a uložené hodnoty.|  
|[fetch_or](http://msdn.microsoft.com/Library/4c532f7f-80c5-432a-b34b-48feacab8dca)|Provede bitové `or` na zadanou hodnotu a uložené hodnoty.|  
|[fetch_sub](http://msdn.microsoft.com/Library/8cc80d4b-0942-45a3-9db8-bbf339a903e4)|Odečte zadanou hodnotu z uložené hodnoty.|  
|[fetch_xor](http://msdn.microsoft.com/Library/92bbaff8-ee29-4a1e-aee4-d9d405285bfe)|Provede bitové `exclusive or` na zadanou hodnotu a uložené hodnoty.|  
|[is_lock_free](http://msdn.microsoft.com/Library/b99d5130-cdda-40a2-b14c-152b13a8ba45)|Určuje, zda atomické operací na `this` jsou *zamykání*. Atomickým typem je *zamykání* Pokud žádné atomické operací na daný typ používat zámky.|  
|[zatížení](http://msdn.microsoft.com/Library/05212726-cf8a-46fe-83d2-c16ac2abb7d1)|Přečte a vrátí uložené hodnoty.|  
|[úložiště](http://msdn.microsoft.com/Library/84759413-d664-47ef-a1f3-a73c5a62007b)|Zadaná hodnota se používá k nahrazení uložené hodnoty.|  
  
## <a name="remarks"></a>Poznámky  
 Typ `Ty` musí být *trivially kopírovatelná*. To znamená, pomocí [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) pro kopírování jeho bajtů musí vytvořit platný `Ty` objekt, který porovnává stejný jako původní objekt. `compare_exchange_weak` a `compare_exchange_strong` členské funkce použití [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) k určení, zda dva `Ty` jsou hodnoty stejné. Tato funkce nebude používat `Ty`-definované `operator==`. Členské funkce `atomic` použít `memcpy` ke kopírování hodnoty typu `Ty`.  
  
 Částečná specializace `atomic<Ty *>`, existuje pro všechny typy ukazatele. Specializace umožňuje přidání posun na hodnotu spravované ukazatel nebo odčítání posun z něj. Aritmetické operace trvat argument typu `ptrdiff_t` a upravit tento argument na základě velikosti `Ty` být konzistentní s aritmetické běžné adres.  
  
 Pro všechny integrální typy s výjimkou existuje specializace `bool`. Každý specializace poskytuje bohatou sadu metody pro atomické aritmetické a logických operací.  
  
||||  
|-|-|-|  
|`atomic<char>`|`atomic<signed char>`|`atomic<unsigned char>`|  
|`atomic<char16_t>`|`atomic<char32_t>`|`atomic<wchar_t>`|  
|`atomic<short>`|`atomic<unsigned short>`|`atomic<int>`|  
|`atomic<unsigned int>`|`atomic<long>`|`atomic<unsigned long>`|  
|`atomic<long long>`|`atomic<unsigned long long>`|  
  
 Integrální specializací jsou odvozeny od odpovídající `atomic_integral` typy. Například `atomic<unsigned int>` je odvozený od `atomic_uint`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<atomic >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [\<Atomic >](../standard-library/atomic.md)   
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)



