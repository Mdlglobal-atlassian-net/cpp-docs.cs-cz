---
title: "_mbccpy_s –, _mbccpy_s_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbccpy_s
- _mbccpy_s_l
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
- _mbccpy_s_l
- mbccpy_s_l
- mbccpy_s
- _mbccpy_s
dev_langs: C++
helpviewer_keywords:
- tccpy_s_l function
- _tccpy_s function
- _mbccpy_s function
- mbccpy_s function
- tccpy_s function
- mbccpy_s_l function
- _tccpy_s_l function
- _mbccpy_s_l function
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 942267c2632e6ffafec3d2fa9308bfb3db69aa87
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mbccpys-mbccpysl"></a>_mbccpy_s, _mbccpy_s_l
Zkopíruje jeden vícebajtových znaků z řetězce na jiný řetězec. Tyto verze nástroje [_mbccpy –, _mbccpy_l –](../../c-runtime-library/reference/mbccpy-mbccpy-l.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _mbccpy_s(  
   unsigned char *dest,  
   size_t buffSizeInBytes,  
   int * pCopied,  
   const unsigned char *src   
);  
errno_t _mbccpy_s_l(  
   unsigned char *dest,  
   size_t buffSizeInBytes,  
   int * pCopied,  
   const unsigned char *src,  
   locale_t locale  
);  
template <size_t size>  
errno_t _mbccpy_s(  
   unsigned char (&dest)[size],  
   int * pCopied,  
   const unsigned char *src   
); // C++ only  
template <size_t size>  
errno_t _mbccpy_s_l(  
   unsigned char (&dest)[size],  
   int * pCopied,  
   const unsigned char *src,  
   locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`dest`  
 Cíl kopírování.  
  
 [v]`buffSizeInBytes`  
 Velikost cílové vyrovnávací paměti.  
  
 [out]`pCopied`  
 Naplní se počet bajtů zkopírovaný (1 nebo 2 v případě úspěšného). Předat `NULL` Pokud vám nezáleží číslo.  
  
 [v]`src`  
 Vícebajtové znakové ke kopírování.  
  
 [v]`locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěšného; Kód chyby při selhání. Pokud `src` nebo `dest` je `NULL`, nebo pokud se více než `buffSizeinBytes` bajtů zkopírován do `dest`, pak je volána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, vrátí funkce `EINVAL` a `errno` je nastaven na `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 `_mbccpy_s` Funkce zkopíruje jeden vícebajtových znaků z `src` k `dest`. Pokud `src` neukazuje na zájemce bajt vícebajtových znaků určeného implicitní volání [_ismbblead –](../../c-runtime-library/reference/ismbblead-ismbblead-l.md), pak jeden bajt, `src` zkopíruje body. Pokud `src` bodů úvodní bajt, ale následující bajtu je 0 a proto neplatný pak 0 se zkopíruje do `dest`, `errno` je nastaven na `EILSEQ`, a vrátí funkce `EILSEQ`.  
  
 `_mbccpy_s`připojení není null ukončovací; ale pokud `src` odkazuje na prázdný znak, pak tuto hodnotu null se zkopíruje do `dest` (Toto je právě regulární jednobajtové kopie).  
  
 Hodnota v `pCopied` , naplní se počet bajtů, které jsou zkopírovány. Možné hodnoty jsou 1 a 2, pokud byla operace úspěšná. Pokud `NULL` je předán, je tento parametr ignorován.  
  
|`src`|zkopírovat do`dest`|`pCopied`|Návratová hodnota|  
|-----------|----------------------|---------------|------------------|  
|úvodní bajt|úvodní bajt|1|0|  
|0|0|1|0|  
|Následuje jiný 0 bajtů realizace|Následuje jiný 0 bajtů realizace|2|0|  
|Následuje 0 bajtů realizace|0|1|`EILSEQ`|  
  
 Všimněte si, druhý řádek je právě ve speciálním případě první. Také Upozorňujeme, že v tabulce předpokládá `buffSizeInBytes`  >=  `pCopied`.  
  
 `_mbccpy_s`používá aktuální národní prostředí pro chování všech závislých na národním prostředí. `_mbccpy_s_l`je stejný jako `_mbccpy_s` s tím rozdílem, že `_mbccpy_s_l` používá národní prostředí předaná chování všech závislých na národním prostředí.  
  
 V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení lze odvodit délka vyrovnávací paměti automaticky, takže není nutné zadat argument velikost. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tccpy_s`|Mapuje makro nebo vložené funkce.|`_mbccpy_s`|Mapuje makro nebo vložené funkce.|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_mbccpy_s`|\<Mbstring.h >|  
|`_mbccpy_s_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen, mblen, _mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)