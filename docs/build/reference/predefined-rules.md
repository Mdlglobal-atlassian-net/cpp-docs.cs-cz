---
title: Předdefinovaná pravidla
ms.date: 11/04/2016
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
ms.openlocfilehash: 7a922a239306f10121791caa8f9f088cea88c019
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319444"
---
# <a name="predefined-rules"></a>Předdefinovaná pravidla

Předdefinované odvozená pravidla použít makra NMAKE zadaný příkazu a možnosti.

|Pravidlo|Příkaz|Výchozí<br /><br /> Akce|Batch<br /><br /> Pravidlo|Nmake platformy běží na|
|----------|-------------|------------------------|--------------------|----------------------------|
|.asm.exe|$(AS) $(AFLAGS) $&LT;|ml $<|Ne|x86|
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|ano|x86|
|.asm.exe|$(AS) $(AFLAGS) $&LT;|ml64 $<|Ne|x64|
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml64 /c $<|ano|x64|
|.c.exe|$(CC) $(CFLAGS) $&LT;|cl $<|Ne|všechny|
|.c.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|ano|všechny|
|.cc.exe|$(CC) $(CFLAGS) $&LT;|cl $<|Ne|všechny|
|.cc.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|ano|všechny|
|.cpp.exe|$(CPP) $(CPPFLAGS) $&LT;|cl $<|Ne|všechny|
|.cpp.obj|$(CPP) $(CPPFLAGS) /c $<|cl /c $<|ano|všechny|
|.cxx.exe|$(CXX) $(CXXFLAGS) $<|cl $<|Ne|všechny|
|.cxx.obj|$(CXX) $(CXXFLAGS) /c $<|cl /c $<|ano|všechny|
|.rc.res|$(RC) $(RFLAGS) /r $<|rc /r $<|Ne|všechny|

## <a name="see-also"></a>Viz také:

[Odvozená pravidla](inference-rules.md)
