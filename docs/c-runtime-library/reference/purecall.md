---
title: "_purecall – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _purecall
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
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- purecall
- _purecall
dev_langs: C++
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c475c66c92dec7990aa8056a1791c8eeb87d6afa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="purecall"></a>_purecall
Výchozí čistou virtuální funkci volání obslužné rutiny. Kompilátor generuje kód pro volání této funkce, když je volána funkce čistý člena virtuální.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
extern "C" int __cdecl _purecall();  
```  
  
## <a name="remarks"></a>Poznámky  
 `_purecall` Je funkce specifická pro společnost Microsoft podrobnosti implementace Microsoft Visual C++ compiler. Tato funkce není určená k volání přímo pomocí kódu a nemá žádné veřejné hlavičce deklarace. Jsou zde uvedeny vzhledem k tomu, že je veřejná export běhové knihovny jazyka C.  
  
 Volání čistou virtuální funkci se o chybu, protože nemá žádné implementace. Kompilátor generuje kód pro vyvolání `_purecall` funkce obslužné rutiny Chyba při volání čistou virtuální funkci. Ve výchozím nastavení `_purecall` ukončí program. Před ukončení, `_purecall` funkce vyvolá `_purecall_handler` fungovat, pokud byla nastavena pro proces. Můžete nainstalovat funkci obslužné rutiny vlastní chyby pro volání čistou virtuální funkci, je pro ladění nebo účely vytváření sestav zachytit. Pokud chcete používat vlastní obslužnou rutinu chyby, vytvořte funkci, která má `_purecall_handler` podpis, pak použít [_set_purecall_handler –](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md) Chcete-li obslužná rutina aktuální.  
  
## <a name="requirements"></a>Požadavky  
 `_purecall` Funkce nemá deklaraci záhlaví. `_purecall_handler` Typedef je definována v \<stdlib.h >.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_get_purecall_handler, _set_purecall_handler –](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)