---
title: "Předem definovaná pravidla | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3be1c8eea7b11f60e9ce9a7cbf5ebc0c2b99b698
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="predefined-rules"></a>Předdefinovaná pravidla
Předdefinované odvozená pravidla použít makra NMAKE zadaný příkaz a možnosti.  
  
|Pravidlo|Příkaz|Výchozí<br /><br /> Akce|Batch<br /><br /> Pravidlo|Platforma nmake běží na|  
|----------|-------------|------------------------|--------------------|----------------------------|  
|. asm.exe|$(AS) $(AFLAGS) $<|ml $<|Ne|x86|  
|. asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|Ano|x86|  
|. asm.exe|$(AS) $(AFLAGS) $<|ml64 v příkazovém $<|Ne|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|. asm.obj|$(AS) $(AFLAGS) /c $<|ml64 v příkazovém /c $<|Ano|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|. c.exe|$(CC) $(CFLAGS) $<|cl $<|Ne|všechny|  
|. c.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|Ano|všechny|  
|. cc.exe|$(CC) $(CFLAGS) $<|cl $<|Ne|všechny|  
|. cc.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|Ano|všechny|  
|. cpp.exe|$(CPP) $(CPPFLAGS) $<|cl $<|Ne|všechny|  
|. cpp.obj|$(CPP) $(CPPFLAGS) /c $<|cl /c $<|Ano|všechny|  
|. cxx.exe|$(CXX) $(CXXFLAGS) $<|cl $<|Ne|všechny|  
|. cxx.obj|$(CXX) $(CXXFLAGS) /c $<|cl /c $<|Ano|všechny|  
|. rc.res|$(RC) $(RFLAGS) /r $<|RC /r $<|Ne|všechny|  
  
## <a name="see-also"></a>Viz také  
 [Odvozená pravidla](../build/inference-rules.md)