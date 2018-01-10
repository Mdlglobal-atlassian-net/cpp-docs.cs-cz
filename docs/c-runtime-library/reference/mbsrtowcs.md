---
title: "mbsrtowcs – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: mbsrtowcs
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
f1_keywords: mbsrtowcs
dev_langs: C++
helpviewer_keywords: mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6b51f8ccbac43e30202598499613d3b1c7c6e0a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mbsrtowcs"></a>mbsrtowcs
Převede řetězec vícebajtových znaků v aktuální národní prostředí na odpovídající široká znaková řetězec pomocí funkce restartování uprostřed vícebajtových znaků. Bezpečnější verze této funkce je k dispozici. v tématu [mbsrtowcs_s –](../../c-runtime-library/reference/mbsrtowcs-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t mbsrtowcs(  
   wchar_t *wcstr,  
   const char **mbstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t mbsrtowcs(  
   wchar_t (&wcstr)[size],  
   const char **mbstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`wcstr`  
 Adres výsledný řetězec převedený široká znaková uložit.  
  
 [ve out]`mbstr`  
 Nepřímý odkaz na umístění vícebajtový řetězec k převedení.  
  
 [v]`count`  
 Maximální počet znaků (ne v bajtech) můžete převést a uložit do `wcstr`.  
  
 [ve out]`mbstate`  
 Ukazatel na `mbstate_t` převodu stavu objektu. Pokud tato hodnota je ukazatel s hodnotou null, použije se objekt statické vnitřní převod stavu. Protože interní `mbstate_t` objekt není bezpečné pro přístup z více vláken, doporučujeme, aby vždy předáte vlastní `mbstate` parametr.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí počet znaků úspěšně převést, není včetně ukončující znak hodnoty null, pokud existuje. Vrátí (Pokud došlo k chybě a nastaví size_t)(-1) `errno` k eilseq –.  
  
## <a name="remarks"></a>Poznámky  
 `mbsrtowcs` Funkce převede řetězec vícebajtové znaky, na kterou nepřímo odkazuje `mbstr`, do široké znaky, které jsou uložené ve vyrovnávací paměti, na kterou odkazuje `wcstr`, pomocí stav převodu obsažené v `mbstate`. Převod pokračuje pro každý znak až do buď ukončující null vícebajtových znaků bez vícebajtové pořadí, které neodpovídá platný znak v aktuální národní prostředí je zjištěna, nebo dokud `count` byly znaků převést. Pokud `mbsrtowcs` zaznamená vícebajtových znaků null (\0) před nebo po `count` dojde, se převede na 16bitové ukončující znak hodnoty null a zastaví.  
  
 Proto široká znaková řetězce na `wcstr` je ukončené hodnotou null jenom v případě `mbsrtowcs` vícebajtových znaků hodnotu null, zaznamená při převodu. Pokud daná pořadí na kterou odkazuje `mbstr` a `wcstr` překrývají, chování `mbsrtowcs` není definován. `mbsrtowcs`je ovlivňován LC_TYPE kategorii aktuální národní prostředí.  
  
 `mbsrtowcs` Funkce se liší od [mbstowcs –, _mbstowcs_l –](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md) podle jeho restartability. Stav převodu je uložený ve `mbstate` pro následující volání stejné nebo jiné funkce nabízet možnost restartování. Výsledky nejsou definovány při kombinování použití funkce nonrestartable a nabízet možnost restartování.  Například by měla použít aplikace `mbsrlen` místo `mbslen`, pokud následných volání `mbsrtowcs` se používá místo`mbstowcs.`  
  
 Pokud `wcstr` ukazatel s hodnotou null, není objekt ukazatel na kterou odkazuje `mbstr` je přiřazen ukazatele null, pokud převod zastavena, protože bylo dosaženo ukončující znak hodnoty null. Pokud existuje, jinak hodnota je přiřazen pouze posledních adresu převést poslední vícebajtových znaků. To umožňuje volání funkce následné restartování převodu, kde byla zastavena toto volání.  
  
 Pokud `wcstr` argument je ukazatel s hodnotou null, `count` argument je ignorován a `mbsrtowcs` vrátí požadovaná velikost široké znaky pro cílový řetězec. Pokud `mbstate` je ukazatel s hodnotou null, funkce, která používá interní není bezpečná pro přístup z více vláken statického `mbstate_t` převodu stavu objektu. Pokud sekvence znaků `mbstr` nemá odpovídající vícebajtových reprezentace znak, je vrácen -1 a `errno` je nastaven na `EILSEQ`.  
  
 Pokud `mbstr` ukazatele null isa, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí hodnotu -1.  
  
 Tato funkce v jazyce C++ má šabloně přetížení, které vyvolá novější a zabezpečené protějšku této funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="exceptions"></a>Výjimky  
 `mbsrtowcs` Tak dlouho, dokud volání funkce neexistuje v aktuální vlákno je funkce s více vlákny bezpečné `setlocale` tak dlouho, dokud tato funkce je prováděna a `mbstate` argument není nulový ukazatel.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`mbsrtowcs`|\<wchar.h >|  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtowc –](../../c-runtime-library/reference/mbrtowc.md)   
 [mbtowc –, _mbtowc_l –](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [mbstowcs –, _mbstowcs_l –](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)