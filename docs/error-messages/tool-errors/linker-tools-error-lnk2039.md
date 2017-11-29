---
title: "Chyba linkerů Lnk2039 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2039
dev_langs: C++
helpviewer_keywords: LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fa023412ab7f79b04fcc6c3c2ebf52eeeda2e53a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2039"></a>Chyba linkerů LNK2039
Import ref třída\<typu >, která je definovaná v another.obj, je nutné buď importované nebo definované, ale ne pomocí obou  
  
 Třída ref ' <`type`>' je v souboru .obj zadaný naimportovány, ale je rovněž definovaný v jiném souboru .obj. Tento stav může způsobit selhání běhového prostředí nebo jiné neočekávanému chování.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, zda se`type`' musí být definován v souboru .obj jiných a zkontrolujte, zda musí být importovány ze souboru .winmd.  
  
2.  Odeberte definici nebo import.  
  
## <a name="see-also"></a>Viz také  
 [Chyby a upozornění Linkerů](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)   
 [Chyba linkerů LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)