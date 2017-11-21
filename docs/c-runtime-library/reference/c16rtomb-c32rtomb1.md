---
title: c16rtomb c32rtomb1 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- c16rtomb
- c32rtomb
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
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
dev_langs: C++
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e9e917719c0b980f3ba46e11456e4a47b2a518ce
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb c32rtomb
Převeďte UTF-16 nebo UTF-32 široká znaková vícebajtových znaků v aktuální národní prostředí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t c16rtomb(  
    char *mbchar,   
    char16_t wchar,  
    mbstate_t *state  
);  
size_t c32rtomb(  
    char *mbchar,   
    char32_t wchar,  
    mbstate_t *state  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`mbchar`  
 Ukazatel na pole k uložení vícebajtových znaků převeden.  
  
 [v]`wchar`  
 Široká znaková převést.  
  
 [ve out]`state`  
 Ukazatel na `mbstate_t` objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet bajtů, které jsou uložené v objektu pole `mbchar`, včetně jakýchkoli pořadí shift. Pokud `wchar` není platný znak široké, hodnota (`size_t`)(-1) se vrátí, `errno` je nastaven na `EILSEQ`a hodnota `state` není zadáno.  
  
## <a name="remarks"></a>Poznámky  
 `c16rtomb` Slouží k převodu znakové sady UTF-16 znaků `wchar` ekvivalentní vícebajtových znaků úzké pořadí v aktuální národní prostředí. Pokud `mbchar` není ukazatele null, funkce úložiště převedený pořadí v poli objektu, na kterou odkazuje `mbchar`. Až `MB_CUR_MAX` bajtů, které jsou uložené v `mbchar`, a `state` nastavena na výsledný stav vícebajtové shift.    Pokud `wchar` je null široká znaková potřeba posloupnost obnovení je uložený stav počáteční shift, v případě potřeby následuje znak hodnoty null a `state` je nastavena do stavu počáteční převod. `c32rtomb` Je stejný jako funkce, ale převádí znak znakové sady UTF-32.  
  
 Pokud `mbchar` je ukazatel s hodnotou null, chování je ekvivalentní volání funkce, která nahradí vnitřní vyrovnávací paměť pro `mbchar` a široké znak hodnoty null pro `wchar`.  
  
 `state` Objekt převod stavu lze provést následující volání této funkce a dalších funkcí s možností restartování, které Udržovat stav shift výstup vícebajtové znaky. Výsledky nejsou definovány, když kombinovat používání funkcí s možností restartování a bez nabízet možnost restartování, nebo pokud volání `setlocale` se mezi volání funkcí s možností restartování.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`c16rtomb`, `c32rtomb`|C, C++: \<uchar.h >|  
  
 Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtoc16 mbrtoc32](../../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)   
 [wcrtomb –](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb_s –](../../c-runtime-library/reference/wcrtomb-s.md)