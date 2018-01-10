---
title: _callnewh | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _callnewh
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords: _callnewh
dev_langs: C++
helpviewer_keywords: _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86085472c63d2ad3fbc1cf53d893bd8da2f8c244
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="callnewh"></a>_callnewh
Volá aktuálně nainstalované *novou obslužnou rutinu*.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
int _callnewh(  
   size_t size  
   )  
```  
  
#### <a name="parameters"></a>Parametry  
 `size`  
 Velikost paměti, který [operátor new](../../cpp/new-operator-cpp.md) pokusil přidělit.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|0|Chyba: Žádné nové rutiny se nainstaluje nebo žádné nové obslužná rutina je aktivní.|  
|1|Úspěch: Novou obslužnou rutinu je nainstalována a aktivní. Přidělení paměti můžete opakovat.|  
  
## <a name="exceptions"></a>Výjimky  
 Tato funkce vyvolá [bad_alloc](../../standard-library/bad-alloc-class.md) Pokud *novou obslužnou rutinu* nebyl nalezen.  
  
## <a name="remarks"></a>Poznámky  
 *Novou obslužnou rutinu* je volána, pokud [operátor new](../../cpp/new-operator-cpp.md) nepodaří úspěšně přidělit paměť. Nové obslužná rutina může potom zahájit některé příslušné akce, jako je například uvolnění paměti, aby být úspěšné následné přidělení.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|_callnewh|internal.h|  
  
## <a name="see-also"></a>Viz také  
 [_set_new_handler –](../../c-runtime-library/reference/set-new-handler.md)   
 [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md)