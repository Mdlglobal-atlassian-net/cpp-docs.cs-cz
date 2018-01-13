---
title: _get_invalid_parameter_handler _get_thread_local_invalid_parameter_handler | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_invalid_parameter_handler
- stdlib/_get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- stdlib/_get_thread_local_invalid_parameter_handler
dev_langs: C++
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b00d6528301101729e032a63298dd0874bfa8ed5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="getinvalidparameterhandler-getthreadlocalinvalidparameterhandler"></a>_get_invalid_parameter_handler _get_thread_local_invalid_parameter_handler
Získá funkce, která je volána, když CRT zjistí neplatný argument.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_invalid_parameter_handler _get_invalid_parameter_handler(void);  
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktuálně nastavené neplatný parametr obslužné rutiny funkce nebo ukazatele null, pokud žádná nastavení.  
  
## <a name="remarks"></a>Poznámky  
 `_get_invalid_parameter_handler` Funkce získá aktuálně nastavené obslužné rutiny globální neplatný parametr. Vrátí ukazatele null, pokud byla nastavena žádná obslužná rutina globální neplatný parametr. Podobně `_get_thread_local_invalid_parameter_handler` získá obslužná rutina aktuální místní neplatný parametr se nazývá na vlákno nebo ukazatele null, pokud byla nastavena žádná obslužná rutina. Informace o tom, jak nastavit globální a místní neplatný parametr obslužné rutiny najdete v tématu [_set_invalid_parameter_handler –, _set_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).  
  
 Ukazatel na funkci obslužná rutina vrácený neplatný parametr má následujícího typu:  
  
```C  
typedef void (__cdecl* _invalid_parameter_handler)(  
    wchar_t const*,  
    wchar_t const*,  
    wchar_t const*,   
    unsigned int,  
    uintptr_t  
    );  
```  
  
 Podrobnosti na obslužnou rutinu neplatný parametr najdete v tématu prototyp v [_set_invalid_parameter_handler –, _set_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_get_invalid_parameter_handler`, `_get_thread_local_invalid_parameter_handler`|C: \<stdlib.h ><br /><br /> C++: \<cstdlib – > nebo \<stdlib.h >|  
  
 `_get_invalid_parameter_handler` a `_get_thread_local_invalid_parameter_handler` funkce se konkrétní společnosti Microsoft. Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [_set_invalid_parameter_handler –, _set_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)   
 [Verze funkcí CRT se zdokonaleným zabezpečením](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)