---
title: -CLRHEADER | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRHEADER
dev_langs:
- C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5896e12d5e3b3b3984884388d11c6380e900d73d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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