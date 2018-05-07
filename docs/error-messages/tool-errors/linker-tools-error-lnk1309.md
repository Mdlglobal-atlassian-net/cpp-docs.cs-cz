---
title: Chyba linkerů Lnk1309 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1309
dev_langs:
- C++
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f179a74823be1293bc927afe122c4bf14c0030b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1309"></a>Chyba linkerů LNK1309
Type1 modulu došlo k detekci; Neplatná s /CLRIMAGETYPE:type2 přepínače  
  
 Typ obrázku CLR byl vyžádán pomocí **/CLRIMAGETYPE** ale linkeru nemohl vytvořit image daného typu, protože jeden nebo více modulů byly kompatibilní s daným typem.  
  
 Například uvidíte LNK1309, pokud zadáte **/CLRIMAGETYPE:safe** a předejte modul vytvořené s **/CLR: pure**.  
  
 Zobrazí se také LNK1309 při vytvoření částečně důvěryhodné aplikace čistý CLR pomocí .lib ptrustu [d]. Informace o tom, jak vytvořit částečně důvěryhodné aplikace najdete v tématu [postupy: Vytvoření částečně důvěryhodné aplikace odebrání závislostí na knihovnu DLL knihovny CRT](../../dotnet/create-a-partially-trusted-application.md).  
  
 Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [/CLRIMAGETYPE (zadat typ z obrázku CLR)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).