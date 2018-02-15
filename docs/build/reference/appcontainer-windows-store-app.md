---
title: / APPCONTAINER (aplikace pro UPW nebo Microsoft Store) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1cc6e1d4c6e18cd2118571e57f671f85a0a3fb55
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="appcontainer-microsoft-store-app"></a>/ APPCONTAINER (aplikace Microsoft Store)
Určuje, zda linkeru vytvoří spustitelné bitové kopie, který se musí spustit v kontejnerem aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení je /APPCONTAINER vypnuté.  
  
 Tato možnost upravuje spustitelný soubor indikující, zda aplikace musí být spuštěn v kontejneru appcontainer izolace procesu prostředí. Zadejte /APPCONTAINER pro aplikaci, která musí být spuštěný v prostředí appcontainer – například univerzální platformu Windows (UWP) nebo Windows Phone 8.x aplikace. (Možnost nastavena automaticky v sadě Visual Studio při vytvoření aplikace pro univerzální Windows ze šablony.) Pro desktopové aplikace zadejte /APPCONTAINER:NO nebo právě vynechejte možnost.  
  
 Možnost /APPCONTAINER byla zavedena v [!INCLUDE[win8](../../build/reference/includes/win8_md.md)].  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **příkazového řádku** stránku vlastností.  
  
5.  V **další možnosti**, zadejte `/APPCONTAINER` nebo `/APPCONTAINER:NO`.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)