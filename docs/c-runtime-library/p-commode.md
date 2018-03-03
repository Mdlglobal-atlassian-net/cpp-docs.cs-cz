---
title: __p__commode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 74d63f051c929dbf03b5077379c324b133034732
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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