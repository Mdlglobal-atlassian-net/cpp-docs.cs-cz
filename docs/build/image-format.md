---
title: "Bitovou kopii formátu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5cc70468d5b3ce9f678c1cd563ac79f172cedcc8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="image-format"></a>Formát obrázku
Spustitelné bitové kopie není ve formátu PE32 +. Spustitelné bitové kopie (knihovny DLL a souborů exe) jsou omezeny na maximální velikost 2 gigabajty, takže relativní adresování s 32bitovým posunem můžete používat k adresování statických dat bitové kopie. Tato data zahrnují tabulku importních adres, řetězcové konstanty, statické globální data a tak dále.  
  
## <a name="see-also"></a>Viz také  
 [x64 softwarové konvence](../build/x64-software-conventions.md)