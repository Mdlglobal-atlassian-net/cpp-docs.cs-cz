---
title: "_strinc –, _wcsinc –, _mbsinc _mbsinc_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsinc
- _wcsinc
- _mbsinc_l
- _strinc
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
- mbsinc_l
- _strinc
- strinc
- _mbsinc
- _wcsinc
- wcsinc
- mbsinc
- _mbsinc_l
dev_langs: C++
helpviewer_keywords:
- _mbsinc function
- wcsinc function
- mbsinc_l function
- _strinc function
- strinc function
- _mbsinc_l function
- mbsinc function
- _wcsinc function
- _tcsinc function
- tcsinc function
ms.assetid: 54685943-8e2c-45e9-a559-2d94930dc6b4
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4fcda1d1c288e6fe8d6a3dfafea287e79ab6738f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="strinc-wcsinc-mbsinc-mbsincl"></a>_strinc, _wcsinc, _mbsinc, _mbsinc_l
Posune ukazatel řetězec o jeden znak.  
  
> [!IMPORTANT]
>  `_mbsinc`a `_mbsinc_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_strinc(  
   const char *current,  
   _locale_t locale  
);  
wchar_t *_wcsinc(  
   const wchar_t *current,  
   _locale_t locale  
);  
unsigned char *_mbsinc(  
   const unsigned char *current   
);  
unsigned char *_mbsinc_l(  
   const unsigned char *current,  
   _locale_t locale  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `current`  
 Znak ukazatel.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Všechny tyto rutiny vrátí ukazatel na znak, který následuje `current`.  
  
## <a name="remarks"></a>Poznámky  
 `_mbsinc` Funkce vrací ukazatel na první bajt vícebajtových znaků, který následuje `current`. `_mbsinc`rozpozná vícebajtových znaků pořadí podle [vícebajtové znakové stránky](../../c-runtime-library/code-pages.md) který je aktuálně používán; `_mbsinc_l` se shoduje s tím rozdílem, že místo toho používá parametr národního prostředí, který se předává v. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Funkce obecného textu `_tcsinc`, definované v souboru Tchar.h, mapuje `_mbsinc` Pokud `_MBCS` byla definována, nebo `_wcsinc` Pokud `_UNICODE` byla definována. V opačném `_tcsinc` mapuje `_strinc`. `_strinc`a `_wcsinc` jsou jedním znaková a široká charakterová verze `_mbsinc`. `_strinc`a `_wcsinc` jsou k dispozici pouze pro toto mapování a v opačném případě by se neměla používat. Další informace najdete v tématu [použití mapování obecného textu](../../c-runtime-library/using-generic-text-mappings.md) a [mapování obecného textu](../../c-runtime-library/generic-text-mappings.md).  
  
 Pokud `current` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu `EINVAL` a nastaví `errno` k `EINVAL`.  
  
> [!IMPORTANT]
>  Tato funkce může být zranitelný vůči hrozbám přetečení vyrovnávací paměti. Přetečení vyrovnávací paměti můžete použít pro útoky systému, protože může dojít k tomu bude vyplacena neoprávněně zvýšení úrovně oprávnění. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_mbsinc`|\<Mbstring.h >|  
|`_mbsinc_l`|\<Mbstring.h >|  
|`_strinc`|\<Tchar.h >|  
|`_wcsinc`|\<Tchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [_strdec –, _wcsdec –, _mbsdec, _mbsdec_l –](../../c-runtime-library/reference/strdec-wcsdec-mbsdec-mbsdec-l.md)   
 [_strnextc –, _wcsnextc –, _mbsnextc –, _mbsnextc_l –](../../c-runtime-library/reference/strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)   
 [_strninc, _wcsninc, _mbsninc, _mbsninc_l](../../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)