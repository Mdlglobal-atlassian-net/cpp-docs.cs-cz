---
title: "Proměnné prostředí CL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cl
dev_langs: C++
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ba01a980aa24a3ff695479edd08e88d9ea538dcc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
