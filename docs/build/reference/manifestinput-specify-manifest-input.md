---
title: -MANIFESTINPUT (určení vstupu manifestu) | Dokumentace Microsoftu
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
ms.openlocfilehash: d1b5ed266f1b8929deee3ffb60a10b18b7604afc
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464811"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Určit vstup manifestu)
Určuje vstupní soubor manifestu pro zahrnutí do manifestu, který je vložený v obrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/MANIFESTINPUT:filename  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Soubor manifestu pro zahrnutí do vloženého manifestu.  
  
## <a name="remarks"></a>Poznámky  
 **/MANIFESTINPUT** Určuje cestu vstupního souboru pro použití k tvorbě vloženého manifestu spustitelné bitové kopie. Pokud máte více vstupních souborů manifestu, použijte přepínač vícekrát – jednou pro každý vstupní soubor. Vstupní soubory manifestu jsou sloučeny pro tvorbu vloženého manifestu. Tato možnost vyžaduje **/MANIFEST: EMBED** možnost.  
  
 Tuto možnost nelze nastavit přímo v sadě Visual Studio. Místo toho použijte **přídavné soubory manifestu** vlastnosti projektu, chcete-li určit další soubory manifestu k zahrnutí. Další informace najdete v tématu [vstup a výstup, Nástroj Manifest, vlastnosti konfigurace, \<Projectname > dialogového okna stránky vlastností](../../ide/input-and-output-manifest-tool.md).  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)