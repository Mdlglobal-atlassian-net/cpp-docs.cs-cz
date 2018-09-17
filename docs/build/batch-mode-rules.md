---
title: Pravidla dávkového režimu | Dokumentace Microsoftu
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
ms.openlocfilehash: 4ddc5983f6a18146d12c75484e0db70f12797b35
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706235"
---
# <a name="batch-mode-rules"></a>Pravidla dávkového režimu

```
{frompath}.fromext{topath}.toext::
   commands
```

Dávková odvozená pravidla poskytnout pouze jednoho vyvolání odvozené pravidlo, když N příkazy procházejí tato pravidla odvození. Bez dávková odvozená pravidla bude vyžadovat N příkazů má být volána. N je počet závislé objekty, které aktivují odvozené pravidlo.

Soubory pravidel, která obsahují dávková odvozená pravidla musí používat NMAKE 1.62 nebo vyšší verze. Pokud chcete zkontrolovat verzi NMAKE, makro _NMAKE_VER k dispozici s NMAKE verze 1.62 nebo vyšší. Toto makro vrací řetězec vyjadřující verze produktu Visual C++.

Pouze syntaktickou rozdíl oproti standardní odvozené pravidlo je, že odvození pravidla dávkového režimu je přerušen skrze dvojtečka (:).

> [!NOTE]
>  Nástroj pro vyvolání musí být schopna zpracovávat více souborů. Odvozené pravidlo režimu služby batch musí používat `$<` jako makra pro přístup k závislé soubory.

Dávková odvozená pravidla může urychlit proces sestavení. Je rychlejší slouží k poskytování soubory pro kompilátor v dávce, protože kompilátor ovladač je vyvolána pouze jednou. Například kompilátor jazyka C a C++ provádí lépe při zpracování sady souborů, protože ho může zůstat paměti rezidentní během procesu.

Následující příklad ukazuje způsob použití dávková odvozená pravidla:

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

NMAKE vytvoří následující výsledek s dávková odvozená pravidla:

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