---
title: Předdefinovaná pravidla
ms.date: 11/04/2016
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
ms.openlocfilehash: b4b8ca7b0126ca42b2144aa094e7f766f6344b2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609687"
---
# <a name="predefined-rules"></a>Předdefinovaná pravidla

Předdefinované odvozená pravidla použít makra NMAKE zadaný příkazu a možnosti.

|Pravidlo|Příkaz|Výchozí<br /><br /> Akce|Služby batch<br /><br /> Pravidlo|Nmake platformy běží na|
|----------|-------------|------------------------|--------------------|----------------------------|
|. asm.exe|$(AS) $(AFLAGS) $&LT;|ml $<|Ne|x86|
|. asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|Ano|x86|
|. asm.exe|$(AS) $(AFLAGS) $&LT;|ml64 v příkazovém $<|Ne|x64|
|. asm.obj|$(AS) $(AFLAGS) /c $<|ml64 v příkazovém /c $<|Ano|x64|
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