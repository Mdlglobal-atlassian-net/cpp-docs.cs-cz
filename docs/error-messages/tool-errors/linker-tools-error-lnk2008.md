---
title: "Chyba linkerů Lnk2008 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2008
dev_langs: C++
helpviewer_keywords: LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c8617c42c281ba5f469ee95c304d0888e1100847
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2008"></a>Chyba linkerů LNK2008
Oprava cíl není zarovnaný 'symbol_name.  
  
 ODKAZ najít oprava cíl v souboru objektu, který nebyl správně zarovnána.  
  
 Tato chyba může být způsobeno vlastní podle bodu zarovnání (například #pragma [pack](../../preprocessor/pack.md)), [zarovnat](../../cpp/align-cpp.md) modifikátor, nebo pomocí kódu jazyka sestavení, která mění podle bodu zarovnání.  
  
 Pokud váš kód nepoužívá výše uvedených možností, může být způsobeno kompilátorem.