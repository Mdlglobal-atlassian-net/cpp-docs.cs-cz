---
title: Proměnné prostředí CL
ms.date: 06/06/2019
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 4d6b1982b1e544459a025d6cb7bee75666e7130e
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440255"
---
# <a name="cl-environment-variables"></a>Proměnné prostředí CL

Nástroj CL používá následující proměnné prostředí:

- CL a \_CL_, je-li definován. Nástroj CL přiřadí možnosti a argumenty definované v proměnné prostředí CL k argumentům příkazového řádku a před zpracováním připojí možnosti a argumenty definované v \_CL_.

- Zahrňte, který musí odkazovat na podadresář \include instalace sady Visual Studio.

- LIBPATH, která určuje adresáře, ve kterých budou hledány soubory metadat, na které odkazuje [#using](../../preprocessor/hash-using-directive-cpp.md). Další informace o LIBPATH najdete v tématu [#using](../../preprocessor/hash-using-directive-cpp.md).

Pomocí následující syntaxe můžete nastavit proměnnou prostředí CL nebo \_CL_:

> SET CL = [[*možnost*]... [*soubor*]...] [ *odkaz na/Link – opt* ...] \
> Nastavte \_CL\_= [[*možnost*]... [*soubor*]...] [ *odkaz na/Link – opt* ...]

Podrobnosti o argumentech proměnných prostředí CL a \_CL_ naleznete v tématu [syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md).

Pomocí těchto proměnných prostředí můžete definovat soubory a možnosti, které často používáte. Pak použijte příkazový řádek k poskytnutí dalších souborů a možností CL pro konkrétní účely. Proměnné prostředí CL a \_CL_ jsou omezeny na 1024 znaků (vstupní limit příkazového řádku).

Možnost [/d](d-preprocessor-definitions.md) nemůžete použít k definování symbolu, který používá symbol rovná se ( **=** ). Místo toho můžete použít znaménko čísla ( **#** ) pro symbol rovná se. Tímto způsobem můžete použít proměnné prostředí CL nebo \_CL_ k definování konstant preprocesoru s explicitními hodnotami, například `/DDEBUG#1` k definování `DEBUG=1`.

Související informace najdete v tématu [nastavení proměnných prostředí](../setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Příklady

Následující příkaz je příkladem nastavení proměnné prostředí CL:

> SET CL =/Zp2/Ox/I\INCLUDE\MYINCLS \LIB\BINMODE. OBJEKTU

Pokud je nastavena proměnná prostředí CL, pak pokud zadáte `CL INPUT.C` do příkazového řádku, bude platný příkaz:

> CL/Zp2/Ox/I\INCLUDE\MYINCLS \LIB\BINMODE. VSTUP OBJ. R

Následující příklad způsobí, že příkaz v prostém CLě zkompiluje zdrojové soubory Soubor1. c a SOUBOR2. c a pak propojí soubory objektů Soubor1. obj, SOUBOR2. obj a FILE3. obj:

> NASTAVTE CL = SOUBOR1. C SOUBOR2. R
> Nastavte \_CL_ = FILE3. Objektu
> CL

Tyto proměnné prostředí umožňují volání CL stejný účinek jako následující příkazový řádek:

> CL SOUBOR1. C SOUBOR2. FILE3 C. OBJEKTU

## <a name="see-also"></a>Viz také

[Nastavení možností kompilátoru](compiler-command-line-syntax.md) \
[Parametry kompilátoru MSVC](compiler-options.md)
