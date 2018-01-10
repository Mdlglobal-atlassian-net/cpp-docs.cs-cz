---
title: "Chyba linkerů Lnk1309 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1309
dev_langs: C++
helpviewer_keywords: LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 425fb564ae2bd099746fc9b76b496595caa10a0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1309"></a>Chyba linkerů LNK1309
Type1 modulu došlo k detekci; Neplatná s /CLRIMAGETYPE:type2 přepínače  
  
 Typ obrázku CLR byl vyžádán pomocí **/CLRIMAGETYPE** ale linkeru nemohl vytvořit image daného typu, protože jeden nebo více modulů byly kompatibilní s daným typem.  
  
 Například uvidíte LNK1309, pokud zadáte **/CLRIMAGETYPE:safe** a předejte modul vytvořené s **/CLR: pure**.  
  
 Zobrazí se také LNK1309 při vytvoření částečně důvěryhodné aplikace čistý CLR pomocí .lib ptrustu [d]. Informace o tom, jak vytvořit částečně důvěryhodné aplikace najdete v tématu [postupy: Vytvoření částečně důvěryhodné aplikace odebrání závislostí na knihovnu DLL knihovny CRT](../../dotnet/create-a-partially-trusted-application.md).  
  
 Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [/CLRIMAGETYPE (zadat typ z obrázku CLR)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).