---
title: -APPCONTAINER (aplikace pro Windows Store) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22ca7bec885f20518950626d33f7e3af553d0d52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="appcontainer-windows-store-app"></a>/APPCONTAINER (Aplikace pro web Windows Store)
Určuje, zda linkeru vytvoří spustitelné bitové kopie, který se musí spustit v kontejnerem aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení je /APPCONTAINER vypnuté.  
  
 Tato možnost upravuje spustitelný soubor indikující, zda aplikace musí být spuštěn v kontejneru appcontainer izolace procesu prostředí. Zadejte /APPCONTAINER pro aplikaci, která musí být spuštěný v prostředí appcontainer – například [!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)] aplikace. (Možnost nastavena automaticky v sadě Visual Studio při vytváření [!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)] aplikace ze šablony.) Pro desktopové aplikace zadejte /APPCONTAINER:NO nebo právě vynechejte možnost.  
  
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