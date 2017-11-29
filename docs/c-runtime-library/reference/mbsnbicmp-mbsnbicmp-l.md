---
title: "_mbsnbicmp –, _mbsnbicmp_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbicmp_l
- _mbsnbicmp
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strnicmp
- _wcsnicmp_l
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _tcsnicmp
- _strnicmp_l
- _tcsnicmp_l
- _wcsnicmp
- _mbsnbicmp_l
dev_langs: C++
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6abe7372f42e679264ec501918ad62823ba53ba9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mbsnbicmp-mbsnbicmpl"></a>_mbsnbicmp, _mbsnbicmp_l
Porovná `n` bajtů dvě vícebajtových znaků řetězce a ignoruje velikost písmen.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _mbsnbicmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `string1, string2`  
 Řetězce ukončené hodnotou Null pro porovnání.  
  
 `count`  
 Počet bajtů k porovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota označuje vztah mezi dílčích řetězců.  
  
|Návratová hodnota|Popis|  
|------------------|-----------------|  
|< 0|`string1`substring menší než `string2` dílčí řetězec.|  
|0|`string1`substring identické `string2` dílčí řetězec.|  
|> 0|`string1`substring větší než `string2` dílčí řetězec.|  
  
 Při chybě `_mbsnbcmp` vrátí `_NLSCMPERROR`, která je definována v String.h a Mbstring.h.  
  
## <a name="remarks"></a>Poznámky  
 `_mbsnbicmp` Funkce provádí ordinální porovnávání maximálně prvního `count` bajtů `string1` a `string2`. Porovnání se provádí převod na malá písmena; každý znak `_mbsnbcmp` je malá a velká písmena verze `_mbsnbicmp`. Porovnání končí, když je dosaženo ukončující znak hodnoty null v buď řetězec před `count` jsou porovnávány znaků. Pokud jsou si rovny řetězce při dosažení ukončující znak hodnoty null v buď řetězec před `count` znaky jsou porovnávány, kratší řetězec je menší.  
  
 `_mbsnbicmp`je podobná `_mbsnicmp`kromě toho, že až porovná řetězce `count` bajtů místo znaky.  
  
 Dva řetězce obsahující znaky umístěný mezi 'Z' a 'a' v tabulce ASCII ('[','\\', ']', ' ^', '_', a '\`') porovnat odlišně, v závislosti na jejich případě. Například dva řetězce "`ABCDE`"a"`ABCD^`" porovnat jedním ze způsobů, je-li porovnání malá písmena ("`abcde`" > "`abcd^`") a jiným způsobem ("`ABCDE`" < "`ABCD^`") Pokud je velká písmena.  
  
 `_mbsnbicmp`rozpozná vícebajtových znaků pořadí podle [vícebajtové znakové stránky](../../c-runtime-library/code-pages.md) aktuálně používán. Nemá vliv na aktuální nastavení národního prostředí.  
  
 Pokud má jedna `string1` nebo `string2` je ukazatel s hodnotou null, `_mbsnbicmp` volá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu `_NLSCMPERROR` a nastaví `errno` k `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsnicmp`|`_strnicmp`|`_mbsnbicmp`|`_wcsnicmp`|  
|`_tcsnicmp_l`|`_strnicmp_l`|`_mbsnbicmp_l`|`_wcsnicmp_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_mbsnbicmp`|< mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [_mbsnbcmp –, _mbsnbcmp_l –](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md).  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [_mbsnbcat –, _mbsnbcat_l –](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [_mbsnbcmp –, _mbsnbcmp_l –](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [_stricmp –, _wcsicmp –, _mbsicmp –, _stricmp_l –, _wcsicmp_l –, _mbsicmp_l –](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)