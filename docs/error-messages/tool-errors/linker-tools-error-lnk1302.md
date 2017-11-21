---
title: "Chyba linkerů Lnk1302 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1302
dev_langs: C++
helpviewer_keywords: LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7154cc538e17050eafec251729cf26a3cd62e573
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1302"></a>Chyba linkerů LNK1302
podporují pouze propojování bezpečné .netmodules; Nelze vytvořit odkaz .netmodule souboru  
  
 .netmodule (Kompilovat s **/LN**) byla předána uživatelské pokus o vyvolání MSIL propojování linkeru.  Modul C++ je platný pro MSIL propojování, pokud je kompilován s **/CLR: safe**.  
  
 Opravit tuto chybu, kompilovat s **/CLR: safe** povolit MSIL propojování nebo předat **/CLR** nebo **/CLR: pure** souboru .obj linkeru místo modulu.  
  
 Další informace naleznete v tématu  
  
-   [/LN (vytvořit modul MSIL)](../../build/reference/ln-create-msil-module.md)  
  
-   [soubory .netmodule jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md)