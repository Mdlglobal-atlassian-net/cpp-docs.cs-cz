---
title: setjmp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: setjmp
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
apitype: DLLExport
f1_keywords: setjmp
dev_langs: C++
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 845c4eaac5c9aa0c4878016061eb07e6740f12f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="setjmp"></a>setjmp
Uloží aktuální stav programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int setjmp(  
   jmp_buf env   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `env`  
 Proměnná, ve kterém je uložený prostředí.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu 0 po uložení prostředí zásobníku. Pokud `setjmp` vrátí jako výsledek toho `longjmp` volat, vrátí `value` argument `longjmp`, nebo pokud `value` argument `longjmp` 0, `setjmp` vrátí hodnotu 1. Neexistuje žádný návratový chyby.  
  
## <a name="remarks"></a>Poznámky  
 `setjmp` Funkce uloží zásobníku prostředí, které můžete následně obnovit, pomocí `longjmp`. Při použití společně, `setjmp` a `longjmp` poskytnout způsob, jak provést jiné než místní `goto`. Jsou jsou obvykle používány k předat řízení provádění kódu zpracování chyb nebo obnovení pomocí dříve vyvolání rutiny bez použití normální volání nebo vrátit konvence.  
  
 Volání `setjmp` uloží aktuální prostředí zásobníku v `env`. Další volání `longjmp` obnoví uložené prostředí a vrátí ovládacího prvku do bodu bezprostředně za odpovídající `setjmp` volání. Všechny proměnné (s výjimkou registrace proměnné) dostupný pro rutiny přijetí řízení obsahovat hodnoty měly při `longjmp` byla volána.  
  
 Není možné použít `setjmp` přejít z nativní do spravovaného kódu.  
  
 **Poznámka:** `setjmp` a `longjmp` nepodporují sémantiku objekt C++. V programech, C++ použijte tento mechanismus zpracování výjimek C++.  
  
 Další informace najdete v tématu [pomocí setjmp a longjmp](../../cpp/using-setjmp-longjmp.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`setjmp`|\<setjmp.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [_fpreset –](../../c-runtime-library/reference/fpreset.md).  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [longjmp](../../c-runtime-library/reference/longjmp.md)   
 [_setjmp3](../../c-runtime-library/setjmp3.md)