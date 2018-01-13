---
title: "_local_unwind2 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _local_unwind2
apilocation:
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- _local_unwind2
- local_unwind2
dev_langs: C++
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3b0c027623f5b562219e46c67ef730754538d602
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="localunwind2"></a>_local_unwind2
Vnitřní funkce CRT. Spouští všechny obslužné rutiny ukončení, které jsou uvedené v tabulce uvedené oboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _local_unwind2(  
   PEXCEPTION_REGISTRATION xr,  
   int stop  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`xr`  
 Registrační záznam, který je přidružen jeden obor tabulky.  
  
 [v]`stop`  
 Lexikální úroveň, která určuje, kde `_local_unwind2` by se měla zastavit.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se používá pouze v prostředí runtime. Nevolejte metodu v kódu.  
  
 Když tato metoda provede obslužné rutiny ukončení, začne na aktuální úrovni lexikální a funguje jeho způsobem až lexikální úrovně, dokud nedosáhne úroveň, která je indikován `stop`. Nepracuje obslužné rutiny ukončení na úrovni označená `stop`.  
  
## <a name="see-also"></a>Viz také  
 [Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)