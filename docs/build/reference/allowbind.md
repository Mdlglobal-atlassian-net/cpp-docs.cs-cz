---
title: -ALLOWBIND | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af4a9f3d898d0087f0e8e861ccfe72e4adadb1de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368912"
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