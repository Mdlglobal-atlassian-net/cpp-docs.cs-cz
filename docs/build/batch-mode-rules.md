---
title: Pravidla dávkového režimu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b002b17fcc70ff4e374fb0630e9c18a52cbfc4f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361441"
---
# <a name="batch-mode-rules"></a>Pravidla dávkového režimu
```  
{frompath}.fromext{topath}.toext::  
   commands  
```  
  
 Dávková odvozená pravidla zadejte pouze jeden vyvolání odvozené pravidlo při N příkazy projít toto pravidlo odvození. Bez dávková odvozená pravidla bude vyžadovat N příkazy má být volána. N je počet závislých položek, které aktivují odvozené pravidlo.  
  
 Soubory pravidel, které obsahují dávková odvozená pravidla musí používat NMAKE verze 1.62 nebo vyšší. Pokud chcete zkontrolovat verzi NMAKE, spusťte _NMAKE_VER makro k dispozici s NMAKE verze 1.62 nebo vyšší. Toto makro vrací řetězec představující verze produktu Visual C++.  
  
 Pouze syntaktické rozdíl oproti standardní odvozené pravidlo je, že dávková odvozená pravidla je byla ukončena s dvojitou dvojtečkou (:).  
  
> [!NOTE]
>  Nástroj volaná musí být schopna zpracovávat více souborů. Dávková odvozená pravidla musí používat `$<` jako makro pro přístup k souborům závislé.  
  
 Odvozená pravidla dávkového režimu urychlit procesu sestavení. Je rychlejší k poskytování soubory kompilátoru v dávce, protože ovladač kompilátoru vyvolána pouze jednou. Například kompilátor C a C++ provede lépe při zpracování sady souborů, protože ho může zůstat paměti rezidentní během procesu.  
  
 Následující příklad ukazuje, jak používat dávková odvozená pravidla:  
  
```  
#  
# sample makefile to illustrate batch-mode inference rules  
#  
O = .  
S = .  
Objs = $O/foo1.obj $O/foo2.obj $O/foo2.obj $O/foo3.obj $O/foo4.obj  
CFLAGS = -nologo  
  
all : $(Objs)  
  
!ifdef NOBatch  
{$S}.cpp{$O}.obj:  
!else  
{$S}.cpp{$O}.obj::  
!endif  
   $(CC) $(CFLAGS) -Fd$O\ -c $<  
  
$(Objs) :  
  
#end of makefile  
```  
  
 NMAKE vytvoří následující výstup bez dávková odvozená pravidla:  
  
```  
E:\tmp> nmake -f test.mak -a NOBatch=1  
  
Microsoft (R) Program Maintenance Utility   Version 7.00.0000  
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.  
        cl -nologo -Fd.\ -c .\foo1.cpp  
foo1.cpp  
        cl -nologo -Fd.\ -c .\foo2.cpp  
foo2.cpp  
        cl -nologo -Fd.\ -c .\foo3.cpp  
foo3.cpp  
        cl -nologo -Fd.\ -c .\foo4.cpp  
foo4.cpp  
```  
  
 NMAKE vytváří následující výsledků dávková odvozená pravidla:  
  
```  
E:\tmp> nmake -f test.mak -a  
  
Microsoft (R) Program Maintenance Utility   Version 7.00.0000  
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.  
  
        cl -nologo -Fd.\ -c .\foo1.cpp .\foo2.cpp .\foo3.cpp .\foo4.cpp  
foo1.cpp  
foo2.cpp  
foo3.cpp  
foo4.cpp  
Generating Code...  
```  
  
## <a name="see-also"></a>Viz také  
 [Odvozená pravidla](../build/inference-rules.md)