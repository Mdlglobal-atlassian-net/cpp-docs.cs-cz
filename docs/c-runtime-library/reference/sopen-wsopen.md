---
title: "_sopen –, _wsopen – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _sopen
- _wsopen
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wsopen
- wsopen
- _sopen
- _tsopen
dev_langs: C++
helpviewer_keywords:
- sopen function
- sharing files
- opening files, for sharing
- _sopen function
- wsopen function
- files [C++], opening
- files [C++], sharing
- _wsopen function
ms.assetid: a9d4cccf-06e9-414d-96fa-453fca88cc1f
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bce1d0aac8b6b4d835b956a9ac05eece4e2e6428
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="sopen-wsopen"></a>_sopen, _wsopen
Otevře soubor pro sdílení. Bezpečnější verze tyto funkce jsou k dispozici, najdete v části [_sopen_s –, _wsopen_s –](../../c-runtime-library/reference/sopen-s-wsopen-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _sopen(  
   const char *filename,  
   int oflag,  
   int shflag [,  
   int pmode ]   
);  
int _wsopen(  
   const wchar_t *filename,  
   int oflag,  
   int shflag [,  
   int pmode ]   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Název souboru.  
  
 `oflag`  
 Druh operace povoleny.  
  
 `shflag`  
 Druh sdílení povoleno.  
  
 `pmode`  
 Nastavení oprávnění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí, vrátí se popisovač souboru pro otevřený soubor.  
  
 Pokud `filename` nebo `oflag` je `NULL` ukazatele, nebo pokud `oflag` nebo `shflag` není v platném rozsahu hodnot, není volána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte `errno` na jednu z následujících hodnot.  
  
 `EACCES`  
 Zadaná cesta je adresář, nebo soubor je jen pro čtení, ale došlo k pokusu o operaci otevřít pro zápis.  
  
 `EEXIST`  
 `_O_CREAT`a `_O_EXCL` příznaky byly zadány, ale `filename` již existuje.  
  
 `EINVAL`  
 Neplatný `oflag` nebo `shflag` argument.  
  
 `EMFILE`  
 Nejsou k dispozici žádné další popisovače souborů.  
  
 `ENOENT`  
 Soubor nebo cesta nebyla nalezena.  
  
 Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_sopen` Funkce otevře soubor určený touto `filename` a připraví soubor sdílený čtení nebo zápisu, podle definice `oflag` a `shflag`. `_wsopen`široká charakterová verze `_sopen`; `filename` argument `_wsopen` je široká charakterová řetězec. `_wsopen`a `_sopen` chovat jinak shodně.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tsopen`|`_sopen`|`_sopen`|`_wsopen`|  
  
 Celočíselný výraz `oflag` se vytvoří kombinací nejméně jeden z následujících manifestu konstanty, které jsou definovány v \<fcntl.h >. Pokud dva nebo více konstant formuláři argument `oflag`, jsou kombinované pomocí operátoru bitové operace OR ( `|` ).  
  
 `_O_APPEND`  
 Přemístí ukazatel souboru na konec souboru před každou operaci zápisu.  
  
 `_O_BINARY`  
 Otevře soubor v binárním režimu (nepřeložený). (Viz [fopen –](../../c-runtime-library/reference/fopen-wfopen.md) popis binárního režimu.)  
  
 `_O_CREAT`  
 Soubor se vytvoří a otevře ji pro zápis. Nemá vliv, pokud soubor určeného `filename` existuje. `pmode` Argument je požadován při `_O_CREAT` je zadán.  
  
 `_O_CREAT | _O_SHORT_LIVED`  
 Vytvoří soubor jako dočasné a pokud je to možné není vyprázdnit na disk. `pmode` Argument je požadován při `_O_CREAT` je zadán.  
  
 `_O_CREAT | _O_TEMPORARY`  
 Vytvoří soubor jako dočasné; soubor je odstraněn při zavření posledního popisovače souborů. `pmode` Argument je požadován při `_O_CREAT` je zadán.  
  
 `_O_CREAT | _O_EXCL`  
 Vrací hodnotu chyby, pokud soubor určený touto `filename` existuje. Platí pouze při použití s `_O_CREAT`.  
  
 `_O_NOINHERIT`  
 Brání vytváření sdílený soubor popisovače.  
  
 `_O_RANDOM`  
 Určuje především náhodný přístup z disku.  
  
 `_O_RDONLY`  
 Otevře se soubor jen pro čtení. Nelze zadat u `_O_RDWR` nebo `_O_WRONLY`.  
  
 `_O_RDWR`  
 Otevře soubor pro čtení i zápis. Nelze zadat u `_O_RDONLY` nebo `_O_WRONLY`.  
  
 `_O_SEQUENTIAL`  
 Určuje především sekvenční přístup z disku.  
  
 `_O_TEXT`  
 Otevře soubor v režimu textových (přeložit). (Další informace najdete v tématu [Text a vstupně-výstupní soubor binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [fopen –](../../c-runtime-library/reference/fopen-wfopen.md).)  
  
 `_O_TRUNC`  
 Otevře soubor a zkrátí ho nule length; soubor musí mít oprávnění k zápisu. Nelze zadat u `_O_RDONLY`. `_O_TRUNC`použít s `_O_CREAT` otevře existující soubor nebo soubor se vytvoří.  
  
> [!NOTE]
>  `_O_TRUNC` Příznak zničí obsah zadaného souboru.  
  
 `_O_WRONLY`  
 Otevře soubor pro zápis pouze. Nelze zadat u `_O_RDONLY` nebo `_O_RDWR`.  
  
 `_O_U16TEXT`  
 Otevře soubor v režimu Unicode UTF-16.  
  
 `_O_U8TEXT`  
 Otevře soubor v režimu Unicode UTF-8.  
  
 `_O_WTEXT`  
 Otevře soubor v režimu Unicode.  
  
 Pokud chcete nastavit režim souboru přístup, je nutné zadat buď `_O_RDONLY`, `_O_RDWR`, nebo `_O_WRONLY`. Neexistuje žádná výchozí hodnota pro režim přístupu.  
  
 Při otevření souboru v režimu Unicode pomocí `_O_WTEXT`, `_O_U8TEXT`, nebo `_O_U16TEXT`, vstupní funkce převede data, která je pro čtení ze souboru do UTF-16 data uložená jako typ `wchar_t`. Funkce, které zapisovat do souboru otevřeného v režimu Unicode očekávat vyrovnávací paměti, které obsahují data ve formátu UTF-16 uložené jako typ `wchar_t`. Pokud soubor zakódován pomocí kódování UTF-8, je při je zapsán a kódování UTF-8 obsah souboru je přeložit na UTF-16, když je pro čtení dat ve formátu UTF-16 přeložit na UTF-8. Pokus o čtení nebo zápisu lichý počet bajtů v režimu Unicode způsobí, že chyba ověření parametru. Číst nebo zapisovat data, která je uložená v programu jako UTF-8, použijte místo režim Unicode režim textových nebo binárních souborů. Jste zodpovědní za jakékoli požadované kódování překlad.  
  
 Pokud `_sopen` je volán s `_O_WRONLY | _O_APPEND` (režim připojení) a `_O_WTEXT`, `_O_U16TEXT`, nebo `_O_U8TEXT`, nejprve se pokusí otevřít soubor pro čtení a zápis, přečtěte si Kusovníku a pak ho znovu otevřít pro zápis pouze. Pokud otevírání souboru pro čtení a zápis selže, otevře soubor pro zápis pouze a používá výchozí hodnota pro nastavení režimu kódování Unicode.  
  
 Argument `shflag` je konstantní výraz, který se skládá z jednoho z následujících manifestu konstant, které jsou definovány v \<share.h >.  
  
 `_SH_DENYRW`  
 Odmítne oprávnění ke čtení a zápisu do souboru.  
  
 `_SH_DENYWR`  
 Odepře přístup pro zápis do souboru.  
  
 `_SH_DENYRD`  
 Odepře přístup pro čtení do souboru.  
  
 `_SH_DENYNO`  
 Povolí přístup čtení a zápisu.  
  
 `pmode` Se vyžaduje jenom v případě `_O_CREAT` je zadán. Pokud soubor neexistuje, `pmode` určuje nastavení v souboru oprávnění, která jsou nastavena při prvním zavření nový soubor. V opačném `pmode` je ignorována. `pmode`je použit celočíselný výraz, který obsahuje jedno nebo obě manifestu konstanty `_S_IWRITE` a `_S_IREAD`, která jsou definována v \<sys\stat.h >. Pokud jsou zadány oba konstanty, jsou kombinovat s operátoru bitové operace OR. Význam `pmode` je následující.  
  
 `_S_IWRITE`  
 Zápis povolen.  
  
 `_S_IREAD`  
 Čtení povolené.  
  
 `_S_IREAD | _S_IWRITE`  
 Čtení a zápis povolen.  
  
 Není-li oprávnění k zápisu, soubor je jen pro čtení. V operačním systému Windows jsou všechny soubory čitelný; není možné udělit oprávnění jen pro zápis. Proto režimů `_S_IWRITE` a `_S_IREAD | _S_IWRITE` odpovídají.  
  
 `_sopen`použije aktuální maska souboru oprávnění k `pmode` předtím, než jsou oprávnění nastavena. (Viz [_umask –](../../c-runtime-library/reference/umask.md).)  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_sopen`|\<IO.h >|\<fcntl.h >, \<sys\types.h >, \<sys\stat.h >, \<share.h >|  
|`_wsopen`|\<IO.h > nebo \<wchar.h >|\<fcntl.h >, \<sys\types.h >, \<sys\stat.h >, \<share.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [_locking –](../../c-runtime-library/reference/locking.md).  
  
## <a name="see-also"></a>Viz také  
 [I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)   
 [_close –](../../c-runtime-library/reference/close.md)   
 [_creat –, _wcreat –](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen –, _wfopen –](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_fsopen –, _wfsopen –](../../c-runtime-library/reference/fsopen-wfsopen.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)