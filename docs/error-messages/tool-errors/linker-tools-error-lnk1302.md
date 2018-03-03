---
title: "Chyba linkerů Lnk1302 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1302
dev_langs:
- C++
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a5b9201608d6d457288c7ade9376147da08bcb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1302"></a>Chyba linkerů LNK1302
podporují pouze propojování bezpečné .netmodules; Nelze vytvořit odkaz .netmodule souboru  
  
 .netmodule (Kompilovat s **/LN**) byla předána uživatelské pokus o vyvolání MSIL propojování linkeru.  Modul C++ je platný pro MSIL propojování, pokud je kompilován s **/CLR: safe**.  
  
 Opravit tuto chybu, kompilovat s **/CLR: safe** povolit MSIL propojování nebo předat **/CLR** nebo **/CLR: pure** souboru .obj linkeru místo modulu.  
  
 Další informace naleznete v tématu  
  
-   [/LN (vytvořit modul MSIL)](../../build/reference/ln-create-msil-module.md)  
  
-   [Soubory .netmodule jako vstup linkeru](../../build/reference/netmodule-files-as-linker-input.md)