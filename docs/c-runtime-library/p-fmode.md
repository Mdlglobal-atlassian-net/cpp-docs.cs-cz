---
title: __p__fmode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __p__fmode
apilocation:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- __p__fmode
dev_langs:
- C++
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c520f81062f1bbbb295f17c6bc041afb8b5f2877
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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