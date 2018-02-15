---
title: "_get_current_locale – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _get_current_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_current_locale
- __get_current_locale
- _get_current_locale
dev_langs:
- C++
helpviewer_keywords:
- get_current_locale function
- _get_current_locale function
- locales, getting information on
- __get_current_locale function
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7199cb6cf4f0451f4607c7b9cd8a670a4d5afe2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="getcurrentlocale"></a>_get_current_locale
Získá objekt národního prostředí představující aktuální národní prostředí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_locale_t _get_current_locale(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Objekt národního prostředí představující aktuální národní prostředí.  
  
## <a name="remarks"></a>Poznámky  
 `_get_current_locale` Funkce získá aktuálně nastavené národní prostředí pro vlákno a vrátí objekt národního prostředí reprezentující toto národní prostředí.  
  
 Předchozí název této funkce `__get_current_locale` (se dvěma úvodní podtržítka) je zastaralá.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_get_current_locale`|\<Locale.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [setlocale –, _wsetlocale –](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [_free_locale](../../c-runtime-library/reference/free-locale.md)