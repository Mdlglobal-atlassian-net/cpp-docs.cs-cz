---
title: -CLRHEADER | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /CLRHEADER
dev_langs: C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 699fa0e97236b1c5cf207e73dcbb39156bfbb130
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
  
-   1 – / CLR: safe (bitové kopie je MSIL pouze, může běžet na jakékoli platformě CLR a pravděpodobně ověřitelné).  
  
-   3 – / CLR: pure (bitové kopie je MSIL pouze, ale pouze může běžet na x86 platformy).  
  
 Můžete také programově zkontrolovat, pokud byl vytvořený bitovou kopii pro modul common language runtime.  Další informace najdete v tématu [postupy: určení, pokud bitová kopie je nativní nebo CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).  
  
 **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti DUMPBIN](../../build/reference/dumpbin-options.md)