---
title: _CrtDoForAllClientObjects
ms.date: 11/04/2016
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
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
ms.openlocfilehash: 86268bd9ac49c8ea27f715404236bcb9291f5d8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339712"
---
# <a name="crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

Volá funkci poskytované aplikací pro všechny **_CLIENT_BLOCK** typy v haldě (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>Parametry

*pfn*<br/>
Ukazatel na funkci zpětného volání funkce poskytované aplikací. První parametr této funkce se odkazuje na data. Druhý parametr není ukazatel kontextu, který se předává do volání k **_CrtDoForAllClientObjects**.

*context*<br/>
Ukazatel na kontext, který poskytované aplikací má předat do funkce poskytované aplikací.

## <a name="remarks"></a>Poznámky

**_CrtDoForAllClientObjects** funkce hledá propojeného seznamu haldy pro bloky paměti se **_CLIENT_BLOCK** typu a volání funkce poskytované aplikací bloku tohoto typu se nachází. Nalezené bloku a *kontextu* parametru jsou předány jako argumenty funkce poskytované aplikací. Během ladění aplikace můžete sledovat konkrétní skupinu přidělení explicitně voláním ladění funkcí haldy pro přidělení paměti a určení, že bloky přiřadit **_CLIENT_BLOCK** typ bloku. Tyto bloky můžete potom samostatně sledovány a jinak hlášeny na během detekce nevrácení a vykazování stavu paměti.

Pokud **_CRTDBG_ALLOC_MEM_DF** bitové pole [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) není zapnutý příznak **_CrtDoForAllClientObjects** okamžitě vrátí. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_CrtDoForAllClientObjects** odstraněna během předběžného zpracování.

Další informace o **_CLIENT_BLOCK** zadejte a jak mohou využívat jiné funkce ladění, naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Pokud *pfn* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je nastavena na **EINVAL** a funkce vrátí.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>, \<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

**Knihovny:** Ladicí verze knihoven universal C Runtime pouze.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[Funkce vykazování stavu haldy](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
