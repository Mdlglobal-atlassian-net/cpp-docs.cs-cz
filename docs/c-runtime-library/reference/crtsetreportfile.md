---
title: _CrtSetReportFile
ms.date: 11/04/2016
apiname:
- _CrtSetReportFile
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
- CrtSetReportFile
- _CrtSetReportFile
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
ms.openlocfilehash: 32a560e09c47468daf48c185e23d6e289c6d1d9b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464243"
---
# <a name="crtsetreportfile"></a>_CrtSetReportFile

Když použijete [_CrtSetReportMode](crtsetreportmode.md) k určení **_CRTDBG_MODE_FILE**, můžete zadat popisovač souboru k přijetí textu zprávy. **_CrtSetReportFile** také používá [_CrtDbgReport _crtdbgreportw –](crtdbgreport-crtdbgreportw.md) k určení cíle textu (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
_HFILE _CrtSetReportFile(
   int reportType,
   _HFILE reportFile
);
```

### <a name="parameters"></a>Parametry

*reportType*<br/>
Typ sestavy: **_CRT_WARN**, **_CRT_ERROR**, a **_CRT_ASSERT**.

*reportFile*<br/>
Nový soubor sestavy pro *reportType*.

## <a name="return-value"></a>Návratová hodnota

Při úspěšném dokončení **_CrtSetReportFile** vrátí předchozí soubor sestavy definovaný pro typ sestavy určený v *reportType*. Pokud je předána neplatná hodnota *reportType*, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **_CRTDBG_HFILE_ERROR**. Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_CrtSetReportFile** se používá s [_CrtSetReportMode](crtsetreportmode.md) funkce k definování cíle nebo cílů pro typ konkrétní sestavy generované **_CrtDbgReport**. Když **_CrtSetReportMode** byla volána přiřadit **_CRTDBG_MODE_FILE** reporting režim pro konkrétní typ sestavy, **_CrtSetReportFile** by měla být volána pro definování konkrétního souboru nebo datový proud použít jako cíl. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_CrtSetReportFile** odstraněna během předběžného zpracování.

Následující seznam ukazuje dostupné možnosti pro *reportFile* a výsledné chování **_CrtDbgReport**. Tyto možnosti jsou definovány jako bitové příznaky v souboru Crtdbg.h.

- **popisovač souboru**

   Popisovač souboru, který bude cílem pro zprávy. Ověření platnosti popisovače nejsou provedeny žádné pokusy. Musíte otevřít a zavřít popisovač souboru. Příklad:

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

   Zapíše zprávu do **stderr**, který může být přesměrován takto:

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   Zapíše zprávu do **stdout**, který lze přesměrovat.

- **_CRTDBG_REPORT_FILE**

   Vrátí aktuální režim sestavy.

Soubor sestavy používaný každý typ sestavy lze ovládat samostatně. Například je možné určit, že *reportType* z **_CRT_ERROR** hlášené pro **stderr**, zatímco *reportType* z **_CRT_ASSERT** oznámený popisovač uživatelem definovaného souboru nebo datového proudu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UPW). Standardní datový proud popisovačů, které jsou spojeny s konzolou, **stdin**, **stdout**, a **stderr**, musí být přesměrován před funkcí jazyka C za běhu můžete použít v aplikacích pro UWP . Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

**Knihovny:** ladicí verze [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
