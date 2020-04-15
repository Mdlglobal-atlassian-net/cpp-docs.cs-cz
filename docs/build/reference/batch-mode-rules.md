---
title: Pravidla dávkového režimu
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: 38402e7b8a937cebb823ce13fa1ac01fc1099878
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328415"
---
# <a name="batch-mode-rules"></a>Pravidla dávkového režimu

```
{frompath}.fromext{topath}.toext::
   commands
```

Pravidla odvození dávkového režimu poskytují pouze jedno vyvolání pravidla odvození, když příkazy N procházejí tímto pravidlem odvození. Bez pravidel odvození dávkového režimu by vyžadovalo vyvolání příkazů N. N je počet závislých osob, které aktivují pravidlo odvození.

Makefiles, které obsahují pravidla odvození dávkového režimu musí používat NMAKE verze 1.62 nebo vyšší. Chcete-li zkontrolovat verzi NMAKE, spusťte makro _NMAKE_VER, které je k dispozici s nmake verze 1.62 nebo vyšší. Toto makro vrátí řetězec představující verzi produktu Visual C++.

Jediný syntaktický rozdíl od standardního pravidla odvození je, že pravidlo odvození dávkového režimu je ukončeno dvojitým dvojtečkou (::).

> [!NOTE]
> Vztažný nástroj musí být schopen zpracovat více souborů. Pravidlo odvození dávkového režimu `$<` musí být používáno jako makro pro přístup k závislým souborům.

Pravidla odvození dávkového režimu může urychlit proces sestavení. Je rychlejší dodávat soubory do kompilátoru v dávce, protože ovladač kompilátoru je vyvolána pouze jednou. Například kompilátor C a C++ funguje lépe při zpracování sady souborů, protože může zůstat rezidentní paměti během procesu.

Následující příklad ukazuje, jak používat pravidla odvození dávkového režimu:

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

NMAKE vytváří následující výstup bez pravidel odvození dávkového režimu:

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

NMAKE vytváří následující výsledek s pravidly odvození dávkového režimu:

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

[Odvozená pravidla](inference-rules.md)
