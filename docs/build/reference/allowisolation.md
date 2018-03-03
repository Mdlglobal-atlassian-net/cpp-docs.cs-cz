---
title: -ALLOWISOLATION | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ba0295d73e51e28fbdd953d7d9a3a2ae5131c27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="allowisolation"></a>/ALLOWISOLATION
Určuje chování pro vyhledání manifestu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 **/ ALLOWISOLATION** způsobí, že operační systém manifest vyhledávání a zatížení.  
  
 **/ ALLOWISOLATION** je výchozí.  
  
 **/ALLOWISOLATION:No** označuje, zda jsou načteny spustitelné soubory, jako kdyby nebyla žádná manifest a způsobí [Editbin – odkaz](../../build/reference/editbin-reference.md) nastavit `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bitů v hlavičce volitelné `DllCharacteristics` pole.  
  
 Při izolaci je zakázán pro spustitelný soubor, zavaděč systému Windows není zkuste najít manifest aplikace pro nově vytvořený proces. Nový proces nemá výchozí aktivační kontext, i když je manifestu v samotné spustitelný soubor nebo pokud je manifestu, který má název *název spustitelného souboru*. exe.manifest.  
  
## <a name="see-also"></a>Viz také  
 [– Možnosti nástroje EDITBIN](../../build/reference/editbin-options.md)   
 [/ ALLOWISOLATION (vyhledání manifestu)](../../build/reference/allowisolation-manifest-lookup.md)   
 [Manifest soubory – referenční dokumentace](http://msdn.microsoft.com/library/aa375632.aspx)