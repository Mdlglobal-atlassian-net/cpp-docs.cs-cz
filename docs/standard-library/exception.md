---
title: '&lt;jímka&gt;'
ms.date: 11/04/2016
f1_keywords:
- <exception>
helpviewer_keywords:
- exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
ms.openlocfilehash: 681baee5ac5d19e8b3ffdf37c37599c9cb68f253
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457907"
---
# <a name="ltexceptiongt"></a>&lt;jímka&gt;

Definuje několik typů a funkcí, které se týkají zpracování výjimek. Zpracování výjimek se používá v situacích, ve kterých lze systém zotavit z chyby. Poskytuje prostředky pro vrácení vykonávání z funkce do programu. Cílem začlenění zpracování výjimek je zvýšit robustnost programu a poskytnout řádný způsob zotavení z chyby.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> výjimky

**Obor názvů:** std

## <a name="members"></a>Členové

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)|Typ, který popisuje ukazatele na výjimku.|
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|Typ, který popisuje ukazatel na funkci vhodnou pro použití jako `terminate_handler`.|
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|Typ, který popisuje ukazatel na funkci vhodnou pro použití jako `unexpected_handler`.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[current_exception](../standard-library/exception-functions.md#current_exception)|Získá ukazatel na aktuální výjimku.|
|[get_terminate](../standard-library/exception-functions.md#get_terminate)|Získá aktuální `terminate_handler` funkci.|
|[get_unexpected](../standard-library/exception-functions.md#get_unexpected)|Získá aktuální `unexpected_handler` funkci.|
|[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)|`exception_ptr` Vytvoří objekt, který obsahuje kopii výjimky.|
|[rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)|Vyvolá výjimku předanou jako parametr.|
|[rethrow_if_nested](../standard-library/exception-functions.md#rethrow_if_nested)|Přetypování a vyvolá výjimku, pokud je vnořený.|
|[set_terminate](../standard-library/exception-functions.md#set_terminate)|Vytvoří nový `terminate_handler` , který se bude volat při ukončení programu.|
|[set_unexpected](../standard-library/exception-functions.md#set_unexpected)|Vytvoří novou `unexpected_handler` hodnotu, pokud dojde k neočekávané výjimce.|
|[ruší](../standard-library/exception-functions.md#terminate)|Zavolá obslužnou rutinu ukončení.|
|[throw_with_nested](../standard-library/exception-functions.md#throw_with_nested)|Vyvolá výjimku, je-li vnořeno.|
|[uncaught_exception](../standard-library/exception-functions.md#uncaught_exception)|Vrátí **hodnotu true** pouze v případě, že právě probíhá zpracování vyvolané výjimky.|
|[unexpected](../standard-library/exception-functions.md#unexpected)|Zavolá obslužnou rutinu neočekávané události.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[bad_exception – třída](../standard-library/bad-exception-class.md)|Třída popisuje výjimku, kterou lze vyvolat z `unexpected_handler`.|
|[exception – třída](../standard-library/exception-class.md)|Třída slouží jako základní třída pro všechny výjimky vyvolané některými výrazy a C++ standardní knihovnou.|
|[nested_exception – třída](../standard-library/nested-exception-class.md)|Třída popisuje výjimku, kterou lze zachytit a uložit pro pozdější použití.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
