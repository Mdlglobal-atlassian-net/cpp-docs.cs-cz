---
title: Chyba linkerů Lnk1302 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1302
dev_langs:
- C++
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6aa84a411f91303c84acb44e2e6c0ab3d975e19f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1302"></a>Chyba linkerů LNK1302
podporují pouze propojování bezpečné .netmodules; Nelze vytvořit odkaz .netmodule souboru  
  
 .netmodule (Kompilovat s **/LN**) byla předána uživatelské pokus o vyvolání MSIL propojování linkeru.  Modul C++ je platný pro MSIL propojování, pokud je kompilován s **/CLR: safe**.  
  
 Opravit tuto chybu, kompilovat s **/CLR: safe** povolit MSIL propojování nebo předat **/CLR** nebo **/CLR: pure** souboru .obj linkeru místo modulu.  
  
 Další informace naleznete v tématu  
  
-   [/LN (vytvoření modulu MSIL)](../../build/reference/ln-create-msil-module.md)  
  
-   [Soubory .netmodule jako vstup linkeru](../../build/reference/netmodule-files-as-linker-input.md)