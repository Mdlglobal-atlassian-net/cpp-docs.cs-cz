---
title: Proměnné prostředí CL
ms.date: 05/06/2019
f1_keywords:
- cl
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 620ec386e06b1a0eed91c94e9b2b891d9955fd00
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65217633"
---
# <a name="cl-environment-variables"></a>Proměnné prostředí CL

Cl – nástroj používá následující proměnné prostředí:

- CL a \_CL\_, pokud je definována. Nástroj CL připojí na začátek možnosti a argumenty, které jsou definovány v proměnné prostředí CL na argumenty příkazového řádku a připojí možností a argumentů definované v \_CL\_, před zpracováním.

- ZAHRNOUT, který musí ukazovat na podadresáři \include instalace sady Visual Studio.

- Proměnná LIBPATH Určuje adresáře pro vyhledávání souborů metadat odkazovaný adresou [#using](../../preprocessor/hash-using-directive-cpp.md). Zobrazit `#using` Další informace o LIBPATH.

Můžete nastavit CL nebo \_CL\_ proměnnou prostředí pomocí následující syntaxe:

> Nastavte CL = [[*možnost*]... [*souboru*]...] [/ link *optimalizované odkaz* ...] Nastavte \_CL\_= [[*možnost*]... [*souboru*]...] [/ link *optimalizované odkaz* ...]

Podrobnosti o argumenty, které mají CL a \_CL\_ proměnné prostředí, najdete v článku [syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md).

Můžete použít k definování souborů a možnosti, které nejčastěji používáte tyto proměnné prostředí a pomocí příkazového řádku k definování určité soubory a možnosti pro konkrétní účely. CL a \_CL\_ proměnné prostředí jsou omezená na 1024 znaků (příkazový řádek vstupu omezení).

Možnosti/d. nelze použít k definici symbolu, který používá rovnítko (=). Můžete nahradit křížku (#) pro znaménko rovná se. Tímto způsobem můžete použít CL nebo \_CL\_ proměnné prostředí pro definování preprocesoru konstant s explicitní hodnoty – například `/DDEBUG#1` k definování `DEBUG=1`.

Související informace naleznete v tématu [nastavit proměnné prostředí](../setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Příklady

Následuje příklad nastavení proměnné prostředí CL:

> SET CL=/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ

Pokud je tato proměnná prostředí nastavíte, pokud zadáte `CL INPUT.C` příkazového řádku, toto je účinné příkaz:

> CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ INPUT.C

Následující příklad způsobí, že obyčejný CL příkaz pro kompilaci souborů zdrojového souboru FILE1.c a soubor FILE2.c a pak propojení objektových souborů FILE1.obj FILE2.obj a FILE3.obj:

> SADA CL = FILE1. C FILE2. SADA C \_CL\_= SOUBOR3. OBJ CL

To má stejný účinek jako následující příkazový řádek:

> CL FILE1.C FILE2.C FILE3.OBJ

## <a name="see-also"></a>Viz také:

[Nastavení možností kompilátoru](compiler-command-line-syntax.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)
