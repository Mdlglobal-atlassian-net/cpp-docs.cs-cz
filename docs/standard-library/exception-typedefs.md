---
title: '&lt;výjimka&gt; – definice TypeDef | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
author: corob-msft
ms.author: corob
ms.openlocfilehash: 93feda8c6359c5ec24fd4fd9dd38c632726b676b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197022"
---
# <a name="ltexceptiongt-typedefs"></a>&lt;výjimka&gt; – definice TypeDef

||||
|-|-|-|
|[exception_ptr](#exception_ptr)|[terminate_handler](#terminate_handler)|[unexpected_handler](#unexpected_handler)|

## <a name="exception_ptr"></a>  exception_ptr

Typ, který popisuje ukazatele na výjimku.

```cpp
typedef unspecified exception_ptr;
```

### <a name="remarks"></a>Poznámky

Neurčená vnitřní třída, která se používá k implementaci `exception_ptr` typu.

Použití `exception_ptr` pro odkázání na aktuální výjimku nebo instanci uživatelské výjimky. V implementaci společnosti Microsoft, je reprezentována výjimku [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-_exception_record) struktury. Každý `exception_ptr` objekt obsahuje referenční pole výjimky, která odkazuje na kopii `EXCEPTION_RECORD` struktura, která představuje výjimku.

Pokud deklarujete `exception_ptr` proměnné, proměnná není přidružen k žádné výjimce. Tedy referenční pole výjimky je NULL. Tyto `exception_ptr` objekt, se nazývá *nulový exception_ptr*.

Použití `current_exception` nebo `make_exception_ptr` funkce pro přiřazení výjimky do `exception_ptr` objektu. Při přiřazení výjimky do `exception_ptr` proměnné, referenční pole výjimky proměnné odkazuje na kopii výjimky. Pokud není dostatek paměti pro zkopírování výjimky, referenční pole výjimky odkazuje na kopii [std::bad_alloc](../standard-library/bad-alloc-class.md) výjimky. Pokud `current_exception` nebo `make_exception_ptr` funkce nemůže zkopírovat výjimku z jiného důvodu, zavolá funkce `terminate` CRT funkce pro ukončení aktuálního procesu.

Bez ohledu na její název `exception_ptr` objektu je sám není ukazatel. Nedodržuje sémantiku ukazatele a nelze použít s přístup ke členu ukazatel ( `->`) nebo operátory dereference (*). `exception_ptr` Objekt nemá žádné veřejné datové členy a členské funkce.

**Porovnání:**

Můžete použít rovnosti ( `==`) a není rovno ( `!=`) operátory pro porovnání dvou `exception_ptr` objekty. Operátory neporovnávají binární hodnoty (bitový vzor) z `EXCEPTION_RECORD` struktury, které představují výjimky. Místo toho operátory porovnávají adresy v referenčním poli výjimky z `exception_ptr` objekty. V důsledku toho s hodnotou null `exception_ptr` a hodnota NULL rovnají.

## <a name="terminate_handler"></a>  terminate_handler

Typ, který popisuje ukazatele na funkci vhodný pro použití jako `terminate_handler`.

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje ukazatele na funkci vhodný pro použití jako obslužná rutina ukončení.

### <a name="example"></a>Příklad

Zobrazit [set_terminate](../standard-library/exception-functions.md#set_terminate) příklad použití `terminate_handler`.

## <a name="unexpected_handler"></a>  unexpected_handler

Typ, který popisuje ukazatele na funkci vhodný pro použití jako `unexpected_handler`.

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>Příklad

Zobrazit [set_unexpected](../standard-library/exception-functions.md#set_unexpected) příklad použití `unexpected_handler`.

## <a name="see-also"></a>Viz také:

[\<výjimky >](../standard-library/exception.md)<br/>
