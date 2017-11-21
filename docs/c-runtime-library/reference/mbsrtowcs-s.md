---
title: "mbsrtowcs_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: mbsrtowcs_s
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
f1_keywords: mbsrtowcs_s
dev_langs: C++
helpviewer_keywords: mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 72489315ad23bf65086105c5d76da1edea48674d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mbsrtowcss"></a>mbsrtowcs_s
Převod řetězce vícebajtových znaků v aktuální národní prostředí na jeho široká znaková řetězcová reprezentace. Verzi [mbsrtowcs –](../../c-runtime-library/reference/mbsrtowcs.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t mbsrtowcs_s(  
   size_t * pReturnValue,  
   wchar_t * wcstr,  
   size_t sizeInWords,  
   const char ** mbstr,  
   size_t count,  
   mbstate_t * mbstate  
);  
template <size_t size>  
errno_t mbsrtowcs_s(  
   size_t * pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char ** mbstr,  
   size_t count,  
   mbstate_t * mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`pReturnValue`  
 Počet znaků převést.  
  
 [out]`wcstr`  
 Adresa vyrovnávací paměti k uložení výsledná převést řetězec široké znaků.  
  
 [out]`sizeInWords`  
 Velikost `wcstr` v slova (široké znaky).  
  
 [ve out]`mbstr`  
 Nepřímý odkaz na umístění řetězce vícebajtových znaků, který má být převeden.  
  
 [v]`count`  
 Maximální počet široké znaky a uložit v `wcstr` vyrovnávací paměti není včetně ukončující null, nebo [_truncate –](../../c-runtime-library/truncate.md).  
  
 [ve out]`mbstate`  
 Ukazatel na `mbstate_t` převodu stavu objektu. Pokud tato hodnota je ukazatel s hodnotou null, použije se objekt statické vnitřní převod stavu. Protože interní `mbstate_t` objekt není bezpečné pro přístup z více vláken, doporučujeme, aby vždy předáte vlastní `mbstate` parametr.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud převod úspěšný 0 pro nulu nebo kód chyby při selhání.  
  
|Chybový stav|Vrátí hodnotu a`errno`|  
|---------------------|------------------------------|  
|`wcstr`je ukazatel s hodnotou null a `sizeInWords` > 0|`EINVAL`|  
|`mbstr`je ukazatel s hodnotou null|`EINVAL`|  
|Řetězec nepřímo na kterou odkazuje `mbstr` obsahuje posloupnost vícebajtové, který není platný pro aktuální národní prostředí.|`EILSEQ`|  
|Cílová vyrovnávací paměť je příliš malá tak, aby obsahovala převedený řetězec (Pokud `count` je `_TRUNCATE`; Další informace najdete v tématu poznámky)|`ERANGE`|  
  
 Pokud dojde k některé z těchto podmínek, jak je popsáno v vyvolání výjimky neplatný parametr [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno provádění pokračovat, funkce vrátí kód chyby a nastaví `errno` , které je uvedené v tabulce.  
  
## <a name="remarks"></a>Poznámky  
 `mbsrtowcs_s` Funkce převede řetězec vícebajtové znaky, na kterou nepřímo odkazuje `mbstr` do široké znaky, které jsou uložené ve vyrovnávací paměti, na kterou odkazuje `wcstr`, pomocí stav převodu obsažené v `mbstate`. Převod bude pokračovat pro jednotlivé znaky, dokud je splněna jedna z těchto podmínek:  
  
-   Vyskytl se vícebajtových znaků hodnotu null  
  
-   Je zjištěna neplatná vícebajtových znaků  
  
-   Počet široké znaky, které jsou uložené v `wcstr` vyrovnávací paměti je rovno `count`.  
  
 Cílový řetězec `wcstr` je vždy ukončené hodnotou null i v případě chybu, pokud `wcstr` je ukazatel s hodnotou null.  
  
 Pokud `count` je speciální hodnota [_truncate –](../../c-runtime-library/truncate.md), `mbsrtowcs_s` převede co nejvíc řetězec jako bude začlenit do cílové vyrovnávací paměti, a přesto nechat místo pro zakončením hodnotu null.  
  
 Pokud `mbsrtowcs_s` úspěšně převede zdrojový řetězec, uloží je velikost v široké znaky převedený řetězec a null ukončení do `*pReturnValue`, zadaný `pReturnValue` není nulový ukazatel. K tomu dojde i v případě `wcstr` argument je ukazatel s hodnotou null a vám umožní určit velikost požadované vyrovnávací paměti. Všimněte si, že pokud `wcstr` je ukazatel s hodnotou null, `count` je ignorována.  
  
 Pokud `wcstr` ukazatel s hodnotou null, není objekt ukazatel na kterou odkazuje `mbstr` je přiřazen ukazatele null, pokud převod zastavena, protože bylo dosaženo ukončující znak hodnoty null. Pokud existuje, jinak hodnota je přiřazen pouze posledních adresu převést poslední vícebajtových znaků. To umožňuje volání funkce následné restartování převodu, kde byla zastavena toto volání.  
  
 Pokud `mbstate` je ukazatel s hodnotou null, interní knihovna `mbstate_t` převodu stavu statické objekt se používá. Protože tato interní statické objekt není bezpečné pro přístup z více vláken, doporučujeme, předáte vlastní `mbstate` hodnotu.  
  
 Pokud `mbsrtowcs_s` zaznamená vícebajtových znaků, který není platný pro aktuální prostředí, odešle -1 do `*pReturnValue`, nastaví cílové vyrovnávací paměti `wcstr` na prázdný řetězec, nastaví `errno` k `EILSEQ`a vrátí `EILSEQ`.  
  
 Pokud daná pořadí na kterou odkazuje `mbstr` a `wcstr` překrývají, chování `mbsrtowcs_s` není definován. `mbsrtowcs_s`je ovlivňován LC_TYPE kategorii aktuální národní prostředí.  
  
> [!IMPORTANT]
>  Ujistěte se, že `wcstr` a `mbstr` se nepřekrývají a že `count` správně odpovídá počtu více-bajtové znaky převést.  
  
 `mbsrtowcs_s` Funkce se liší od [mbstowcs_s –, _mbstowcs_s_l –](../../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md) podle jeho restartability. Stav převodu je uložený ve `mbstate` pro následující volání stejné nebo jiné funkce nabízet možnost restartování. Výsledky nejsou definovány při kombinování použití funkce nonrestartable a nabízet možnost restartování. Například by měla použít aplikace `mbsrlen` místo `mbslen`, pokud následných volání `mbsrtowcs_s` se používá místo`mbstowcs_s.`  
  
 V jazyce C++ pomocí této funkce se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (což eliminuje požadavek na zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit pomocí jejich protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="exceptions"></a>Výjimky  
 `mbsrtowcs_s` Pokud žádná funkce v aktuálním volání vláken je funkce s více vlákny bezpečné `setlocale` tak dlouho, dokud tato funkce je prováděna a `mbstate` argument není nulový ukazatel.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`mbsrtowcs_s`|\<wchar.h >|  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtowc –](../../c-runtime-library/reference/mbrtowc.md)   
 [mbtowc –, _mbtowc_l –](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [mbstowcs_s –, _mbstowcs_s_l –](../../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)   
 [mbsinit –](../../c-runtime-library/reference/mbsinit.md)