---
title: Proměnné prostředí CL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f3986097bcb5028d9ad708c9a3132f5e417d502
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cl-environment-variables"></a>Proměnné prostředí CL

Nástroj CL používá následující proměnné prostředí:

- CL a \_CL\_, pokud je definována. Nástroj CL přidá možnosti a argumenty, které jsou definované v proměnné prostředí CL pro argumenty příkazového řádku a připojí možnosti a argumenty definované v \_CL\_, před zpracováním.

- ZAHRNOUT, které musí odkazovat na podadresáři \include instalace Visual C++.

- LIBPATH, který určuje adresáře, které chcete hledat soubory metadat odkazovaná adresou [#using](../../preprocessor/hash-using-directive-cpp.md). V tématu `#using` Další informace o LIBPATH.

Můžete nastavit CL nebo \_CL\_ proměnné prostředí pomocí následující syntaxe:

> NASTAVIT CL = [[*možnost*]... [*souboru*]...] [/ link *odkaz opt* ...]  
> NASTAVIT \_CL\_= [[*možnost*]... [*souboru*]...] [/ link *odkaz opt* ...]

Podrobnosti o argumenty, které mají CL a \_CL\_ proměnné prostředí, najdete v části [syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md).

Můžete použít k definování soubory a možnosti, které uživatel používá nejčastěji těchto proměnných prostředí a pomocí příkazového řádku zadejte konkrétní soubory a možnosti pro konkrétní účely. CL a \_CL\_ proměnné prostředí jsou omezeny na 1024 znaků (příkazového řádku vstupní omezení).

Možnost /D nelze použít k definování symbol, který používá symbol rovná se (=). Můžete nahradit křížku (#) pro symbolem rovná. Tímto způsobem můžete použít CL nebo \_CL\_ proměnné prostředí k definování preprocesoru konstanty explicitní hodnotami – například `/DDEBUG#1` k definování `DEBUG=1`.

Související informace najdete v tématu [nastavit proměnné prostředí](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Příklady

Následuje příklad nastavení proměnné prostředí CL:

> Nastavte CL = / Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE. OBJ

Když je tato proměnná prostředí nastavená, pokud zadáte `CL INPUT.C` na příkazovém řádku Toto je efektivní příkaz:

> CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE. OBJ VSTUPU. C

Následující příklad způsobí, že prostý příkaz CL zkompilovat zdrojové soubory FILE1.c a FILE2.c, a pak propojit objekt soubory FILE1.obj, FILE2.obj a FILE3.obj:

> SADA CL = FILE1. C FILE2. C  
> NASTAVIT \_CL\_= SOUBOR3. OBJ  
> CL  

Tato akce nemá stejný účinek jako následující příkazový řádek:

> CL FILE1. C FILE2. SOUBOR3 C. OBJ

## <a name="see-also"></a>Viz také

[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
[Možnosti kompilátoru](../../build/reference/compiler-options.md)
