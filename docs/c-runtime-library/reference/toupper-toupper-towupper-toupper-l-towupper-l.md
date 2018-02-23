---
title: "ToUpper, _toupper –, towupper –, _toupper_l –, _towupper_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- towupper
- _toupper
- _totupper
- toupper
dev_langs:
- C++
helpviewer_keywords:
- _toupper function
- towupper function
- uppercase, converting strings to
- totupper function
- string conversion, to different characters
- towupper_l function
- toupper_l function
- string conversion, case
- _toupper_l function
- _towupper_l function
- _totupper function
- case, converting
- characters, converting
- toupper function
ms.assetid: cdef1b0f-b19c-4d11-b7d2-cf6334c9b6cc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2da016750a125c6645a878b3fee04a09c3e76e26
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="toupper-toupper-towupper-toupperl-towupperl"></a>toupper, _toupper, towupper, _toupper_l, _towupper_l
Znak převeden na velká písmena.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int toupper(  
   int c   
);  
int _toupper(  
   int c   
);  
int towupper(  
   wint_t c   
);  
int _toupper_l(  
   int c ,  
   _locale_t locale  
);  
int _towupper_l(  
   wint_t c ,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak, který má převést.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každý z těchto rutin převádí kopii `c`, pokud je to možné a vrátí výsledek.  
  
 Pokud `c` je široké znak, pro kterou `iswlower` nenulový a neexistuje odpovídající široké znak, pro který `iswupper` nenulový, `towupper` vrátí odpovídající celý znak; v opačném `towupper` vrátí `c`beze změny.  
  
 Je rezervovaný pro označení chybu žádnou návratovou hodnotu.  
  
 Aby `toupper` umožnit očekávané výsledky, [__isascii –](../../c-runtime-library/reference/isascii-isascii-iswascii.md) a [islower –](../../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md) musí i vrátit nenulové hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Každý z těchto rutin převede danou malé písmeno velké písmeno Pokud je to možné a vhodné. Case převodu `towupper` je specifický pro národní prostředí. V případě došlo ke změně pouze znaky, které se týkají aktuální národní prostředí. Funkce bez `_l` používat příponu aktuálně nastavené národní prostředí. Verze tyto funkce s `_l` příponu trvat národní prostředí jako parametr a použijte místo aktuálně nastavené národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Aby `toupper` umožnit očekávané výsledky, [__isascii –](../../c-runtime-library/reference/isascii-isascii-iswascii.md) a [isupper –](../../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md) musí i vrátit nenulové hodnoty.  
  
 [Rutiny převodu dat](../../c-runtime-library/data-conversion.md)  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_totupper`|`toupper`|`_mbctoupper`|`towupper`|  
|`_totupper_l`|`_toupper_l`|`_mbctoupper_l`|`_towupper_l`|  
  
> [!NOTE]
>  `_toupper_l` a `_towupper_l` mít žádná závislost na národním prostředí a nejsou určeny k přímému volání. Jsou k dispozici pro interní použití rozhraním `_totupper_l`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`toupper`|\<ctype.h>|  
|`_toupper`|\<ctype.h>|  
|`towupper`|\<ctype.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad v [na funkce](../../c-runtime-library/to-functions.md).  
  
## <a name="see-also"></a>Viz také  
 [je, isw – rutiny](../../c-runtime-library/is-isw-routines.md)   
 [to – funkce](../../c-runtime-library/to-functions.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)