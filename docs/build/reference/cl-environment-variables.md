---
title: Proměnné prostředí CL
ms.date: 06/06/2019
f1_keywords:
- cl
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 0f7930728ef1bf6bea50c4388d52d30c569a8795
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821532"
---
# <a name="cl-environment-variables"></a>Proměnné prostředí CL

Cl – nástroj používá následující proměnné prostředí:

- CL a \_CL_, pokud je definována. Nástroj CL připojí na začátek možnosti a argumenty, které jsou definovány v proměnné prostředí CL do argumentů příkazového řádku a připojí možností a argumentů definované v \_CL_ před zpracováním.

- ZAHRNOUT, který musí ukazovat na podadresáři \include instalace sady Visual Studio.

- Proměnná LIBPATH Určuje adresáře pro vyhledávání souborů metadat odkazovaný adresou [#using](../../preprocessor/hash-using-directive-cpp.md). Další informace o LIBPATH najdete v tématu [#using](../../preprocessor/hash-using-directive-cpp.md).

Můžete nastavit CL nebo \_CL_ proměnnou prostředí pomocí následující syntaxe:

> Nastavte CL = [[*možnost*]... [*souboru*]...] [/ link *optimalizované odkaz* ...] \
> Nastavte \_CL\_= [[*možnost*]... [*souboru*]...] [/ link *optimalizované odkaz* ...]

Podrobnosti o argumenty, které mají CL a \_CL_ proměnné prostředí, najdete v článku [syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md).

Tyto proměnné prostředí můžete použít k definování souborů a možnosti, které nejčastěji používáte. Potom použijte příkazový řádek má dát další soubory a možností CL pro konkrétní účely. CL a \_CL_ proměnné prostředí jsou omezená na 1024 znaků (příkazový řádek vstupu omezení).

Nelze použít [/D](d-preprocessor-definitions.md) možnost definovat symbol, který používá znaménko rovná se ( **=** ). Místo toho můžete použít znak čísla ( **#** ) pro znaménko rovná se. Tímto způsobem můžete použít CL nebo \_CL_ proměnné prostředí pro definování preprocesoru konstant s explicitní hodnoty – například `/DDEBUG#1` k definování `DEBUG=1`.

Související informace naleznete v tématu [nastavit proměnné prostředí](../setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Příklady

Příklad nastavení proměnné prostředí CL je následující příkaz:

> SET CL=/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ

Když je nastavit proměnné prostředí CL, pokud zadáte `CL INPUT.C` příkazového řádku, efektivní příkazu stane:

> CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ INPUT.C

Následující příklad způsobí, že obyčejný CL příkaz pro kompilaci souborů zdrojového souboru FILE1.c a soubor FILE2.c a pak propojení objektových souborů FILE1.obj FILE2.obj a FILE3.obj:

> SADA CL = FILE1. C FILE2. C \
> SET \_CL_=FILE3.OBJ \
> CL

Tyto proměnné prostředí provede volání CL má stejný účinek jako následující příkazový řádek:

> CL FILE1.C FILE2.C FILE3.OBJ

## <a name="see-also"></a>Viz také:

[Nastavení možností kompilátoru](compiler-command-line-syntax.md) \
[Parametry kompilátoru MSVC](compiler-options.md)
