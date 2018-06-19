---
title: '&lt;výjimka&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <exception>
dev_langs:
- C++
helpviewer_keywords:
- exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbd57085225bb21b9f7ce8bd34c537d3bc414797
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845814"
---
# <a name="ltexceptiongt"></a>&lt;Výjimka&gt;

Definuje několik typů a funkcí, které se týkají zpracování výjimek. Zpracování výjimek se používá v situacích, ve kterých lze systém zotavit z chyby. Poskytuje prostředky pro vrácení vykonávání z funkce do programu. Cílem začlenění zpracování výjimek je zvýšit robustnost programu a poskytnout řádný způsob zotavení z chyby.

## <a name="syntax"></a>Syntaxe

```cpp
#include <exception>

```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)|Typ, který popisuje ukazatele na výjimku.|
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|Typ, který popisuje ukazatel na funkci, která je vhodná pro použití jako `terminate_handler`.|
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|Typ, který popisuje ukazatel na funkci, která je vhodná pro použití jako `unexpected_handler`.|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[current_exception](../standard-library/exception-functions.md#current_exception)|Získá ukazatel na aktuální výjimku.|
|[get_terminate –](../standard-library/exception-functions.md#get_terminate)|Získá aktuální `terminate_handler` funkce.|
|[get_unexpected](../standard-library/exception-functions.md#get_unexpected)|Získá aktuální `unexpected_handler` funkce.|
|[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)|Vytvoří `exception_ptr` objekt, který obsahuje kopii výjimku.|
|[rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)|Vyvolá výjimku předanou jako parametr.|
|[set_terminate](../standard-library/exception-functions.md#set_terminate)|Vytvoří nový `terminate_handler` má být volána v ukončení programu.|
|[set_unexpected](../standard-library/exception-functions.md#set_unexpected)|Vytvoří nový `unexpected_handler` být, když je k neočekávané výjimce došlo.|
|[Ukončení](../standard-library/exception-functions.md#terminate)|Zavolá obslužnou rutinu ukončení.|
|[uncaught_exception](../standard-library/exception-functions.md#uncaught_exception)|Vrátí **true** pouze v případě, že vyvolaná výjimka je aktuálně zpracovávána.|
|[unexpected](../standard-library/exception-functions.md#unexpected)|Zavolá obslužnou rutinu neočekávané události.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[bad_exception – třída](../standard-library/bad-exception-class.md)|Třída popisuje výjimku, která může být vyvolána z `unexpected_handler`.|
|[exception – třída](../standard-library/exception-class.md)|Třída slouží jako základní třída pro všechny výjimky vydané určité výrazy a standardní knihovny C++.|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
