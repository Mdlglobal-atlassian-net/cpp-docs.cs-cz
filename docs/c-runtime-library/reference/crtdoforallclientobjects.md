---
title: _Crtdoforallclientobjects – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
dev_langs:
- C++
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 889c3c4060098927df08d785e85b64e7e7becc2c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397197"
---
# <a name="crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

Volání funkce poskytované aplikací pro všechny **_client_block –** typy v haldě (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>Parametry

*pfn* ukazatel na funkci zpětného volání funkce zadané aplikace. První parametr této funkce se odkazuje na data. Druhý parametr je ukazatel kontext, který je předán volání **_crtdoforallclientobjects –**.

*kontext* ukazatel na kontext zadané aplikace mají být předána do funkce zadané aplikace.

## <a name="remarks"></a>Poznámky

**_Crtdoforallclientobjects –** funkce vyhledá haldy odkazovaného seznamu pro bloky paměti s **_client_block –** typu a volání funkce poskytované aplikací při blok tohoto typu je nalezen. Nalezen bloku a *kontextu* parametru jsou funkci byl předán jako argumenty zadané aplikace. Během ladění, můžete aplikaci sledovat konkrétní skupinu přidělení explicitně voláním ladění funkce hald přidělit paměť a určení, že na bloky přiřadit **_client_block –** blokovat typu. Tyto bloky můžete pak sledovat samostatně a ohlášeny odlišně při zjištění paměti a vytváření sestav stavu paměti.

Pokud **_crtdbg_alloc_mem_df –** bit pole [_crtdbgflag –](../../c-runtime-library/crtdbgflag.md) není zapnut příznak, **_crtdoforallclientobjects –** hned vrátí. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání **_crtdoforallclientobjects –** jsou odebrány při předběžném zpracování.

Další informace o **_client_block –** zadejte a jak ho můžete používat další funkce ladění, najdete v části [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Pokud *pfn* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je nastaven na **einval –** a funkce vrátí hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>, \<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

**Knihovny:** ladicí verze universal C Runtime pouze knihovny.

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[Funkce vytváření sestav stavu haldy](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
