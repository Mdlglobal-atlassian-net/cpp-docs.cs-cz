---
title: -CLRHEADER | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLRHEADER
dev_langs:
- C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 73f68c4f73d132254ea64d4b3b3b9f787f3a4b82
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="clrheader"></a>/CLRHEADER
```  
/CLRHEADER file  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 `file`  
 Soubor bitové kopie vytvořené s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="remarks"></a>Poznámky  
 CLRHEADER zobrazí informace o hlavičkách .NET použít libovolné spravované aplikace. Výstup zobrazuje umístění a velikost v bajtech v záhlaví .NET a částech v hlavičce.  
  
 Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití na soubory vytvořené pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.  
  
 Pokud /CLRHEADER se používá pro určitý soubor, který byl kompilován s volbou/CLR, budou existovat **clr záhlaví:** části ve výstupu nástroje dumpbin.  Hodnota **příznaky** označuje, která možnost/CLR byl použit:  
  
-   0 – / CLR (image může obsahovat nativního kódu).  
  
 Můžete také programově zkontrolovat, pokud byl vytvořený bitovou kopii pro modul common language runtime.  Další informace najdete v tématu [postupy: určení, pokud bitová kopie je nativní nebo CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).  
  
 **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a bude v budoucí verzi systému kompilátoru odebrána. Kód, který musí být "čistý" nebo "bezpečnou" musí být přesně do jazyka C#. 
  
## <a name="see-also"></a>Viz také  
 [DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)