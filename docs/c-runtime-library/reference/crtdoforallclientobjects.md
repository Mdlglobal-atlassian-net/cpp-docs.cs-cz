---
title: _CrtDoForAllClientObjects
ms.date: 11/04/2016
api_name:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
ms.openlocfilehash: 4626df0db1956efd26ee267cb8cacf8ea4a4570c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942535"
---
# <a name="_crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

Volá funkci zadanou aplikací pro všechny typy **_CLIENT_BLOCK** v haldě (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>Parametry

*pfn*<br/>
Ukazatel na funkci zpětného volání funkce dodanou aplikací. První parametr této funkce odkazuje na data. Druhý parametr je kontextový ukazatel, který se předává volání **_CrtDoForAllClientObjects**.

*context*<br/>
Ukazatel na kontext poskytovaný aplikací, který bude předán funkci dodané aplikaci.

## <a name="remarks"></a>Poznámky

Funkce **_CrtDoForAllClientObjects** vyhledá v propojeném seznamu haldy paměťové bloky s typem **_CLIENT_BLOCK** a zavolá funkci dodanou aplikací, když se najde blok tohoto typu. Nalezený blok a *kontextový* parametr jsou předány jako argumenty funkce dodané aplikací. Během ladění může aplikace sledovat konkrétní skupinu přidělení explicitním voláním funkcí haldy ladění pro přidělení paměti a určením, že bloky mají přiřazen typ bloku **_CLIENT_BLOCK** . Tyto bloky je pak možné sledovat samostatně a nahlášené jinak během detekce úniku a vytváření sestav stavu paměti.

Pokud není zapnuté bitové pole **_CRTDBG_ALLOC_MEM_DF** příznaku [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) , **_CrtDoForAllClientObjects** se okamžitě vrátí. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtDoForAllClientObjects** se během předběžného zpracování odeberou.

Další informace o typu **_CLIENT_BLOCK** a o tom, jak jej lze použít v jiných funkcích ladění, naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Pokud má PFN **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je nastaveno na **EINVAL** a funkce vrátí.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>, \<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

**Knihovna** Ladit verze pouze knihoven runtime Universal C run-time.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[Funkce vytváření sestav o stavu haldy](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
