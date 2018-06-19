---
title: Chyba linkerů Lnk2008 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2008
dev_langs:
- C++
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4ee6a8a4c4cc6d33f47d5335daa9fccd4e5fd99
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299562"
---
# <a name="linker-tools-error-lnk2008"></a>Chyba linkerů LNK2008
Oprava cíl není zarovnaný 'symbol_name.  
  
 ODKAZ najít oprava cíl v souboru objektu, který nebyl správně zarovnána.  
  
 Tato chyba může být způsobeno vlastní podle bodu zarovnání (například #pragma [pack](../../preprocessor/pack.md)), [zarovnat](../../cpp/align-cpp.md) modifikátor, nebo pomocí kódu jazyka sestavení, která mění podle bodu zarovnání.  
  
 Pokud váš kód nepoužívá výše uvedených možností, může být způsobeno kompilátorem.