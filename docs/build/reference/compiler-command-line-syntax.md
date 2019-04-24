---
title: Syntaxe příkazového řádku kompilátoru MSVC
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 5cee76d5c053dbcfef33a191dc38a958338e4a82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294340"
---
# <a name="compiler-command-line-syntax"></a>Syntaxe příkazového řádku kompilátoru

Cl – příkazový řádek používá následující syntaxi:

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

Následující tabulka popisuje vstup do příkazu CL.

|Entry|Význam|
|-----------|-------------|
|*Možnost*|Jeden nebo více [možností CL](compiler-options.md). Nezapomeňte, že všechny možnosti vztahovat na všechny zadané zdrojové soubory. Možnosti jsou určeny lomítkem (/) nebo pomlčky (-). Pokud možnost přebírá argument, možnost Popis dokumentů, zda je povolena mezera mezi možností a argumentů. Názvy možností (s výjimkou možnost/Help) jsou malá a velká písmena. Zobrazit [pořadí možností CL](order-of-cl-options.md) Další informace.|
|`file`|Název jedné nebo více zdrojových souborů, soubory .obj nebo knihovny. CL zkompiluje zdrojové soubory a předá linkeru názvy soubory .obj a knihoven. Zobrazit [syntaxe názvu souboru CL](cl-filename-syntax.md) Další informace.|
|*lib*|Jeden nebo více názvů knihovny. CL předá linkeru tyto názvy.|
|*command-file*|Soubor, který obsahuje více parametrů a názvů souborů. Zobrazit [soubory příkazů CL](cl-command-files.md) Další informace.|
|*link-opt*|Jeden nebo více [možnosti Linkeru MSVC](linker-options.md). CL předá tyto možnosti linkeru.|

Jako počet znaků v příkazovém řádku, které není delší než 1024, limit určený operační systém, můžete zadat libovolný počet možností, názvy souborů a názvy knihoven.

Informace o vrácené hodnotě cl.exe najdete v tématu [vrátit hodnota cl.exe](return-value-of-cl-exe.md) .

> [!NOTE]
>  Příkazový řádek vstupní maximálně 1024 znaků. není zaručeno, že nebudou v budoucích verzích Windows.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)
