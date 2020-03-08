---
title: výjimka &lt;&gt; definice typedef
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
ms.openlocfilehash: aba17b7bf052b6974bf849f60ff895b8e84a1092
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854901"
---
# <a name="ltexceptiongt-typedefs"></a>výjimka &lt;&gt; definice typedef

## <a name="exception_ptr"></a>exception_ptr

Typ, který popisuje ukazatele na výjimku.

```cpp
typedef unspecified exception_ptr;
```

### <a name="remarks"></a>Poznámky

Nespecifikovaná interní třída, která se používá k implementaci `exception_ptr`ho typu.

Použijte objekt `exception_ptr` pro odkazování na aktuální výjimku nebo instanci uživatelsky definované výjimky. V implementaci společnosti Microsoft je výjimka představována [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record) strukturou. Každý objekt `exception_ptr` obsahuje referenční pole výjimky, které odkazuje na kopii `EXCEPTION_RECORD` struktury, která představuje výjimku.

Pokud deklarujete `exception_ptr` proměnnou, proměnná není přidružena k žádné výjimce. Tedy referenční pole výjimky je NULL. Takový objekt `exception_ptr` se nazývá *exception_ptr null*.

K přiřazení výjimky objektu `exception_ptr` použijte funkci `current_exception` nebo `make_exception_ptr`. Pokud přiřadíte výjimku `exception_ptr` proměnné, referenční pole výjimky proměnné odkazuje na kopii výjimky. Pokud není k dispozici dostatek paměti ke zkopírování výjimky, referenční pole výjimky odkazuje na kopii výjimky [std:: bad_alloc](../standard-library/bad-alloc-class.md) . Pokud funkce `current_exception` nebo `make_exception_ptr` nemůže výjimku kopírovat z jakéhokoli jiného důvodu, funkce volá funkci `terminate` CRT pro ukončení aktuálního procesu.

Bez ohledu na název `exception_ptr` objekt není ukazatelem. Nedodržuje sémantiku ukazatele a nelze jej použít s operátory přístupu členů ukazatele (`->`) nebo dereference (*). Objekt `exception_ptr` nemá žádné veřejné datové členy ani členské funkce.

**Rovnost**

K porovnání dvou objektů `exception_ptr` lze použít operátory EQUAL (`==`) a not equal (`!=`). Operátory neporovnání binární hodnoty (bitového vzoru) `EXCEPTION_RECORD` struktury, které reprezentují výjimky. Místo toho operátory porovnávají adresy v referenčním poli výjimky objektů `exception_ptr`. V důsledku toho je `exception_ptr` null a hodnota NULL porovnána jako shodná.

## <a name="terminate_handler"></a>terminate_handler

Typ popisuje ukazatel na funkci vhodnou pro použití jako `terminate_handler`.

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje ukazatele na funkci vhodný pro použití jako obslužná rutina ukončení.

### <a name="example"></a>Příklad

Příklad použití `terminate_handler`naleznete v tématu [set_terminate](../standard-library/exception-functions.md#set_terminate) .

## <a name="unexpected_handler"></a>unexpected_handler

Typ popisuje ukazatel na funkci vhodnou pro použití jako `unexpected_handler`.

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>Příklad

Příklad použití `unexpected_handler`naleznete v tématu [set_unexpected](../standard-library/exception-functions.md#set_unexpected) .
