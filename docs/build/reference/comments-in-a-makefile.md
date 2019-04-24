---
title: Komentáře v souboru pravidel
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, comments
ms.assetid: 76fd9e3d-5966-47f4-a091-c9e80b232b49
ms.openlocfilehash: c66819210d2112f9a68243ed4d3b34f491caae9d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294353"
---
# <a name="comments-in-a-makefile"></a>Komentáře v souboru pravidel

Předcházet komentář znakem čísla (#). NMAKE ignoruje text z znak čísla na další znak nového řádku. Příklady:

```
# Comment on line by itself
OPTIONS = /MAP  # Comment on macro definition line

all.exe : one.obj two.obj  # Comment on dependency line
    link one.obj two.obj
# Comment in commands block
#   copy *.obj \objects  # Command turned into comment
    copy one.exe \release

.obj.exe:  # Comment on inference rule line
    link $<

my.exe : my.obj ; link my.obj  # Err: cannot comment this
# Error: # must be the first character
.obj.exe: ; link $<  # Error: cannot comment this
```

Chcete-li zadat literální znak, před se stříškou (**^**), následujícím způsobem:

```
DEF = ^#define  #Macro for a C preprocessing directive
```

## <a name="see-also"></a>Viz také:

[Obsah souboru pravidel](contents-of-a-makefile.md)
