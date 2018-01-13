---
title: -ALLOWBIND | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /allowbind
dev_langs: C++
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a4cbd5c619b0a9e146adb9a8ec9117f59e01b89d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="allowbind"></a>/ALLOWBIND
Určuje, zda mohou být vázány knihovny DLL.  
  
```  
  
/ALLOWBIND[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 **/ALLOWBIND** možnost nastaví trochu v záhlaví knihovny DLL, která určuje Bind.exe, že bitovou kopii, může být vázána. Vazba můžete povolit bitovou kopii načíst rychleji, když zavaděč nemá rebase a provádět Oprava adres pro každou knihovnu DLL, odkazovaná. Je možné, knihovny DLL vázat, pokud byly digitálně podepsané – vazba se zruší platnost podpisu. Vazba nemá vliv, pokud adresa místa rozložení náhodné (technologie ASLR) je povolený pro bitovou kopii pomocí **/DYNAMICBASE** ve verzích systému Windows, které podporují technologie ASLR.  
  
 Použití **/ALLOWBIND:NO** Bind.exe zabránit vytvoření vazby knihovnu DLL.  
  
 Další informace najdete v tématu [/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md) – možnost linkeru.  
  
## <a name="see-also"></a>Viz také  
 [EDITBIN – možnosti](../../build/reference/editbin-options.md)