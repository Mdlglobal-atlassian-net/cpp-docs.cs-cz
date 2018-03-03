---
title: Robustnost | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fb071b615d87ab1b605c78e5ba0645be139fba1b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="robustness"></a>Robustnost
Použijte následující funkce běhové knihovny jazyka C programy vašeho programu.  
  
### <a name="run-time-robustness-functions"></a>Robustnost běhové funkce  
  
|Funkce|Použití|  
|--------------|---------|  
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Přenosy ovládacího prvku na váš mechanismus zpracování chyb, pokud `new` operátor se nepodařilo přidělit paměť.|  
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Obslužné rutiny výjimky Win32 (C strukturovaná výjimky) jako C++ zadali výjimky.|  
|[set_terminate –](../c-runtime-library/reference/set-terminate-crt.md)|Nainstaluje ukončení funkce má být volána [ukončit](../c-runtime-library/reference/terminate-crt.md).|  
|[set_unexpected –](../c-runtime-library/reference/set-unexpected-crt.md)|Nainstaluje ukončení funkce má být volána [neočekávané](../c-runtime-library/reference/unexpected-crt.md).|  
  
## <a name="see-also"></a>Viz také  
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)   
 [SetUnhandledExceptionFilter](http://msdn.microsoft.com/library/windows/desktop/ms680634.aspx)