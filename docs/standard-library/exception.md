---
title: '&lt;Výjimka&gt;'
ms.date: 11/04/2016
f1_keywords:
- <exception>
helpviewer_keywords:
- exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
ms.openlocfilehash: 5036f2efc782c3b2f385960cd9cbf6935212f720
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240770"
---
# <a name="ltexceptiongt"></a>&lt;Výjimka&gt;

Definuje několik typů a funkcí, které se týkají zpracování výjimek. Zpracování výjimek se používá v situacích, ve kterých lze systém zotavit z chyby. Poskytuje prostředky pro vrácení vykonávání z funkce do programu. Cílem začlenění zpracování výjimek je zvýšit robustnost programu a poskytnout řádný způsob zotavení z chyby.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<výjimky >

**Namespace:** std

## <a name="members"></a>Členové

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)|Typ, který popisuje ukazatele na výjimku.|
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|Typ, který popisuje ukazatele na funkci vhodný pro použití jako `terminate_handler`.|
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|Typ, který popisuje ukazatele na funkci vhodný pro použití jako `unexpected_handler`.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[current_exception](../standard-library/exception-functions.md#current_exception)|Získá ukazatel na aktuální výjimku.|
|[get_terminate](../standard-library/exception-functions.md#get_terminate)|Získá aktuální `terminate_handler` funkce.|
|[get_unexpected](../standard-library/exception-functions.md#get_unexpected)|Získá aktuální `unexpected_handler` funkce.|
|[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)|Vytvoří `exception_ptr` objekt, který obsahuje kopii výjimky.|
|[rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)|Vyvolá výjimku předanou jako parametr.|
|[rethrow_if_nested](../standard-library/exception-functions.md#rethrow_if_nested)|Přetypování a vyvolá výjimku, pokud je vnořený.|
|[set_terminate](../standard-library/exception-functions.md#set_terminate)|Vytvoří novou `terminate_handler` která se má volat při ukončení programu.|
|[set_unexpected](../standard-library/exception-functions.md#set_unexpected)|Vytvoří novou `unexpected_handler` bude při k neočekávané výjimce.|
|[ukončit](../standard-library/exception-functions.md#terminate)|Zavolá obslužnou rutinu ukončení.|
|[throw_with_nested](../standard-library/exception-functions.md#throw_with_nested)|Vyvolá výjimku, pokud je vnořený.|
|[uncaught_exception](../standard-library/exception-functions.md#uncaught_exception)|Vrátí **true** pouze v případě, že je vyvolaná výjimka právě zpracovávána.|
|[unexpected](../standard-library/exception-functions.md#unexpected)|Zavolá obslužnou rutinu neočekávané události.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[bad_exception – třída](../standard-library/bad-exception-class.md)|Tato třída popisuje výjimku, která mohou být vyvolány z `unexpected_handler`.|
|[exception – třída](../standard-library/exception-class.md)|Tato třída slouží jako základní třída pro všechny výjimky vyvolané některými výrazy a standardní knihovny C++.|
|[nested_exception třídy](../standard-library/nested-exception-class.md)|Tato třída popisuje výjimku, která můžete zachytit a ukládají pro pozdější použití.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
