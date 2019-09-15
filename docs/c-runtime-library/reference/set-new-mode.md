---
title: _set_new_mode
ms.date: 11/04/2016
api_name:
- _set_new_mode
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
ms.openlocfilehash: b248f1c97b1ec334b7441f33862b90473e08993f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948444"
---
# <a name="_set_new_mode"></a>_set_new_mode

Nastaví nový režim obslužné rutiny **pro stav**.

## <a name="syntax"></a>Syntaxe

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Parametry

*newhandlermode*<br/>
Nový režim obslužné rutiny **pro:** platná hodnota je 0 nebo 1.

## <a name="return-value"></a>Návratová hodnota

Vrátí předchozí sadu obslužné rutiny pro **metodu**pro vytvoření. Návratová hodnota 1 znamená, že při selhání přidělení paměti, **je dřív volána** nová rutina obslužné rutiny; Návratová hodnota 0 značí, že nebyla. Pokud argument *newhandlermode* není roven 0 nebo 1, vrátí hodnotu-1.

## <a name="remarks"></a>Poznámky

C++ Funkce **_set_new_mode** nastaví nový režim obslužné rutiny pro [stav](malloc.md)". Nový režim obslužné rutiny **označuje, zda je při** selhání zavolána nová rutina obslužné rutiny nastavenou na [_set_new_handler](set-new-handler.md). Ve výchozím nastavení nevolá hodnota \ nevolá novou rutinu obslužné rutiny při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, aby se při neúspěšném přidělení paměti nezdařila **volání nové** rutiny obslužné rutiny stejným způsobem jako operátor **New** , když dojde **k chybě ze** stejného důvodu. Další informace naleznete v tématu operátory [New](../../cpp/new-operator-cpp.md) a [Delete](../../cpp/delete-operator-cpp.md) v  *C++ referenční příručce jazyka*. Chcete-li přepsat výchozí hodnotu, zavolejte:

```cpp
_set_new_mode(1);
```

na začátku v programu nebo propojení s NewMode. obj (viz [možnosti propojení](../../c-runtime-library/link-options.md)).

Tato funkce ověří svůj parametr. Pokud je *newhandlermode* cokoli jiného než 0 nebo 1, funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí <strong>_set_new_mode</strong> hodnotu-1 a nastaví **errno** na `EINVAL`.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_new_mode**|\<New. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
