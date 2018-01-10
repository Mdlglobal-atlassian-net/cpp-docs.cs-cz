---
title: mbrtoc16 mbrtoc323 | Microsoft Docs
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
- mbrtoc16
- mbrtoc32
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
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
dev_langs: C++
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c24a7426c788ac7ecfc98f3e649397912960505a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16 mbrtoc32
Změní první vícebajtových znaků v řetězci omezený na ekvivalentní UTF-16 nebo UTF-32 znaků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t mbrtoc16(   
   char16_t* destination,   
   const char* source,   
   size_t max_bytes,   
   mbstate_t* state   
);  
  
size_t mbrtoc32(  
   char32_t* destination,   
   const char* source,   
   size_t max_bytes,   
   mbstate_t* state   
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `destination`  
 Ukazatel `char16_t` nebo `char32_t` ekvivalentní vícebajtových znaků pro převod. Pokud hodnotu null, funkce neukládá hodnotu.  
  
 `source`  
 Ukazatel na vícebajtový řetězec k převedení.  
  
 `max_bytes`  
 Maximální počet bajtů v `source` prozkoumat pro znak pro převod. To by měl mít hodnotu mezi jeden a počet bajtů, včetně všech null ukončovací zbývající v `source`.  
  
 `state`  
 Ukazatel na `mbstate_t` objekt stavu převod použité k interpretaci vícebajtové řetězec, který má jeden nebo více znaků výstup.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu první z těchto podmínek, které se vztahuje zadaný aktuální `state` hodnotu:  
  
|Hodnota|Podmínka|  
|-----------|---------------|  
|0|Další `max_bytes` nebo méně znaků převedena z `source` odpovídají null široké znaku, který je uložen, pokud hodnota `destination` není null.<br /><br /> `state`obsahuje stav počáteční shift.|  
|Mezi 1 a `max_bytes`(včetně)|Hodnota vrácená je počet bajtů `source` , dokončete platný vícebajtových znaků. Převedený široká znaková je uložen, pokud `destination` není null.|  
|-3|Další široká znaková vyplývající z předchozího volání funkce byla uložena v `destination` Pokud `destination` není null. Žádné bajtů z `source` se spotřebovávají toto volání funkce.<br /><br /> Když `source` odkazuje na vícebajtových znaků, který vyžaduje více než jeden znak širokou představovat (například náhradní pár), pak se `state` hodnota je aktualizována tak, aby další volání funkce zapíše na další znak.|  
|-2|Další `max_bytes` bajtů představují neúplnou, ale potenciálně platný, vícebajtových znaků. Žádná hodnota je uložena v `destination`. Tento výsledek může dojít, pokud `max_bytes` je nulová.|  
|-1|Došlo k chybě kódování. Další `max_bytes` nebo méně bajtů nepřispívají k dokončení a platné vícebajtových znaků. Žádná hodnota je uložena v `destination`.<br /><br /> `EILSEQ`je uložený v `errno` a stav převodu `state` není zadáno.|  
  
## <a name="remarks"></a>Poznámky  
 `mbrtoc16` Funkce přečte až `max_bytes` bajtů z `source` najít první dokončení, platný vícebajtových znaků a potom úložiště ekvivalentní UTF-16 znaků v `destination`. Počet bajtů zdroje se interpretují podle aktuální vícebajtové národní prostředí vlákna. Pokud vícebajtových znaků vyžaduje více než jeden znak výstup UTF-16, jako je například náhradní pár, pak se `state` hodnota nastavena na ukládat další znak UTF-16 v `destination` na další volání `mbrtoc16`. `mbrtoc32` Funkce je stejné, ale výstup se ukládají jako znakové sady UTF-32 znaků.  
  
 Pokud `source` má hodnotu null, tyto funkce návratový ekvivalent volání vytvořené pomocí argumenty `NULL` pro `destination`, `""` pro `source`, a `1` pro `max_bytes`. Předané hodnoty `destination` a `max_bytes` jsou ignorovány.  
  
 Pokud `source` je hodnotou not null, funkce spustí na začátku řetězce a zkontroluje až `max_bytes` bajtů můžete určit počet bajtů, které jsou nutné pro dokončení další vícebajtových znaků, včetně jakýchkoli pořadí shift. Pokud testovaných bajtů neobsahují platný a dokončení vícebajtových znaků, převede funkce znak ekvivalentní 16bitové nebo 32bitové široká znaková nebo znaky. Pokud `destination` není null, funkce úložiště výsledek první (a případně pouze) znak v cílovém umístění. Pokud jsou vyžadovány další výstup znaky, je zadána hodnota `state`tak, aby následující volání funkce výstup další znaky a vrátí hodnotu -3. Pokud další znaky výstup nejsou povinné, pak `state` nastavena do stavu počáteční shift.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`mbrtoc16`,                `mbrtoc32`|\<uchar.h >|\<cuchar >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [c16rtomb c32rtomb](../../c-runtime-library/reference/c16rtomb-c32rtomb1.md)   
 [mbrtowc –](../../c-runtime-library/reference/mbrtowc.md)   
 [mbsrtowcs –](../../c-runtime-library/reference/mbsrtowcs.md)   
 [mbsrtowcs_s](../../c-runtime-library/reference/mbsrtowcs-s.md)