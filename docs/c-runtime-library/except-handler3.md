---
title: "_except_handler3 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _except_handler3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- _except_handler3
- except_handler3
dev_langs:
- C++
helpviewer_keywords:
- _except_handler3 function
- except_handler3 function
ms.assetid: b0c64898-0ae5-48b7-9724-80135a0813e2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4fe280562d4f1278d74ae118712c9167de4b54d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="excepthandler3"></a>_except_handler3
Vnitřní funkce CRT. Rozhraní používá k vyhledání příslušné výjimky obslužná rutina zpracovávala aktuální výjimku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _except_handler3(  
   PEXCEPTION_RECORD exception_record,  
   PEXCEPTION_REGISTRATION registration,  
   PCONTEXT context,  
   PEXCEPTION_REGISTRATION dispatcher  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`exception_record`  
 Informace o určité výjimky.  
  
 [v]`registration`  
 Záznam, která určuje obor tabulek, které se má použít k vyhledání obslužná rutina výjimky.  
  
 [v]`context`  
 Vyhrazena.  
  
 [v]`dispatcher`  
 Vyhrazena.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud by měl zrušit výjimku, vrátí `DISPOSITION_DISMISS`. Pokud se výjimka by měla být o úroveň výš předána zapouzdřením obslužné rutiny výjimek, vrátí `DISPOSITION_CONTINUE_SEARCH`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud tato metoda vyhledá obslužnou rutinu příslušné výjimky, předá výjimku do obslužné rutiny. V takovém případě tato metoda nevrátí kód, který je volán a návratovou hodnotu je důležité.  
  
## <a name="see-also"></a>Viz také  
 [Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)