---
title: -ALLOWISOLATION | Dokumentace Microsoftu
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
ms.openlocfilehash: b9511ce2d94a426756581b87d863051da25a627b
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2018
ms.locfileid: "42466408"
---
# <a name="allowisolation"></a>/ALLOWISOLATION
Určuje chování při vyhledávání manifestu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 **/ ALLOWISOLATION** způsobí, že operační systém k vyhledání a načtení manifestu.  
  
 **/ ALLOWISOLATION** je výchozí nastavení.  
  
 **/ALLOWISOLATION:No** označuje, zda jsou načteny spustitelné soubory, jako by nebyly žádné manifestu a způsobí, že [Editbin – referenční dokumentace](../../build/reference/editbin-reference.md) nastavit `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit ve volitelné hlavičce `DllCharacteristics` pole.  
  
 Izolace zakázán pro spustitelný soubor, nebude Windows zavaděče pokuste se najít manifest aplikace pro nově vytvořený procesu. Nový proces nemá výchozí aktivační kontext, i když je manifest ve spustitelném souboru, samotné nebo pokud je manifest, který má název *název spustitelného souboru*. exe.manifest.  
  
## <a name="see-also"></a>Viz také  
 [– Možnosti nástroje EDITBIN](../../build/reference/editbin-options.md)   
 [/ ALLOWISOLATION (vyhledání manifestu)](../../build/reference/allowisolation-manifest-lookup.md)   
 [Referenční příručka souborů manifestu](/windows/desktop/SbsCs/manifest-files-reference)