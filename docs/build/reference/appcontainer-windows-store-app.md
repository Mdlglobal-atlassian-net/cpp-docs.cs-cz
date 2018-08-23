---
title: / APPCONTAINER (aplikace pro UPW/Microsoft Store) | Dokumentace Microsoftu
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
ms.openlocfilehash: eab6a9bd8ac37dec250739e3554c370726dce9eb
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589574"
---
# <a name="appcontainer-microsoft-store-app"></a>/ APPCONTAINER (aplikace pro Microsoft Store)
Určuje, zda linker vytvoří spustitelný obraz, který musí být spuštěn v kontejneru aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení je/appcontainer vypnut.  
  
 Tato možnost změní spustitelný soubor k označení, zda je třeba aplikaci spustit v prostředí izolace procesu appcontainer. Určit/appcontainer pro aplikaci, která se musí spustit v prostředí appcontainer, například univerzální platformu Windows (UPW) nebo Windows Phone 8.x aplikace. (Možnost je nastavena automaticky v sadě Visual Studio při vytváření aplikace Universal Windows ze šablony.) Pro desktopové aplikace zadejte /APPCONTAINER:NO nebo možnost jednoduše vynechejte.  
  
 Možnost/appcontainer byla zavedena v systému Windows 8.  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **příkazového řádku** stránku vlastností.  
  
5.  V **další možnosti**, zadejte `/APPCONTAINER` nebo `/APPCONTAINER:NO`.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)