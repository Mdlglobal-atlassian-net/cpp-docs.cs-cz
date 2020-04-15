---
title: _set_new_mode
ms.date: 4/2/2020
api_name:
- _set_new_mode
- _o__set_new_mode
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_new_mode
- _set_new_mode
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
ms.openlocfilehash: 3a27717d65714de54f477e4e2b3f243c4631fd8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332321"
---
# <a name="_set_new_mode"></a>_set_new_mode

Nastaví nový režim obslužné rutiny pro **malloc**.

## <a name="syntax"></a>Syntaxe

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Parametry

*newhandlermode*<br/>
Nový režim obslužné rutiny pro **malloc**; platná hodnota je 0 nebo 1.

## <a name="return-value"></a>Návratová hodnota

Vrátí předchozí režim obslužné rutiny nastavený pro **malloc**. Vrácená hodnota 1 označuje, že při selhání připřidělování paměti **malloc** dříve volal rutiny obslužné rutiny obslužné rutiny; vrácená hodnota 0 znamená, že tomu tak nebylo. Pokud *argument newhandlermode* se nerovná 0 nebo 1, vrátí -1.

## <a name="remarks"></a>Poznámky

Funkce **_set_new_mode** C++ nastaví nový režim obslužné rutiny pro [malloc](malloc.md). Nový režim obslužné rutiny označuje, zda při selhání **malloc** volá novou rutinu obslužné rutiny nastavenou [_set_new_handler](set-new-handler.md). Ve výchozím nastavení **malloc** nevolá novou rutinu obslužné rutiny při selhání přidělení paměti. Můžete přepsat toto výchozí chování tak, že když **malloc** selže přidělit paměť, **malloc** volá rutinu nové obslužné rutiny stejným způsobem, jako **nový** operátor, když se nezdaří ze stejného důvodu. Další informace naleznete v [nových](../../cpp/new-operator-cpp.md) a [odstranění](../../cpp/delete-operator-cpp.md) operátorů v *referenční příručce jazyka C++*. Chcete-li přepsat výchozí, volejte:

```cpp
_set_new_mode(1);
```

brzy ve vašem programu nebo odkaz s Newmode.obj (viz [Možnosti odkazu](../../c-runtime-library/link-options.md)).

Tato funkce ověřuje jeho parametr. Pokud *newhandlermode* je něco jiného než 0 nebo 1, funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, <strong>_set_new_mode</strong> vrátí -1 `EINVAL`a nastaví **errno** na .

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Zdarma](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
