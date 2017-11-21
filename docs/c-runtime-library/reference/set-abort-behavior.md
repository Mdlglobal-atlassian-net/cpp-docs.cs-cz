---
title: "_set_abort_behavior – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_abort_behavior
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
- _set_abort_behavior
- set_abort_behavior
dev_langs: C++
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.assetid: 43918766-e4ba-4b1f-80e8-1a4a910cd452
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: edf31ccddfb9ab2eaa6de226ff4ec7eb09869438
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="setabortbehavior"></a>_set_abort_behavior
Určuje akci, která mají být provedeny, když program je ukončen neobvyklým způsobem.  
  
> [!NOTE]
>  Nepoužívejte `abort` funkce vypnout [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace, kromě testování nebo ladění scénáře. Programový nebo uživatelského rozhraní způsoby zavřete [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace nejsou povolené podle požadavků [požadavky na certifikaci aplikace systému Windows 8](http://go.microsoft.com/fwlink/?LinkId=262889). Další informace najdete v tématu [životního cyklu aplikací (aplikace pro Windows Store)](http://go.microsoft.com/fwlink/?LinkId=262853).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned int _set_abort_behavior(  
   unsigned int flags,  
   unsigned int mask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`flags`  
 Nová hodnota `abort` příznaky.  
  
 [v]`mask`  
 Maskování pro `abort` flags bits k nastavení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Původní hodnota příznaků.  
  
## <a name="remarks"></a>Poznámky  
 Existují dva `abort` příznaky: `_WRITE_ABORT_MSG` a `_CALL_REPORTFAULT`. `_WRITE_ABORT_MSG`Určuje, zda je vytištěna užitečné textovou zprávu, když program je ukončen neobvyklým způsobem. Zpráva, že aplikace volal `abort` funkce. Výchozí chování je tisknout zprávy. `_CALL_REPORTFAULT`, pokud nastavení, určuje, že stav systému Watson se generuje a kdy hlášené `abort` je volána. Ve výchozím nastavení je hlášení chyb výpisu povolené v sestavení bez ladění.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_set_abort_behavior`|\<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_set_abort_behavior.c  
// compile with: /TC  
#include <stdlib.h>  
  
int main()  
{  
   printf("Suppressing the abort message. If successful, this message"  
          " will be the only output.\n");  
   // Suppress the abort message  
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);  
   abort();  
}  
```  
  
```Output  
Suppressing the abort message. If successful, this message will be the only output.  
```  
  
## <a name="see-also"></a>Viz také  
 [přerušení](../../c-runtime-library/reference/abort.md)