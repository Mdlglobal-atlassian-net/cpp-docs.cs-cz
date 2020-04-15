---
title: Syntaxe příkazového řádku kompilátoru MSVC
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 6a56474b537d78a3d0bea8a74d9082007cd2e295
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320546"
---
# <a name="compiler-command-line-syntax"></a>Syntaxe příkazového řádku kompilátoru

Příkazový řádek CL používá následující syntaxi:

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

Následující tabulka popisuje vstup do příkazu CL.

|Záznam|Význam|
|-----------|-------------|
|*Možnost*|Jedna nebo více [možností CL](compiler-options.md). Všimněte si, že všechny možnosti platí pro všechny zadané zdrojové soubory. Možnosti jsou určeny lomítkem (/) nebo pomlčkou (-). Pokud volba přebírá argument, popis možnosti dokumentuje, zda je mezi možností a argumenty povolena mezera. Názvy možností (s výjimkou možnosti /HELP) rozlišují malá a velká písmena. Další informace naleznete [v části Pořadí možností CL.](order-of-cl-options.md)|
|`file`|Název jednoho nebo více zdrojových souborů, souborů OBJ nebo knihoven. Cl zkompiluje zdrojové soubory a předá názvy souborů OBJ a knihoven propojovacímu systému. Další informace naleznete [v tématu Syntaxe názvu souboru CL.](cl-filename-syntax.md)|
|*Lib*|Jeden nebo více názvů knihoven. CL předá tyto názvy propojovacímu sítí.|
|*soubor příkazů*|Soubor, který obsahuje více možností a názvů souborů. Další informace naleznete v [tématu CL Command Files.](cl-command-files.md)|
|*odkaz-opt*|Jedna nebo více [možností propojovacího zařízení MSVC](linker-options.md). CL předá tyto možnosti propojovacímu zařízení.|

Můžete zadat libovolný počet možností, názvy souborů a názvy knihoven, pokud počet znaků na příkazovém řádku nepřesáhne 1024, což je limit diktovaný operačním systémem.

Informace o vrácené hodnotě cl.exe naleznete v [tématu Return Value of cl.exe](return-value-of-cl-exe.md) .

> [!NOTE]
> Není zaručeno, že vstupní limit příkazového řádku 1024 znaků zůstane v budoucích verzích systému Windows stejný.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)
