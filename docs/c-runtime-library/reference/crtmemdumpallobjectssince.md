---
title: _Crtmemdumpallobjectssince – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _CrtMemDumpAllObjectsSince
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
apitype: DLLExport
f1_keywords:
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
dev_langs:
- C++
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 30d502daad881417035a10b0a7ef3f4efcc41b4f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince

Vypíše informace o objektech v haldě od začátku spuštění programu, nebo ze stavu zadaného haldy (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void _CrtMemDumpAllObjectsSince(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Parametry

*Stav* ukazatel na stavu haldy zahájíte vypsání z nebo **NULL**.

## <a name="remarks"></a>Poznámky

**_Crtmemdumpallobjectssince –** funkce výpisy ladění informace hlavičky objektů přidělené v haldě ve formě uživatelem čitelný. Informace o výpisu lze aplikace ke sledování přidělování a zjišťování problémů paměti. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání **_crtmemdumpallobjectssince –** jsou odebrány při předběžném zpracování.

**_Crtmemdumpallobjectssince –** používá hodnotu *stavu* parametr k určení, kam inicializace operace výpisu. Zahájíte vypsání ze zadaného haldy stavu, *stavu* parametr musí být ukazatel na **_crtmemstate –** struktura, která má byla vyplněna objektem [_crtmemcheckpoint –](crtmemcheckpoint.md) před **_Crtmemdumpallobjectssince –** byla volána. Když *stavu* je **NULL**, funkce začne výpisu od začátku spuštění programu.

Pokud je aplikace nainstalována funkce háku výpisu voláním [_crtsetdumpclient –](crtsetdumpclient.md), potom pokaždé, když **_crtmemdumpallobjectssince –** Vypíše informace o **_client_block –** typ bloku, zavolá funkci výpisu zadané aplikace. Ve výchozím nastavení, interní bloky C Runtime (**_crt_block –**) nejsou zahrnuty do operace výpisu paměti. [_Crtsetdbgflag –](crtsetdbgflag.md) funkce slouží k zapnutí **_crtdbg_check_crt_df –** bit z **_crtdbgflag –** zahrnout tyto bloky. Kromě toho bloky označen jako vydání nebo ignorovat (**_free_block –**, **_ignore_block –**) nejsou součástí výpis stavu paměti.

Další informace o stavu funkce hald a **_crtmemstate –** struktury najdete v tématu [funkce vytváření sestav stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Příklad, jak pomocí **_crtmemdumpallobjectssince –**, najdete v části [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
