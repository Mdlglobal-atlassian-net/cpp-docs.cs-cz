---
title: -MANIFESTINPUT (určit vstup manifestu) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eecf1740855c2feef0d7cac4bbcc85ad95eade6f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372848"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Určit vstup manifestu)
Určuje soubor manifestu vstupní chcete zahrnout do manifestu, který se vloží do bitové kopie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/MANIFESTINPUT:filename  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Soubor manifestu pro zahrnutí do vložený manifest.  
  
## <a name="remarks"></a>Poznámky  
 **/MANIFESTINPUT** možnost určuje cestu k souboru vstupní sloužící k vytvoření embedded manifestu v spustitelné bitové kopie. Pokud máte více manifest vstupní soubory, použijte přepínač několikrát – jednou pro každý vstupní soubor. Chcete-li vytvořit vložený manifest jsou sloučeny manifestu vstupní soubory. Tato možnost vyžaduje **/MANIFEST: vložení** možnost.  
  
 Tuto možnost nelze nastavit přímo v [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]. Místo toho použijte **další soubory manifestu** vlastností projektu a určete další soubory manifestu zahrnout. Další informace najdete v tématu [vstup a výstup, Nástroj Manifest, vlastnosti konfigurace \<název projektu > dialogové okno stránky vlastností](../../ide/input-and-output-manifest-tool.md).  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)