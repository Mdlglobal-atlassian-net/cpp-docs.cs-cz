---
title: "mbstowcs_s –, _mbstowcs_s_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbstowcs_s_l
- mbstowcs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
dev_langs: C++
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
caps.latest.revision: "31"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4501b310f71921c9e79910f0585d85eb647f3e4f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mbstowcss-mbstowcssl"></a>mbstowcs_s, _mbstowcs_s_l
Převede posloupnost více-bajtové znaky na odpovídající posloupnost široké znaky. Verze [mbstowcs –, _mbstowcs_l –](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t mbstowcs_s(  
   size_t *pReturnValue,  
   wchar_t *wcstr,  
   size_t sizeInWords,  
   const char *mbstr,  
   size_t count   
);  
errno_t _mbstowcs_s_l(  
   size_t *pReturnValue,  
   wchar_t *wcstr,  
   size_t sizeInWords,  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t mbstowcs_s(  
   size_t *pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbstowcs_s_l(  
   size_t *pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`pReturnValue`  
 Počet znaků převést.  
  
 [out]`wcstr`  
 Adresa vyrovnávací paměti pro výsledný řetězec převedený široká znaková.  
  
 [v]`sizeInWords`  
 Velikost `wcstr` vyrovnávací paměti v slova.  
  
 [v]`mbstr`  
 Adresu pořadí Null byla ukončena více-bajtové znaky.  
  
 [v]`count`  
 Maximální počet široké znaky a uložit v `wcstr` vyrovnávací paměti není včetně ukončující null, nebo [_truncate –](../../c-runtime-library/truncate.md).  
  
 [v]`locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu, kód chyby při selhání.  
  
|Chybový stav|Vrátí hodnotu a`errno`|  
|---------------------|------------------------------|  
|`wcstr`je `NULL` a `sizeInWords` > 0|`EINVAL`|  
|`mbstr`je`NULL`|`EINVAL`|  
|Cílová vyrovnávací paměť je příliš malá tak, aby obsahovala převedený řetězec (Pokud `count` je `_TRUNCATE`; viz poznámky níže)|`ERANGE`|  
|`wcstr`není `NULL` a `sizeInWords` == 0|`EINVAL`|  
  
 Pokud dojde k některé z těchto podmínek, jak je popsáno v je vyvolána výjimka neplatný parametr [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno provádění pokračovat, funkce vrátí kód chyby a nastaví `errno` , které je uvedené v tabulce.  
  
## <a name="remarks"></a>Poznámky  
 `mbstowcs_s` Funkce převede řetězec vícebajtové znaky, na kterou odkazuje `mbstr` do široké znaky, které jsou uložené ve vyrovnávací paměti, na kterou odkazuje `wcstr`. Převod bude pokračovat pro jednotlivé znaky, dokud je splněna jedna z těchto podmínek:  
  
-   Vyskytl se vícebajtových znaků hodnotu null  
  
-   Je zjištěna neplatná vícebajtových znaků  
  
-   Počet široké znaky, které jsou uložené v `wcstr` vyrovnávací paměti je rovno `count`.  
  
 Cílový řetězec je vždy ukončený hodnotou null (i v případě chyby).  
  
 Pokud `count` je speciální hodnota [_truncate –](../../c-runtime-library/truncate.md), pak `mbstowcs_s` převede co nejvíc řetězec jako bude začlenit do cílové vyrovnávací paměti, a přesto nechat místo pro zakončením hodnotu null.  
  
 Pokud `mbstowcs_s` úspěšně převede zdrojový řetězec, uloží je velikost v široké znaky převedený řetězec, včetně null ukončení do `*pReturnValue` (zadat `pReturnValue` není `NULL`). K tomu dojde i v případě `wcstr` argument je `NULL` a poskytuje způsob, jak určit velikost požadované vyrovnávací paměti. Všimněte si, že pokud `wcstr` je `NULL`, `count` je ignorován a `sizeInWords` musí být 0.  
  
 Pokud `mbstowcs_s` zaznamená neplatný vícebajtových znaků, uloží je 0 `*pReturnValue`, nastaví cílové vyrovnávací paměti na prázdný řetězec, nastaví `errno` k `EILSEQ`a vrátí `EILSEQ`.  
  
 Pokud daná pořadí na kterou odkazuje `mbstr` a `wcstr` překrývají, chování `mbstowcs_s` není definován.  
  
> [!IMPORTANT]
>  Ujistěte se, že `wcstr` a `mbstr` se nepřekrývají a že `count` správně odpovídá počtu více-bajtové znaky převést.  
  
 `mbstowcs_s`používá aktuální národní prostředí pro chování všech závislých na národním prostředí; `_mbstowcs_s_l` se shoduje s tím rozdílem, že používá národní prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`mbstowcs_s`|\<stdlib.h >|  
|`_mbstowcs_s_l`|\<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen – mblen –, _mblen_l –](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbtowc –, _mbtowc_l –](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs –, _wcstombs_l –](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb –, _wctomb_l –](../../c-runtime-library/reference/wctomb-wctomb-l.md)