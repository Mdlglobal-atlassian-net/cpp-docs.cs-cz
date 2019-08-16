---
title: '&lt;výjimka&gt; definice typedef'
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
ms.openlocfilehash: aba17b7bf052b6974bf849f60ff895b8e84a1092
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501963"
---
# <a name="ltexceptiongt-typedefs"></a>&lt;výjimka&gt; definice typedef

## <a name="exception_ptr"></a>exception_ptr

Typ, který popisuje ukazatele na výjimku.

```cpp
typedef unspecified exception_ptr;
```

### <a name="remarks"></a>Poznámky

Neurčená interní třída, která se používá k implementaci `exception_ptr` typu.

`exception_ptr` Použijte objekt pro odkazování na aktuální výjimku nebo instanci uživatelsky definované výjimky. V implementaci společnosti Microsoft je výjimka představována strukturou [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record) . Každý `exception_ptr` objekt obsahuje referenční pole výjimky, které odkazuje na kopii `EXCEPTION_RECORD` struktury, která představuje výjimku.

Pokud deklarujete `exception_ptr` proměnnou, proměnná není přidružena k žádné výjimce. Tedy referenční pole výjimky je NULL. Takový objekt se nazývá exception_ptr s *hodnotou null.* `exception_ptr`

Pomocí funkce `current_exception` or `make_exception_ptr` můžete`exception_ptr` přiřadit výjimku objektu. Pokud přiřadíte výjimku `exception_ptr` proměnné, referenční pole výjimky proměnné odkazuje na kopii výjimky. Pokud není k dispozici dostatek paměti ke zkopírování výjimky, referenční pole výjimky odkazuje na kopii výjimky [std:: bad_alloc](../standard-library/bad-alloc-class.md) . Pokud funkce `make_exception_ptr` `terminate` nebo nemůže výjimku kopírovat z jakéhokoli jiného důvodu, funkce volá funkci CRT k ukončení aktuálního procesu. `current_exception`

Bez ohledu na jeho název `exception_ptr` objekt není ukazatelem. Nedodržuje sémantiku ukazatele a nelze jej použít s operátory přístupu členů ( `->`) a dereference (*). `exception_ptr` Objekt nemá žádné veřejné datové členy ani členské funkce.

**Rovnost**

Operátory EQUAL ( `==`) a not-equal ( `!=`) můžete použít k porovnání dvou `exception_ptr` objektů. Operátory neporovnání binární hodnoty (bitového vzoru) `EXCEPTION_RECORD` struktur, které reprezentují výjimky. Místo toho operátory porovnávají adresy v referenčním poli `exception_ptr` výjimky objektů. V důsledku toho je `exception_ptr` hodnota null a hodnota null porovnána jako shodná.

## <a name="terminate_handler"></a>terminate_handler

Typ popisuje ukazatel na funkci vhodnou pro použití jako `terminate_handler`.

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje ukazatele na funkci vhodný pro použití jako obslužná rutina ukončení.

### <a name="example"></a>Příklad

Příklad [](../standard-library/exception-functions.md#set_terminate) použití `terminate_handler`nástroje naleznete v tématu set_terminate.

## <a name="unexpected_handler"></a>unexpected_handler

Typ popisuje ukazatel na funkci vhodnou pro použití jako `unexpected_handler`.

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>Příklad

Příklad [](../standard-library/exception-functions.md#set_unexpected) použití `unexpected_handler`nástroje naleznete v tématu set_unexpected.
