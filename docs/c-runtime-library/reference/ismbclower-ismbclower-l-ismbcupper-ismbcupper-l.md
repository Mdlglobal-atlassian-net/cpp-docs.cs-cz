---
title: "_ismbclower –, _ismbclower_l –, _ismbcupper –, _ismbcupper_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
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
- _ismbcupper
- _ismbclower
dev_langs:
- C++
helpviewer_keywords:
- _ismbcupper function
- ismbclower function
- _ismbclower_l function
- ismbcupper_l function
- _ismbclower function
- ismbcupper function
- ismbclower_l function
- _ismbcupper_l function
ms.assetid: 17d89587-65bc-477c-ba8f-a84e63cf59e7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 865c2280ab395b5c8172ee978da16a2bcc26f7b9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ismbclower-ismbclowerl-ismbcupper-ismbcupperl"></a>_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l
Zkontroluje, jestli vícebajtových znaků malá nebo velká písmena.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _ismbclower(  
   unsigned int c   
);  
int _ismbclower_l(  
   unsigned int c,  
   _locale_t locale   
);  
int _ismbcupper(  
   unsigned int c   
);  
int _ismbcupper_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak, který má být testována.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Všechny tyto rutiny vrátí nenulovou hodnotu, pokud znak splňuje podmínky testu nebo 0, pokud neexistuje. Pokud `c`< = 255 a existuje odpovídající `_ismbb` rutiny (například `_ismbcalnum` odpovídá `_ismbbalnum`), výsledkem je vrácenou hodnotu odpovídající `_ismbb` rutiny.  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí testuje dané vícebajtových znaků pro danou podmínku.  
  
 Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že používají národní prostředí předaná místo aktuální národní prostředí pro jejich chování závislých na národním prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
|Rutina|Test stavu|Příklad kódu stránka 932|  
|-------------|--------------------|---------------------------|  
|`_ismbclower`|Malá písmena|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové k ASCII písmenu malá písmena anglické: 0x61 < =`c`< = 0x7A.|  
|`_ismbclower_l`|Malá písmena|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové k ASCII písmenu malá písmena anglické: 0x61 < =`c`< = 0x7A.|  
|`_ismbcupper`|Velká písmena|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové velkým písmenem ASCII anglické: 0x41 < =`c`< = 0x5A.|  
|`_ismbcupper_l`|Velká písmena|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové velkým písmenem ASCII anglické: 0x41 < =`c`< = 0x5A.|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_ismbclower`|\<Mbstring.h >|  
|`_ismbclower_l`|\<Mbstring.h >|  
|`_ismbcupper`|\<Mbstring.h >|  
|`_ismbcupper_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace znaků](../../c-runtime-library/character-classification.md)   
 [_ismbc Routines](../../c-runtime-library/ismbc-routines.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [je, isw – rutiny](../../c-runtime-library/is-isw-routines.md)   
 [_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)