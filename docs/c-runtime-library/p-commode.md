---
title: __p__commode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __p__commode
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __p__commode
dev_langs:
- C++
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e91c03f619be1d0f1d8ad23f3b8d60e1be30cfb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="pcommode"></a>__p__commode
Odkazuje na `_commode` globální proměnná, která určuje výchozí *režim souboru potvrzení* pro vstupně-výstupní operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
int * __p__commode(  
   );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel `_commode` – globální proměnná.  
  
## <a name="remarks"></a>Poznámky  
 `__p__commode` Funkce je jen pro interní použití a neměla být volána z uživatelského kódu.  
  
 Určuje režim souboru potvrzení při zápisu důležitých dat na disk. Další informace najdete v tématu [fflush –](../c-runtime-library/reference/fflush.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|__p\__commode|internal.h|