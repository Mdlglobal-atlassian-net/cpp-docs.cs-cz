---
title: __p__fmode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __p__fmode
apilocation:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords: __p__fmode
dev_langs: C++
helpviewer_keywords: __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0a563385ecd1e773433e053cffbae24403eab6fc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="pfmode"></a>__p__fmode
Odkazuje na `_fmode` globální proměnná, která určuje výchozí *režim překladu souboru* pro vstupně-výstupní operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
int* __p__fmode(  
   );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel `_fmode` – globální proměnná.  
  
## <a name="remarks"></a>Poznámky  
 `__p__fmode` Funkce je jen pro interní použití a neměla být volána z uživatelského kódu.  
  
 Určuje režim překladu souboru buď `binary` nebo `text` překlad [_Otevřít](../c-runtime-library/reference/open-wopen.md) a [_pipe –](../c-runtime-library/reference/pipe.md) vstupně-výstupních operací. Další informace najdete v tématu [_fmode –](../c-runtime-library/fmode.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|__p\__fmode –|stdlib.h|