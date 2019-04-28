---
title: _set_new_mode
ms.date: 11/04/2016
apiname:
- _set_new_mode
apilocation:
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
apitype: DLLExport
f1_keywords:
- set_new_mode
- _set_new_mode
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
ms.openlocfilehash: 0228170e4ab5b55b4b061fa61a412766de77a063
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356599"
---
# <a name="setnewmode"></a>_set_new_mode

Nastaví nový režim obslužné rutiny pro **malloc**.

## <a name="syntax"></a>Syntaxe

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Parametry

*newhandlermode*<br/>
Nový režim obslužné rutiny pro **malloc**; platná hodnota je 0 nebo 1.

## <a name="return-value"></a>Návratová hodnota

Vrátí předchozí obslužnou rutinou set režimu pro **malloc**. Návratová hodnota 1 značí, že při selhání přidělení paměti, **malloc** dříve označované jako nové rutiny obsluhy; vrácená hodnota 0 označuje, že tomu tak není. Pokud *newhandlermode* argumentů není roven 0 nebo 1, vrátí hodnotu -1.

## <a name="remarks"></a>Poznámky

C++ **_Set_new_mode** funkce nastaví nový režim obslužné rutiny pro [malloc](malloc.md). Nový režim obslužné rutiny Určuje, zda je při selhání, **malloc** je volat nové rutiny obsluhy úmluvu [_set_new_handler](set-new-handler.md). Ve výchozím nastavení **malloc** nevolá nové rutiny obsluhy při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, aby, když **malloc** selže přidělování paměti, **malloc** volá nové rutiny obsluhy ve stejném způsobu, jakým **nové** operátor Když selže ze stejného důvodu. Další informace najdete v tématu [nové](../../cpp/new-operator-cpp.md) a [odstranit](../../cpp/delete-operator-cpp.md) operátory ve *referenční dokumentace jazyka C++*. Pokud chcete přepsat výchozí nastavení, volání:

```cpp
_set_new_mode(1);
```

zpočátku v programu nebo propojení s Newmode.obj (viz [možnosti propojení](../../c-runtime-library/link-options.md)).

Tato funkce ověřuje svůj parametr. Pokud *newhandlermode* je něco jinak než 0 nebo 1, funkce vyvolá obslužnou rutinu neplatného parametru, jako je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, <strong>_set_new_mode</strong> vrátí hodnotu -1 a nastaví **errno** k `EINVAL`.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
