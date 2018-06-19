---
title: -ALLOWISOLATION | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5cb92a7f31d48dad4a7fb608703c71ccc661e176
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368971"
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