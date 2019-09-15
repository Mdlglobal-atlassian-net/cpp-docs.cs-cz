---
title: _CrtSetReportHook2, _CrtSetReportHookW2
ms.date: 11/04/2016
api_name:
- _CrtSetReportHook2
- _CrtSetReportHookW2
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
- CrtSetReportHookW2
- CrtSetReportHook2
- _CrtSetReportHookW2
- _CrtSetReportHook2
helpviewer_keywords:
- CrtSetReportHook2 function
- _CrtSetReportHook2 function
- _CrtSetReportHookW2 function
- CrtSetReportHookW2 function
ms.assetid: 12e5f68d-c8a7-4b1a-9a75-72ba4a8592d0
ms.openlocfilehash: 37ec0cea3fb558a5926e6f9c707e0e5033a17222
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942222"
---
# <a name="_crtsetreporthook2-_crtsetreporthookw2"></a>_CrtSetReportHook2, _CrtSetReportHookW2

Nainstaluje nebo odinstaluje funkci vytváření sestav definovanou klientem, a to tak, že je zapojte do procesu generování sestav ladění C za běhu (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
int _CrtSetReportHook2(
   int mode,
   _CRT_REPORT_HOOK pfnNewHook
);
int _CrtSetReportHookW2(
   int mode,
   _CRT_REPORT_HOOKW pfnNewHook
);
```

### <a name="parameters"></a>Parametry

*Mode*<br/>
Akce, která se má provést: **_CRT_RPTHOOK_INSTALL** nebo **_CRT_RPTHOOK_REMOVE**.

*pfnNewHook*<br/>
Zavěšení sestavy pro instalaci nebo odebrání v rámci této funkce s úzkým znakem nebo verzí s velkým znakem

## <a name="return-value"></a>Návratová hodnota

-1 Pokud došlo k chybě, s **EINVAL** nebo **ENOMEM** sadou; v opačném případě vrátí počet odkazů *pfnNewHook* po volání.

## <a name="remarks"></a>Poznámky

**_CrtSetReportHook2** a **_CrtSetReportHookW2** umožňují připojit nebo odpojte funkci, zatímco [_CrtSetReportHook](crtsetreporthook.md) umožňuje připojit pouze funkci.

**_CrtSetReportHook2** nebo **_CrtSetReportHookW2** by měly být použity namísto **_CrtSetReportHook** , pokud je volání zavěšení provedeno v knihovně DLL a pokud je možné načíst více knihoven DLL a nastavit vlastní funkce zavěšení. V takové situaci mohou být knihovny DLL uvolněny v jiném pořadí, než jaké byly načteny a funkce Hooku může být ponechána na Nenačtené knihovně DLL. Pokud byly funkce zavěšení přidány pomocí **_CrtSetReportHook**, všechny výstupy ladění způsobí proces.

Jakékoli funkce zavěšení přidané pomocí **_CrtSetReportHook** jsou volány, pokud nejsou přidány žádné funkce připojení s **_CrtSetReportHook2** nebo **_CrtSetReportHookW2** , nebo pokud jsou všechny funkce připojení přidány pomocí **_CrtSetReportHook2** a **_ CrtSetReportHookW2** vrátí **hodnotu false**.

Verze této funkce je k dispozici ve verzi s velkým znakem. Funkce zavěšení sestav přebírají řetězec, jehož typ (šířku nebo zúžené znaky) se musí shodovat s použitou verzí této funkce. Použijte následující prototyp funkce pro zavěšení sestavy používané ve verzi s velkým znakem této funkce:

```C
int YourReportHook( int reportType, wchar_t *message, int *returnValue );
```

Pro zavěšení sestav s úzkým znakem použijte následující prototyp:

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

Tyto funkce ověřují své parametry. Pokud je *režim* nebo **pfnNewNook** neplatný, vyvolají tyto funkce obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí-1.

> [!NOTE]
> Pokud je vaše aplikace kompilována s možností **/CLR** a funkce vytváření sestav je volána poté, co aplikace ukončila hlavní, modul CLR vyvolá výjimku, pokud funkce vytváření sestav volá jakékoli funkce CRT.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_CrtSetReportHook2**|\<crtdbg.h>|\<errno.h>|
|**_CrtSetReportHookW2**|\<crtdbg.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Příklad

```C
// crt_setreporthook2.c
#include <windows.h>
#include <stdio.h>
#include <crtdbg.h>
#include <assert.h>

int __cdecl TestHook1(int nReportType, char* szMsg, int* pnRet)
{
   int nRet = FALSE;

   printf("CRT report hook 1.\n");
   printf("CRT report type is \"");
   switch (nReportType)
   {
      case _CRT_ASSERT:
      {
         printf("_CRT_ASSERT");
         // nRet = TRUE;   // Always stop for this type of report
         break;
      }

      case _CRT_WARN:
      {
         printf("_CRT_WARN");
         break;
      }

      case _CRT_ERROR:
      {
         printf("_CRT_ERROR");
         break;
      }

      default:
      {
         printf("???Unknown???");
         break;
      }
   }

   printf("\".\nCRT report message is:\n\t");
   printf(szMsg);

   if   (pnRet)
      *pnRet = 0;

   return   nRet;
}

int __cdecl   TestHook2(int nReportType, char* szMsg, int* pnRet)
{
   int   nRet = FALSE;

   printf("CRT report hook 2.\n");
   printf("CRT report type is \"");
   switch   (nReportType)
   {
      case _CRT_WARN:
      {
         printf("_CRT_WARN");
         break;
      }

      case _CRT_ERROR:
      {
         printf("_CRT_ERROR");
         break;
      }

      case _CRT_ASSERT:
      {
         printf("_CRT_ASSERT");
         nRet = TRUE;   // Always stop for this type of report
         break;
      }

      default:
      {
         printf("???Unknown???");
         break;
      }
   }

   printf("\".\nCRT report message is: \t");
   printf(szMsg);

   if   (pnRet)
      *pnRet = 0;
   // printf("CRT report code is %d.\n", *pnRet);
   return   nRet;
}

int   main(int argc, char* argv[])
{
   int   nRet = 0;

   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1)"
          " returned %d\n", nRet);

   _ASSERT(0);

   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"
          " returned %d\n", nRet);
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1);
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1)"
          " returned %d\n", nRet);

   return   nRet;
}
```

### <a name="output"></a>Výstup

```Output
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1) returned 0
```

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
