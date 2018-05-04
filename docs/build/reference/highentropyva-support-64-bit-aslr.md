---
title: -HIGHENTROPYVA (podpora 64bitové technologie ASLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de2487cbeff97ded6e95a36393fbbcfbd510e6d0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (podpora 64bitové technologie ASLR)
Určuje, že spustitelné bitové kopie podporuje vysokou entropií 64-bit adresu místa rozložení náhodné (technologie ASLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/HIGHENTROPYVA[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení je/highentropyva na pro 64bitové spustitelné bitové kopie. Není použitelná pro 32-bit spustitelné bitové kopie. Chcete-li tuto možnost, musí být na také /DYNAMICBASE.  
  
 / HIGHENTROPYVA upravuje hlavičku souboru .dll nebo .exe indikující, zda je podporováno technologie ASLR s adresami 64-bit. Pokud je tato možnost nastavená na spustitelný soubor a všechny moduly, které závisí na, operační systém, který podporuje 64bitové technologie ASLR rebase segmentů spustitelné bitové kopie v době zatížení pomocí náhodnou adres v 64-bit virtuálního adresového prostoru. Tento velký adresní prostor je obtížnější pro útočníka tak snadno uhodnout umístění paměti konkrétní oblasti.  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **příkazového řádku** stránku vlastností.  
  
5.  V **další možnosti**, zadejte `/HIGHENTROPYVA` nebo `/HIGHENTROPYVA:NO`.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)