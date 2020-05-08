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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: f3635d462d2c7438ce985d74ff347120c02c82e0
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920092"
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

Funkce **_Set_new_mode** jazyka C++ nastaví nový režim obslužné rutiny pro stav [".](malloc.md) Nový režim obslužné rutiny **označuje, zda je při** selhání zavolána nová rutina obslužné rutiny, jak je nastavena [_set_new_handler](set-new-handler.md). Ve výchozím nastavení **malloc** nevolá hodnota \ nevolá novou rutinu obslužné rutiny při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, aby se při neúspěšném přidělení paměti nezdařila **volání nové** rutiny obslužné rutiny stejným způsobem jako operátor **New** , když dojde **k chybě ze** stejného důvodu. Další informace naleznete v tématu operátory [New](../../cpp/new-operator-cpp.md) a [Delete](../../cpp/delete-operator-cpp.md) v *Referenční příručce jazyka C++*. Chcete-li přepsat výchozí hodnotu, zavolejte:

```cpp
_set_new_mode(1);
```

na začátku v programu nebo propojení s NewMode. obj (viz [možnosti propojení](../../c-runtime-library/link-options.md)).

Tato funkce ověří svůj parametr. Pokud je *newhandlermode* cokoli jiného než 0 nebo 1, funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, <strong>_set_new_mode</strong> vrátí hodnotu-1 a nastaví **errno** na `EINVAL`.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_new_mode**|\<New. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[dost](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
