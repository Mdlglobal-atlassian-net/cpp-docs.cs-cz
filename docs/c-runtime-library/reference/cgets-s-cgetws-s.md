---
title: "_cgets_s –, _cgetws_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _cgetws_s
- _cgets_s
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cgets_s
- cgets_s
- cgetws_s
- _cgetws_s
dev_langs: C++
helpviewer_keywords:
- strings [C++], getting from console
- console, getting strings from
- _cgets_s function
- cget_s function
- _cgetws_s function
- cgetws_s function
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
caps.latest.revision: "31"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b2763bdf1c3efd4571b6bfbe68b26ef46c941aed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cgetss-cgetwss"></a>_cgets_s, _cgetws_s
Získá řetězec znaků z konzoly. Tyto verze nástroje [_cgets – a _cgetws –](../../c-runtime-library/cgets-cgetws.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _cgets_s(   
   char *buffer,  
   size_t numberOfElements,  
   size_t *pSizeRead  
);  
errno_t _cgetws_s(  
   wchar_t *buffer  
   size_t numberOfElements,  
   size_t *pSizeRead  
);  
template <size_t size>  
errno_t _cgets_s(   
   char (&buffer)[size],  
   size_t *pSizeRead  
); // C++ only  
template <size_t size>  
errno_t _cgetws_s(  
   wchar_t (&buffer)[size],  
   size_t *pSizeRead  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`buffer`  
 Umístění úložiště pro data.  
  
 [v]`numberOfElements`  
 Velikost vyrovnávací paměti v jednobajtové nebo široké znaky, což je také maximální počet znaků ke čtení.  
  
 [v]`pSizeRead`  
 Počet znaků, ve skutečnosti přečíst.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je nula v případě úspěšného; k chybě, jinak hodnota kódu, pokud dojde k chybě.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`buffer`|`numberOfElements`|`pSizeRead`|Vrátí|Obsah`buffer`|  
|--------------|------------------------|-----------------|------------|--------------------------|  
|`NULL`|všechny|všechny|`EINVAL`|není k dispozici|  
|není`NULL`|nula|všechny|`EINVAL`|nedojde ke změně|  
|není`NULL`|všechny|`NULL`|`EINVAL`|řetězec nulové délky|  
  
## <a name="remarks"></a>Poznámky  
 `_cgets_s`a `_cgetws_s` Přečtěte řetězec z konzoly a zkopírujte řetězec (s hodnotou null ukončovací znak) do `buffer`. `_cgetws_s`široká znaková verze funkce; než velikost znak je stejný jako chování tyto dvě funkce. Maximální velikost řetězce čtení, je předaná jako `numberOfElements` parametr. Tato velikost by měla obsahovat jeden znak pro ukončující hodnotu null. Skutečný počet znaků pro čtení je umístěn v `pSizeRead`.  
  
 Pokud dojde k chybě během operace nebo při ověřování parametry, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a `EINVAL` je vrácen.  
  
 V jazyce C++ použití tyto funkce se zjednodušilo díky šabloně přetížení; přetížení lze odvodit automaticky, a tím, takže není nutné zadat argument velikost délka vyrovnávací paměti a starší, méně bezpečné funkce můžou automaticky nahradit se svými protějšky novější, bezpečnější. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_cgetts_s`|`_cgets_s`|`_cgets_s`|`_cgetws_s`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_cgets_s`|\<conio.h >|  
|`_cgetws_s`|\<conio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [I/O konzoly a portu](../../c-runtime-library/console-and-port-i-o.md)   
 [_getch –, _getwch –](../../c-runtime-library/reference/getch-getwch.md)