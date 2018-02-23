---
title: "_ismbchira –, _ismbchira_l –, _ismbckata –, _ismbckata_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _ismbckata
- _ismbchira_l
- _ismbchira
- _ismbckata_l
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
- ismbckata_l
- _ismbckata_l
- ismbckata
- ismbchira
- _ismbckata
- ismbchira_l
- _ismbchira_l
- _ismbchira
dev_langs:
- C++
helpviewer_keywords:
- _ismbckata function
- _ismbchira function
- _ismbckata_l function
- Katakana
- ismbchira function
- _ismbchira_l function
- ismbchira_l function
- ismbdkata_l function
- Hiragana
- ismbckata function
ms.assetid: 2db388a2-be31-489b-81c8-f6bf3f0582d3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 38fe65f2b81def4afe08339f38b00cd69702fd83
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ismbchira-ismbchiral-ismbckata-ismbckatal"></a>_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l
**Stránka 932 konkrétní funkce kódu**  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _ismbchira(  
   unsigned int c   
);  
int _ismbchira_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbckata(  
   unsigned int c   
);  
int _ismbckata_l(  
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
 Všechny tyto rutiny vrátí nenulovou hodnotu, pokud znak splňuje podmínky testu nebo 0, pokud neexistuje. Pokud `c` < = 255 a existuje odpovídající `_ismbb` rutiny (například `_ismbcalnum` odpovídá `_ismbbalnum`), výsledkem je vrácenou hodnotu odpovídající `_ismbb` rutiny.  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí testuje dané vícebajtových znaků pro danou podmínku.  
  
 Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že používají národní prostředí předaná místo aktuální národní prostředí pro jejich chování závislých na národním prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
|Rutina|Test stavu (pouze znaková stránka 932)|  
|-------------|-------------------------------------------|  
|`_ismbchira`|Dvoubajtové Hiragana: 0x829F < =`c`< = 0x82F1.|  
|`_ismbchira_l`|Dvoubajtové Hiragana: 0x829F < =`c`< = 0x82F1.|  
|`_ismbckata`|Dvoubajtové katakana: 0x8340 < =`c`< = 0x8396.|  
|`_ismbckata_l`|Dvoubajtové katakana: 0x8340 < =`c`< = 0x8396.|  
  
 **End kódu konkrétní stránka 932**  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_ismbchira`|\<Mbstring.h >|  
|`_ismbchira_l`|\<Mbstring.h >|  
|`_ismbckata`|\<Mbstring.h >|  
|`_ismbckata_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace znaků](../../c-runtime-library/character-classification.md)   
 [_ismbc Routines](../../c-runtime-library/ismbc-routines.md)   
 [je, isw – rutiny](../../c-runtime-library/is-isw-routines.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)