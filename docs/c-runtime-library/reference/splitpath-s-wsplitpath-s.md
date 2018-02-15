---
title: "_splitpath_s –, _wsplitpath_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wsplitpath_s
- _splitpath_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wsplitpath_s
- splitpath_s
- _splitpath_s
- wsplitpath_s
dev_langs:
- C++
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9baa71ca1a3d624c08df8ff1cbd14a9386e1b83d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="splitpaths-wsplitpaths"></a>_splitpath_s, _wsplitpath_s
Název cesty dělí do součásti. Toto jsou verze [_splitpath –, _wsplitpath –](../../c-runtime-library/reference/splitpath-wsplitpath.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _splitpath_s(  
   const char * path,  
   char * drive,  
   size_t driveNumberOfElements,  
   char * dir,  
   size_t dirNumberOfElements,  
   char * fname,  
   size_t nameNumberOfElements,  
   char * ext,   
   size_t extNumberOfElements  
);  
errno_t _wsplitpath_s(  
   const wchar_t * path,  
   wchar_t * drive,  
   size_t driveNumberOfElements,  
   wchar_t *dir,  
   size_t dirNumberOfElements,  
   wchar_t * fname,  
   size_t nameNumberOfElements,  
   wchar_t * ext,  
   size_t extNumberOfElements  
);  
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>  
errno_t _splitpath_s(  
   const char *path,  
   char (&drive)[drivesize],  
   char (&dir)[dirsize],  
   char (&fname)[fnamesize],  
   char (&ext)[extsize]  
); // C++ only  
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>  
errno_t _wsplitpath_s(  
   const wchar_t *path,  
   wchar_t (&drive)[drivesize],  
   wchar_t (&dir)[dirsize],  
   wchar_t (&fname)[fnamesize],  
   wchar_t (&ext)[extsize]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `path`  
 Úplná cesta.  
  
 [out] `drive`  
 Jednotka písmenem následovaným dvojtečkou (`:`). Abyste mohli předávat `NULL` pro tento parametr, pokud není nutné písmeno jednotky.  
  
 [in] `driveNumberOfElements`  
 Velikost `drive` vyrovnávací paměti v jednobajtové nebo široké znaky. Pokud `drive` je `NULL`, tato hodnota musí být 0.  
  
 [out] `dir`  
 Cesta k adresáři, včetně koncové lomítko. Předávání lomítka ( `/` ), zpětná lomítka ( `\` ), nebo mohou být použity obě. Abyste mohli předávat `NULL` pro tento parametr, pokud není nutné cesta k adresáři.  
  
 [in] `dirNumberOfElements`  
 Velikost `dir` vyrovnávací paměti v jednobajtové nebo široké znaky. Pokud `dir` je `NULL`, tato hodnota musí být 0.  
  
 [out] `fname`  
 Základní název souboru (bez přípony). Abyste mohli předávat `NULL` pro tento parametr, pokud není nutné název souboru.  
  
 [in] `nameNumberOfElements`  
 Velikost `fname` vyrovnávací paměti v jednobajtové nebo široké znaky. Pokud `fname` je `NULL`, tato hodnota musí být 0.  
  
 [out] `ext`  
 Příponu názvu souboru, včetně úvodní období (**.**). Abyste mohli předávat `NULL` pro tento parametr, pokud není nutné příponu názvu souboru.  
  
 [in] `extNumberOfElements`  
 Velikost `ext` vyrovnávací paměti v jednobajtové nebo široké znaky. Pokud `ext` je `NULL`, tato hodnota musí být 0.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěšného; Kód chyby při selhání.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|Podmínka|Návratová hodnota|  
|---------------|------------------|  
|`path` je `NULL`|`EINVAL`|  
|`drive` je `NULL`, `driveNumberOfElements` je nulová|`EINVAL`|  
|`drive` jinou hodnotu než`NULL`, `driveNumberOfElements` je nulová.|`EINVAL`|  
|`dir` je `NULL`, `dirNumberOfElements` je nulová|`EINVAL`|  
|`dir` jinou hodnotu než`NULL`, `dirNumberOfElements` je nulová.|`EINVAL`|  
|`fname` je `NULL`, `nameNumberOfElements` je nulová|`EINVAL`|  
|`fname` jinou hodnotu než`NULL`, `nameNumberOfElements` je nulová.|`EINVAL`|  
|`ext` je `NULL`, `extNumberOfElements` je nulová|`EINVAL`|  
|`ext` jinou hodnotu než`NULL`, `extNumberOfElements` je nulová.|`EINVAL`|  
  
 Pokud dojde k některé z výše uvedených podmínek, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí `EINVAL`.  
  
 Pokud některé z vyrovnávací paměti je příliš krátká pro uložení výsledek, tyto funkce zrušte všechny vyrovnávací paměti do prázdné řetězce, nastavte `errno` k `ERANGE`a vrátí `ERANGE`.  
  
## <a name="remarks"></a>Poznámky  
 `_splitpath_s` Funkce dělí do jeho součástí čtyři cestu. `_splitpath_s` automaticky zpracovává argumenty řetězce vícebajtových znaků podle potřeby, rozpozná sekvencí vícebajtových znaků podle vícebajtové znakové stránky aktuálně používán. `_wsplitpath_s` široká charakterová verze `_splitpath_s`; argumenty, které mají `_wsplitpath_s` jsou široká charakterová řetězce. Tyto funkce chovají stejně jako jinak  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tsplitpath_s`|`_splitpath_s`|`_splitpath_s`|`_wsplitpath_s`|  
  
 Jednotlivé komponenty úplná cesta je uložena v samostatné vyrovnávací paměti; manifestu konstanty `_MAX_DRIVE`, `_MAX_DIR`, `_MAX_FNAME`, a `_MAX_EXT` (definovanou v STDLIB. H) zadejte maximální povolenou velikost pro každou součást souboru. Komponenty soubory větší než odpovídající manifestu konstanty způsobit poškození haldy.  
  
 V následující tabulce jsou uvedeny hodnoty manifestu konstanty.  
  
|Název|Hodnota|  
|----------|-----------|  
|_MAX_DRIVE|3|  
|_MAX_DIR|256|  
|_MAX_FNAME|256|  
|_MAX_EXT|256|  
  
 Pokud úplná cesta neobsahuje součásti (například název souboru), `_splitpath_s` přiřadí prázdný řetězec odpovídající vyrovnávací paměti.  
  
 V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení lze odvodit délka vyrovnávací paměti automaticky, takže není nutné zadat argument velikost. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
 Ladicí verze těchto funkcí nejprve vyplnit vyrovnávací paměť s 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_splitpath_s`|\<stdlib.h>|  
|`_wsplitpath_s`|\<stdlib.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [_makepath_s –, _wmakepath_s –](../../c-runtime-library/reference/makepath-s-wmakepath-s.md).  
  
## <a name="see-also"></a>Viz také  
 [Zpracování souborů](../../c-runtime-library/file-handling.md)   
 [_splitpath, _wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [_fullpath, _wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_makepath, _wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)