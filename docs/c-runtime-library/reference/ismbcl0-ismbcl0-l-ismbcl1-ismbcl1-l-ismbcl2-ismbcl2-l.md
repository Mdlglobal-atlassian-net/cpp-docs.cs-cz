---
title: "_ismbcl0 –, _ismbcl0_l –, _ismbcl1 –, _ismbcl1_l –, _ismbcl2 –, _ismbcl2_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _ismbcl2
- _ismbcl1
- _ismbcl0
- _ismbcl2_l
- _ismbcl1_l
- _ismbcl0_l
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
- ismbcl0
- _ismbcl1_l
- _ismbcl0
- ismbcl1
- ismbcl0_l
- _ismbcl2_l
- ismbcl2
- ismbcl1_l
- _ismbcl1
- _ismbcl0_l
- _ismbcl2
- ismbcl2_l
dev_langs:
- C++
helpviewer_keywords:
- _ismbcl0_l function
- _ismbcl2 function
- _ismbcl1_l function
- ismbcl2 function
- _ismbcl1 function
- ismbcl0_l function
- ismbcl2_l function
- ismbcl1_l function
- ismbcl0 function
- ismbcl1 function
- _ismbcl2_l function
- _ismbcl0 function
ms.assetid: ee15ebd1-462c-4a43-95f3-6735836d626a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 007b94015b0d898ccedf9d9a7a07d60b26f5faa7
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ismbcl0-ismbcl0l-ismbcl1-ismbcl1l-ismbcl2-ismbcl2l"></a>_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l
**Kód stránka 932 konkrétní funkce**, pomocí aktuální národní prostředí nebo zadané kategorii LC_CTYPE – převod stavu.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _ismbcl0(  
   unsigned int c   
);  
int _ismbcl0_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcl1(  
   unsigned int c   
);  
int _ismbcl1_l(  
   unsigned int c ,  
   _locale_t locale  
);  
int _ismbcl2(  
   unsigned int c   
);  
int _ismbcl2_l(  
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
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez `_l` příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s `_l` příponu jsou shodné s tím rozdílem, že používají předaný v místo toho parametr národního prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
|Rutina|Test stavu (pouze znaková stránka 932)|  
|-------------|-------------------------------------------|  
|`_ismbcl0`|JIS non-Kanji: 0x8140<=`c`<=0x889E.|  
|`_ismbcl0_l`|JIS non-Kanji: 0x8140<=`c`<=0x889E.|  
|`_ismbcl1`|Úroveň 1 JIS: 0x889F < =`c`< = 0x9872.|  
|`_ismbcl1_l`|Úroveň 1 JIS: 0x889F < =`c`< = 0x9872.|  
|`_ismbcl2`|Úroveň 2 JIS: 0x989F < =`c`< = 0xEAA4.|  
|`_ismbcl2_l`|Úroveň 2 JIS: 0x989F < =`c`< = 0xEAA4.|  
  
 Funkce zkontrolujte, zda zadaná hodnota `c` odpovídá podmínky testu popsané výše, ale není, zkontrolujte `c` je platný vícebajtových znaků. Pokud nižší bajt je v oblastech 0x00-0x3F, 0x7F nebo 0xFD - 0xFF, tyto funkce vrátí nenulovou hodnotu, která určuje, že znak, který splňuje podmínky testu. Použití [_ismbbtrail –](../../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) k ověření, zda je definována vícebajtových znaků.  
  
 **End kódu konkrétní stránka 932**  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_ismbcl0`|\<Mbstring.h >|  
|`_ismbcl0_l`|\<Mbstring.h >|  
|`_ismbcl1`|\<Mbstring.h >|  
|`_ismbcl1_l`|\<Mbstring.h >|  
|`_ismbcl2`|\<Mbstring.h >|  
|`_ismbcl2_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace znaků](../../c-runtime-library/character-classification.md)   
 [_ismbc Routines](../../c-runtime-library/ismbc-routines.md)   
 [is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)