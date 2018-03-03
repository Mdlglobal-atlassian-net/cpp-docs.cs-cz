---
title: "_setjmp3 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _setjmp3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- setjmp3
- _setjmp3
dev_langs:
- C++
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 72bc1e833ddaa72979e25274b7328d8987f62763
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="setjmp3"></a>_setjmp3
Vnitřní funkce CRT. Na nové implementace `setjmp` funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _setjmp3(  
   OUT jmp_buf env,  
   int count,  
   (optional parameters)  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`env`  
 Adresa vyrovnávací paměti pro ukládání informací o stavu.  
  
 [v]`count`  
 Počet Další `DWORD`s informací, které jsou uložené v `optional parameters`.  
  
 [v]`optional parameters`  
 Další data posunuta pomocí `setjmp` vnitřní. První `DWORD` je ukazatel na funkci, která se používá k unwind doplňující data a vrátit do stálého registru zaregistrovat stavu. Druhý `DWORD` je úroveň zkuste obnovit. Žádná další data se uloží do pole obecných datových v `jmp_buf`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 0.  
  
## <a name="remarks"></a>Poznámky  
 Nepoužívejte tuto funkci v programu C++. Je vnitřní funkce, která nepodporuje C++. Další informace o tom, jak používat `setjmp`, najdete v části [používání setjmp/longjmp](../cpp/using-setjmp-longjmp.md).  
  
## <a name="requirements"></a>Požadavky  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [setjmp](../c-runtime-library/reference/setjmp.md)