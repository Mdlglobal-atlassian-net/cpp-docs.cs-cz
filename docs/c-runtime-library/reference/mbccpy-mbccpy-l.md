---
title: "_mbccpy –, _mbccpy_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _mbccpy
- _mbccpy_l
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
- _mbccpy
- tccpy
- ftccpy
- mbccpy
- _tccpy
- _ftccpy
dev_langs:
- C++
helpviewer_keywords:
- _tccpy function
- _tccpy_l function
- tccpy_l function
- tccpy function
- mbccpy function
- _mbccpy_l function
- _mbccpy function
- mbccpy_l function
ms.assetid: 13f4de6e-7792-41ac-b319-dd9b135433aa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9ad2ff9b8d9b1369b009898ae9b78c34c3643f85
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="mbccpy-mbccpyl"></a>_mbccpy, _mbccpy_l
Zkopíruje vícebajtových znaků z jednoho řetězce k jiným řetězcem. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_mbccpy_s –, _mbccpy_s_l –](../../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md).  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _mbccpy(  
   unsigned char *dest,  
   const unsigned char *src   
);  
void _mbccpy_l(  
   unsigned char *dest,  
   const unsigned char *src,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dest`  
 Cíl kopírování.  
  
 `src`  
 Vícebajtové znakové ke kopírování.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="remarks"></a>Poznámky  
 `_mbccpy` Funkce zkopíruje jeden vícebajtových znaků z `src` k `dest`.  
  
 Tato funkce ověří jeho parametry. Pokud `_mbccpy` byla předána ukazatel s hodnotou null pro `dest` nebo `src`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL`.  
  
 `_mbccpy` používá aktuální národní prostředí pro chování všech závislých na národním prostředí. `_mbccpy_l` je stejný jako `_mbccpy` s tím rozdílem, že `_mbccpy_l` používá národní prostředí předaná chování všech závislých na národním prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 **Poznámka k zabezpečení** pomocí řetězce ukončené hodnotou null. Řetězce ukončené hodnotou null nesmí překročit velikost cílové vyrovnávací paměti. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795). Přetečení vyrovnávací paměti problémy jsou často metodu systému útoku, výsledkem bude vyplacena neoprávněně zvýšení úrovně oprávnění.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tccpy`|Mapuje makro nebo vložené funkce|`_mbccpy`|Mapuje makro nebo vložené funkce|  
|`_tccpy_l`|není k dispozici|`_mbccpy_l`|není k dispozici|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_mbccpy`|\<mbctype.h>|  
|`_mbccpy_l`|\<mbctype.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen, mblen, _mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)