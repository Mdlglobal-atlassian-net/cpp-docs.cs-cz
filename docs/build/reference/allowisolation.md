---
title: -ALLOWISOLATION | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /ALLOWISOLATION
dev_langs: C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bb0a3973b140e452d3cb1198c5a98ca2caf61a1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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