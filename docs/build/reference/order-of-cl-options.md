---
title: Pořadí možností CL (C++) – Visual Studio
ms.date: 12/14/2018
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: 6c57a68dd15d82a9d6a01bfe145374bda6eb1510
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439196"
---
# <a name="order-of-cl-options"></a>Pořadí možností CL

Možnosti se mohou objevit kdekoli na příkazovém řádku CL s výjimkou možnosti/Link, která se musí vyskytovat jako poslední. Kompilátor začíná s možnostmi zadanými v [proměnné prostředí CL](cl-environment-variables.md) a pak čte příkazový řádek zleva doprava – zpracování příkazových souborů v pořadí, v jakém je narazí. Každá možnost se vztahuje na všechny soubory v příkazovém řádku. Pokud CL nalezne konfliktní možnosti, použije možnost úplně vpravo.

## <a name="see-also"></a>Viz také

[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
