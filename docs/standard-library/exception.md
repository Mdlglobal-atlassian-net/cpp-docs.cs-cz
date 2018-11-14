---
title: '&lt;Výjimka&gt;'
ms.date: 11/04/2016
f1_keywords:
- <exception>
helpviewer_keywords:
- exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
ms.openlocfilehash: e599a725feb46eaa90023fdb9c999f5b2d159637
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522036"
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
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|Typ, který popisuje ukazatele na funkci vhodný pro použití jako `terminate_handler`.|
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|Typ, který popisuje ukazatele na funkci vhodný pro použití jako `unexpected_handler`.|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[current_exception](../standard-library/exception-functions.md#current_exception)|Získá ukazatel na aktuální výjimku.|
|[get_terminate –](../standard-library/exception-functions.md#get_terminate)|Získá aktuální `terminate_handler` funkce.|
|[get_unexpected](../standard-library/exception-functions.md#get_unexpected)|Získá aktuální `unexpected_handler` funkce.|
|[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)|Vytvoří `exception_ptr` objekt, který obsahuje kopii výjimky.|
|[rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)|Vyvolá výjimku předanou jako parametr.|
|[set_terminate](../standard-library/exception-functions.md#set_terminate)|Vytvoří novou `terminate_handler` která se má volat při ukončení programu.|
|[set_unexpected](../standard-library/exception-functions.md#set_unexpected)|Vytvoří novou `unexpected_handler` bude při k neočekávané výjimce.|
|[ukončit](../standard-library/exception-functions.md#terminate)|Zavolá obslužnou rutinu ukončení.|
|[uncaught_exception](../standard-library/exception-functions.md#uncaught_exception)|Vrátí **true** pouze v případě, že je vyvolaná výjimka právě zpracovávána.|
|[unexpected](../standard-library/exception-functions.md#unexpected)|Zavolá obslužnou rutinu neočekávané události.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[bad_exception – třída](../standard-library/bad-exception-class.md)|Tato třída popisuje výjimku, která mohou být vyvolány z `unexpected_handler`.|
|[exception – třída](../standard-library/exception-class.md)|Tato třída slouží jako základní třída pro všechny výjimky vyvolané některými výrazy a standardní knihovny C++.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
