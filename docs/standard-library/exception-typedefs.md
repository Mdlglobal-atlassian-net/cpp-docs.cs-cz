---
title: '&lt;výjimka&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
ms.openlocfilehash: f71c03e0c0a2e7ea4f37a85e85628ccf630ea317
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368726"
---
# <a name="ltexceptiongt-typedefs"></a>&lt;výjimka&gt; typedefs

## <a name="exception_ptr"></a><a name="exception_ptr"></a>exception_ptr

Typ, který popisuje ukazatele na výjimku.

```cpp
typedef unspecified exception_ptr;
```

### <a name="remarks"></a>Poznámky

Nespecifikovaná vnitřní třída, která `exception_ptr` se používá k implementaci typu.

`exception_ptr` Objekt použijte k odkazování na aktuální výjimku nebo instanci výjimky zadané uživatelem. V implementaci společnosti Microsoft je výjimka reprezentována [strukturou EXCEPTION_RECORD.](/windows/win32/api/winnt/ns-winnt-exception_record) Každý `exception_ptr` objekt obsahuje referenční pole výjimky, `EXCEPTION_RECORD` které odkazuje na kopii struktury, která představuje výjimku.

Když deklarujete proměnnou, `exception_ptr` proměnná není přidružena k žádné výjimce. Tedy referenční pole výjimky je NULL. Takový `exception_ptr` objekt se nazývá *exception_ptr null*.

Pomocí `current_exception` funkce `make_exception_ptr` nebo přiřaďte `exception_ptr` objektu výjimku. Při přiřazení výjimky `exception_ptr` proměnné odkazuje referenční pole výjimky proměnné na kopii výjimky. Pokud není dostatek paměti pro kopírování výjimky, referenční pole výjimky odkazuje na kopii [výjimky std::bad_alloc.](../standard-library/bad-alloc-class.md) Pokud `current_exception` funkce `make_exception_ptr` nebo nemůže z kopírovat výjimku z `terminate` jiného důvodu, funkce volá funkci CRT k ukončení aktuálního procesu.

Navzdory svému názvu `exception_ptr` není objekt sám o sobě ukazatelem. Nedodržuje sémantiku ukazatele a nelze jej použít `->`s operátory přístupu člena ukazatele ( ) nebo dereference (*). Objekt `exception_ptr` nemá žádné veřejné datové členy nebo členské funkce.

**Porovnání:**

Můžete použít stejné `==`( ) a `!=`nerovno - `exception_ptr` ) operátory porovnat dva objekty. Operátory neporovnávají binární hodnotu (bitový vzor) `EXCEPTION_RECORD` struktur, které představují výjimky. Místo toho operátory porovnat adresy v referenčním `exception_ptr` poli výjimky objektů. V důsledku toho `exception_ptr` hodnota null a hodnota NULL porovnat jako rovné.

## <a name="terminate_handler"></a><a name="terminate_handler"></a>terminate_handler

Typ popisuje ukazatel na funkci vhodnou pro `terminate_handler`použití jako .

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje ukazatele na funkci vhodný pro použití jako obslužná rutina ukončení.

### <a name="example"></a>Příklad

Příklad použití aplikace naleznete `terminate_handler` [set_terminate.](../standard-library/exception-functions.md#set_terminate)

## <a name="unexpected_handler"></a><a name="unexpected_handler"></a>unexpected_handler

Typ popisuje ukazatel na funkci vhodnou pro `unexpected_handler`použití jako .

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>Příklad

Příklad použití aplikace naleznete `unexpected_handler` [set_unexpected.](../standard-library/exception-functions.md#set_unexpected)
