---
title: Předem definovaná pravidla | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0a21847bb9363099fa64825b45a90003de053da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="predefined-rules"></a>Předdefinovaná pravidla
Předdefinované odvozená pravidla použít makra NMAKE zadaný příkaz a možnosti.  
  
|Pravidlo|Příkaz|Výchozí<br /><br /> Akce|Batch<br /><br /> Pravidlo|Platforma nmake běží na|  
|----------|-------------|------------------------|--------------------|----------------------------|  
|. asm.exe|$(AS) $(AFLAGS) $&LT;|ml $<|Ne|x86|  
|. asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|Ano|x86|  
|. asm.exe|$(AS) $(AFLAGS) $&LT;|ml64 v příkazovém $<|Ne|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|. asm.obj|$(AS) $(AFLAGS) /c $<|ml64 v příkazovém /c $<|Ano|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|. c.exe|$(CC) $(CFLAGS) $&LT;|cl $<|Ne|všechny|  
|. c.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|Ano|všechny|  
|. cc.exe|$(CC) $(CFLAGS) $&LT;|cl $<|Ne|všechny|  
|. cc.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|Ano|všechny|  
|. cpp.exe|$(CPP) $(CPPFLAGS) $&LT;|cl $<|Ne|všechny|  
|. cpp.obj|$(CPP) $(CPPFLAGS) /c $<|cl /c $<|Ano|všechny|  
|. cxx.exe|$(CXX) $(CXXFLAGS) $&LT;|cl $<|Ne|všechny|  
|. cxx.obj|$(CXX) $(CXXFLAGS) /c $<|cl /c $<|Ano|všechny|  
|. rc.res|$(RC) $(RFLAGS) /r $<|RC /r $<|Ne|všechny|  
  
## <a name="see-also"></a>Viz také  
 [Odvozená pravidla](../build/inference-rules.md)