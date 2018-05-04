---
title: / APPCONTAINER (aplikace pro UPW nebo Microsoft Store) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ca1a3ed5adaada689d374eeb3e67bae6c989e0b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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