---
title: "_ismbbgraph –, _ismbbgraph_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbbgraph_l
- _ismbbgraph
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
- _ismbbgraph
- _ismbbgraph_l
- ismbbgraph
- ismbbgraph_l
dev_langs: C++
helpviewer_keywords:
- _ismbbgraph_l function
- ismbbgraph_l function
- _ismbbgraph function
- ismbbgraph function
ms.assetid: b60db718-134f-4796-acc1-592d0b9efbb7
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3638740d4a62e42da71a7b076e636443e0530cdc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ismbbgraph-ismbbgraphl"></a>_ismbbgraph, _ismbbgraph_l
Určuje, zda je konkrétní vícebajtových znaků grafické znak.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _ismbbgraph (  
   unsigned int c   
);  
int _ismbbgraph_l (  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Celé číslo má být testována.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí nenulovou hodnotu, pokud výraz:  
  
```  
( _PUNCT | _UPPER | _LOWER | _DIGIT ) || _ismbbkprint  
```  
  
 je nenulové hodnoty pro `c`, nebo 0, pokud není. `_ismbbgraph`používá aktuální národní prostředí pro chování všech závislých na národním prostředí. `_ismbbgraph_l`se shoduje s tím rozdílem, že používá národní prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_ismbbgraph`|\<Mbctype.h >|  
|`_ismbbgraph_l`|\<Mbctype.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace bajtů](../../c-runtime-library/byte-classification.md)   
 [_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)