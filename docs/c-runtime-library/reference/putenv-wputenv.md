---
title: "_putenv –, _wputenv – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _putenv
- _wputenv
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
dev_langs: C++
helpviewer_keywords:
- _putenv function
- environment variables, deleting
- putenv function
- tputenv function
- environment variables, creating
- wputenv function
- _wputenv function
- _tputenv function
- environment variables, modifying
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5fdb0ee73b6ee289a97e3debfb7b4b5427ba003f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="putenv-wputenv"></a>_putenv, _wputenv
Vytvoří, upraví nebo odstraní proměnné prostředí. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_putenv_s –, _wputenv_s –](../../c-runtime-library/reference/putenv-s-wputenv-s.md).  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _putenv(  
   const char *envstring   
);  
int _wputenv(  
   const wchar_t *envstring   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `envstring`  
 Definice řetězců prostředí.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí 0, pokud bylo úspěšné nebo -1 v případě k chybě.  
  
## <a name="remarks"></a>Poznámky  
 `_putenv` Funkce přidá nové proměnné prostředí nebo upraví hodnoty existujících proměnných prostředí. Proměnné prostředí definují prostředí, ve kterém proces provádí (například výchozí cesta hledání pro knihovny propojení v aplikaci). `_wputenv`široká charakterová verze `_putenv`; `envstring` argument `_wputenv` je široká charakterová řetězec.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tputenv`|`_putenv`|`_putenv`|`_wputenv`|  
  
 `envstring` Argument musí být ukazatel na řetězec ve formátu `varname=string`, kde `varname` je název proměnné prostředí, chcete-li přidat nebo upravit a `string` je hodnota proměnné. Pokud `varname` už je součástí prostředí, jeho hodnota je nahrazena `string`, jinak hodnota nové `varname` proměnnou a její `string` hodnota se přidá do prostředí. Proměnnou z prostředí můžete odebrat tak, že zadáte prázdnou `string` – jinými slovy, tak, že zadáte pouze `varname=`.  
  
 `_putenv`a `_wputenv` ovlivňují jenom prostředí, ve kterém je lokální vzhledem k aktuální proces; se nedá použít k úpravě prostředí příkaz úrovni. To znamená tyto funkce fungují pouze na datové struktury přístupné běhové knihovny a ne na prostředí segmentu pro proces vytvořené operačního systému. Aktuální proces ukončí, stane se prostředí úroveň proces volání (ve většině případů úroveň operačního systému). Ale upravený prostředí se dá předat do jakékoli nové procesů vytvořených službou `_spawn`, `_exec`, nebo `system`, a získat tyto nové procesy žádné nové položky přidal `_putenv` a `_wputenv`.  
  
 Neměňte položku prostředí přímo: místo toho použijte `_putenv` nebo `_wputenv` ho změnit. Na konkrétní prvky uvolnění přímo `_environ[]` globální pole může vést k neplatné paměti adresovaném.  
  
 `getenv`a `_putenv` pomocí globální proměnné `_environ` pro přístup k tabulce prostředí; `_wgetenv` a `_wputenv` použít `_wenviron`. `_putenv`a `_wputenv` může změnit hodnotu `_environ` a `_wenviron`, proto zrušení platnosti `_envp` argument `main` a `_wenvp` argument `wmain`. Proto je bezpečnější používat `_environ` nebo `_wenviron` pro přístup k informacím prostředí. Další informace o vztahu z `_putenv` a `_wputenv` globální proměnné, najdete v tématu [_environ –, _wenviron –](../../c-runtime-library/environ-wenviron.md).  
  
> [!NOTE]
>  `_putenv` a `_getenv` řady funkcí nejsou bezpečné pro přístup z více vláken. `_getenv`může vrátit ukazatel řetězec při `_putenv` upravuje řetězec, způsobuje náhodné chyby. Ujistěte se, že jsou synchronizovány volání na tyto funkce.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_putenv`|\<stdlib.h >|  
|`_wputenv`|\<stdlib.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Příklad, jak pomocí `_putenv`, najdete v části [getenv _wgetenv –](../../c-runtime-library/reference/getenv-wgetenv.md).  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [GETENV –, _wgetenv –](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_searchenv –, _wsearchenv –](../../c-runtime-library/reference/searchenv-wsearchenv.md)