---
title: "&lt;výjimka&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <exception>
dev_langs: C++
helpviewer_keywords: exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e152b51a5c33bc6e33622af2a08cb40886af67b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ltexceptiongt"></a>&lt;Výjimka&gt;
Definuje několik typů a funkcí, které se týkají zpracování výjimek. Zpracování výjimek se používá v situacích, ve kterých lze systém zotavit z chyby. Poskytuje prostředky pro vrácení vykonávání z funkce do programu. Cílem začlenění zpracování výjimek je zvýšit robustnost programu a poskytnout řádný způsob zotavení z chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <exception>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)|Typ, který popisuje ukazatele na výjimku.|  
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|Typ, který popisuje ukazatel na funkci, která je vhodná pro použití jako `terminate_handler`.|  
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|Typ, který popisuje ukazatel na funkci, která je vhodná pro použití jako `unexpected_handler`.|  
  
### <a name="functions"></a>Funkce  
  
|||  
|-|-|  
|[current_exception](../standard-library/exception-functions.md#current_exception)|Získá ukazatel na aktuální výjimku.|  
|[get_terminate –](../standard-library/exception-functions.md#get_terminate)|Získá aktuální `terminate_handler` funkce.|  
|[get_unexpected –](../standard-library/exception-functions.md#get_unexpected)|Získá aktuální `unexpected_handler` funkce.|  
|[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)|Vytvoří `exception_ptr` objekt, který obsahuje kopii výjimku.|  
|[rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)|Vyvolá výjimku předanou jako parametr.|  
|[set_terminate –](../standard-library/exception-functions.md#set_terminate)|Vytvoří nový `terminate_handler` má být volána v ukončení programu.|  
|[set_unexpected –](../standard-library/exception-functions.md#set_unexpected)|Vytvoří nový `unexpected_handler` být, když je k neočekávané výjimce došlo.|  
|[ukončení](../standard-library/exception-functions.md#terminate)|Zavolá obslužnou rutinu ukončení.|  
|[uncaught_exception](../standard-library/exception-functions.md#uncaught_exception)|Vrátí **true** pouze v případě, že vyvolaná výjimka je aktuálně zpracovávána.|  
|[neočekávané](../standard-library/exception-functions.md#unexpected)|Zavolá obslužnou rutinu neočekávané události.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[bad_exception – třída](../standard-library/bad-exception-class.md)|Třída popisuje výjimku, která může být vyvolána z `unexpected_handler`.|  
|[exception – třída](../standard-library/exception-class.md)|Třída slouží jako základní třída pro všechny výjimky vydané určité výrazy a standardní knihovny C++.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

