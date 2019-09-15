---
title: _CrtSetReportFile
ms.date: 11/04/2016
api_name:
- _CrtSetReportFile
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
- CrtSetReportFile
- _CrtSetReportFile
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
ms.openlocfilehash: bf88bae40031f6e92d6f936ac8a50f85d6c4e36c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942283"
---
# <a name="_crtsetreportfile"></a>_CrtSetReportFile

Po použití [_CrtSetReportMode](crtsetreportmode.md) k určení **_CRTDBG_MODE_FILE**můžete zadat popisovač souboru pro příjem textu zprávy. **_CrtSetReportFile** se používá také v [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md) k určení cíle textu (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
_HFILE _CrtSetReportFile(
   int reportType,
   _HFILE reportFile
);
```

### <a name="parameters"></a>Parametry

*reportType*<br/>
Typ sestavy: **_CRT_WARN**, **_CRT_ERROR**a **_CRT_ASSERT**.

*reportFile*<br/>
Nový soubor sestavy pro *ReportType*.

## <a name="return-value"></a>Návratová hodnota

Po úspěšném dokončení vrátí **_CrtSetReportFile** předchozí soubor sestavy definovaný pro typ sestavy určený v *ReportType*. Pokud je předána neplatná hodnota pro *ReportType*, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **_CRTDBG_HFILE_ERROR**. Další informace najdete v tématech [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_CrtSetReportFile** se používá s funkcí [_CrtSetReportMode](crtsetreportmode.md) k definování cíle nebo cílů pro konkrétní typ sestavy generovaný **_CrtDbgReport**. Pokud byla volána **_CrtSetReportMode** pro přiřazení režimu generování sestav **_CRTDBG_MODE_FILE** pro konkrétní typ sestavy, **_CrtSetReportFile** by měla být volána k definování konkrétního souboru nebo datového proudu, který chcete použít jako cíl. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtSetReportFile** se během předběžného zpracování odeberou.

V následujícím seznamu jsou uvedeny dostupné možnosti pro *reportFile* a výsledné chování **_CrtDbgReport**. Tyto možnosti jsou definovány jako bitové příznaky v souboru Crtdbg. h.

- **popisovač souboru**

   Popisovač souboru, který bude cílem pro zprávy. Není proveden žádný pokus o ověření platnosti popisovače. Je nutné otevřít a zavřít popisovač souboru. Příklad:

   ```C
   HANDLE hLogFile;
   hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,
      FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,
      FILE_ATTRIBUTE_NORMAL, NULL);
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, hLogFile);

   _RPT0(_CRT_WARN,"file message\n");
   CloseHandle(hLogFile);
   ```

- **_CRTDBG_FILE_STDERR**

   Zapíše zprávu do **stderr**, kterou je možné přesměrovat takto:

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   Zapíše zprávu do **stdout**, kterou můžete přesměrovat.

- **_CRTDBG_REPORT_FILE**

   Vrátí aktuální režim sestavy.

Soubor sestavy používaný jednotlivými typy sestav lze samostatně kontrolovat. Například je možné určit, že *ReportType* **_CRT_ERROR** bude hlášen do **stderr**, zatímco *ReportType* **_CRT_ASSERT** být hlášen uživatelsky definovanému popisovači souboru nebo datovému proudu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou, **stdin**, **stdout**a **stderr**, musí být přesměrované před tím, než je funkce modulu runtime jazyka C můžou použít v aplikacích pro UWP. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

**Knihovna** Ladit verze pouze [funkcí knihoven CRT](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
