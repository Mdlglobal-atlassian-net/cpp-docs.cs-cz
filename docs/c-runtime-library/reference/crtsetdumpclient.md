---
title: _CrtSetDumpClient
ms.date: 11/04/2016
api_name:
- _CrtSetDumpClient
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtSetDumpClient
- CrtSetDumpClient
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
ms.openlocfilehash: f739f86a8410c66135704d61944d122a38c196a5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938563"
---
# <a name="_crtsetdumpclient"></a>_CrtSetDumpClient

Nainstaluje funkci definovanou aplikací k vypsání bloků paměti typu **_CLIENT_BLOCK** (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
_CRT_DUMP_CLIENT _CrtSetDumpClient( _CRT_DUMP_CLIENT dumpClient );
```

### <a name="parameters"></a>Parametry

*dumpClient*<br/>
Nová funkce výpisu paměti definovaná klientem, která se připojí k procesu výpisu paměti ladění C Runtime.

## <a name="return-value"></a>Návratová hodnota

Vrátí dříve definovanou funkci výpisu bloku klienta.

## <a name="remarks"></a>Poznámky

Funkce **_CrtSetDumpClient** umožňuje aplikaci připojit svoji vlastní funkci k vypsání objektů uložených v blocích paměti **_CLIENT_BLOCK** do procesu výpisu paměti ladění jazyka C za běhu. Výsledkem je, že pokaždé, když funkce výpisu ladění, jako je [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) nebo [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) , vypíše blok paměti **_CLIENT_BLOCK** , zavolá se i funkce výpisu paměti aplikace. **_CrtSetDumpClient** poskytuje aplikaci s jednoduchou metodou zjišťování nevracení paměti a ověřování nebo vytváření sestav obsahu dat uložených v blocích **_CLIENT_BLOCK** . Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtSetDumpClient** se během předběžného zpracování odeberou.

Funkce **_CrtSetDumpClient** nainstaluje novou funkci výpisu definované aplikace zadanou v *dumpClient* a vrátí dříve definovanou funkci výpisu paměti. Příkladem funkce výpisu bloku klienta je následující:

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

Argument *userPortion* je ukazatel na začátek části uživatelských dat bloku paměti a *velikostí bloku* určuje velikost přiděleného bloku paměti v bajtech. Funkce výpisu bloku klienta musí vracet **typ void**. Ukazatel na funkci výpisu klienta, která je předána do **_CrtSetDumpClient** , je typu **_CRT_DUMP_CLIENT**, jak je definováno v souboru Crtdbg. h:

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

Další informace o funkcích, které pracují s bloky paměti typu **_CLIENT_BLOCK** , najdete v tématu [funkce zavěšení bloků klienta](/visualstudio/debugger/client-block-hook-functions). Funkci [_CrtReportBlockType](crtreportblocktype.md) lze použít k vrácení informací o typech a podtypůch bloků.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtSetDumpClient**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtGetDumpClient](crtgetdumpclient.md)<br/>
