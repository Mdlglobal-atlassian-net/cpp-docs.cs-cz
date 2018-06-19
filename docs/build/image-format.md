---
title: Bitovou kopii formátu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 356480333a62d998213726016f3940b318c218a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367937"
---
# <a name="image-format"></a>Formát obrázku
Spustitelné bitové kopie není ve formátu PE32 +. Spustitelné bitové kopie (knihovny DLL a souborů exe) jsou omezeny na maximální velikost 2 gigabajty, takže relativní adresování s 32bitovým posunem můžete používat k adresování statických dat bitové kopie. Tato data zahrnují tabulku importních adres, řetězcové konstanty, statické globální data a tak dále.  
  
## <a name="see-also"></a>Viz také  
 [x64 – softwarové konvence](../build/x64-software-conventions.md)