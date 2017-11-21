---
title: __argc, __argv, __wargv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __wargv
- __argv
- __argc
apilocation: msvcrt120.dll
apitype: DLLExport
f1_keywords:
- __argv
- __argc
- __wargv
dev_langs: C++
helpviewer_keywords:
- __argv
- __wargv
- __argc
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dbb6e0886844cda7142ee52fcb545e122c38ea8e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="argc-argv-wargv"></a>__argc, __argv, __wargv
`__argc` – Globální proměnná je počet argumentů příkazového řádku předaný do programu. `__argv`ukazatel na pole znaková jeden nebo více byte znakové řetězce, které obsahují argumenty program a `__wargv` je ukazatel na pole široká charakterová řetězců, které obsahují argumenty programu. Tyto globální proměnné zadejte argumenty, které mají `main` nebo `wmain`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
extern int __argc;  
extern char ** __argv;  
extern wchar_t ** __wargv;  
```  
  
## <a name="remarks"></a>Poznámky  
 V programu, který používá `main` funkce, `__argc` a `__argv` jsou inicializovány při spuštění programu pomocí příkazového řádku, který se používá ke spuštění programu. Příkazový řádek je analyzován do jednotlivých argumenty a rozbaleny zástupné znaky. Počet argumentů je přiřazena k `__argc` argument řetězce mají při přidělování v haldě a ukazatel na pole argumentů je přiřazena k `__argv`. V programu zkompilovat použít široké znaky a `wmain` funkce, argumenty, které jsou analyzovány a zástupné znaky jsou rozšířit jako řetězce široká charakterová a ukazatel na pole řetězců. argument je přiřazena k `__wargv`.  
  
 Pro přenosné kód, doporučujeme, abyste použili argumenty předávané `main` získat argumenty příkazového řádku v programu.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE není definován|_UNICODE definováno|  
|---------------------|---------------------------|-----------------------|  
|`__targv`|`__argv`|`__wargv`|  
  
## <a name="requirements"></a>Požadavky  
  
|Globální proměnná|Požadovaný hlavičkový soubor|  
|---------------------|---------------------|  
|`__argc`, `__argv`, `__wargv`|\<stdlib.h >, \<cstdlib – > (C++)|  
  
 `__argc`, `__argv`, a `__wargv` jsou rozšíření Microsoft. Informace o kompatibilitě, najdete v části [kompatibility](../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Globální proměnné](../c-runtime-library/global-variables.md)   
 [hlavní: spuštění programu](../cpp/main-program-startup.md)   
 [Použití funkce wmain namísto main](../cpp/using-wmain-instead-of-main.md)