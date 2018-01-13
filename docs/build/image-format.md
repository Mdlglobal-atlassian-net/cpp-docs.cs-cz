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
ms.workload: cplusplus
ms.openlocfilehash: c0761acfe02b7d86f9316d06913de15347e9d522
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="image-format"></a>Formát obrázku
Spustitelné bitové kopie není ve formátu PE32 +. Spustitelné bitové kopie (knihovny DLL a souborů exe) jsou omezeny na maximální velikost 2 gigabajty, takže relativní adresování s 32bitovým posunem můžete používat k adresování statických dat bitové kopie. Tato data zahrnují tabulku importních adres, řetězcové konstanty, statické globální data a tak dále.  
  
## <a name="see-also"></a>Viz také  
 [x64 – softwarové konvence](../build/x64-software-conventions.md)