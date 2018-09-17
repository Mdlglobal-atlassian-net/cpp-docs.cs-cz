---
title: Syntaxe příkazového řádku kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18fb22ba370a447be8cb4cb2fb96633d702a1089
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710297"
---
# <a name="compiler-command-line-syntax"></a>Syntaxe příkazového řádku kompilátoru

Cl – příkazový řádek používá následující syntaxi:

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

Následující tabulka popisuje vstup do příkazu CL.

|Položka|Význam|
|-----------|-------------|
|*Možnost*|Jeden nebo více [možností CL](../../build/reference/compiler-options.md). Nezapomeňte, že všechny možnosti vztahovat na všechny zadané zdrojové soubory. Možnosti jsou určeny lomítkem (/) nebo pomlčky (-). Pokud možnost přebírá argument, možnost Popis dokumentů, zda je povolena mezera mezi možností a argumentů. Názvy možností (s výjimkou možnost/Help) jsou malá a velká písmena. Zobrazit [pořadí možností CL](../../build/reference/order-of-cl-options.md) Další informace.|
|`file`|Název jedné nebo více zdrojových souborů, soubory .obj nebo knihovny. CL zkompiluje zdrojové soubory a předá linkeru názvy soubory .obj a knihoven. Zobrazit [syntaxe názvu souboru CL](../../build/reference/cl-filename-syntax.md) Další informace.|
|*lib*|Jeden nebo více názvů knihovny. CL předá linkeru tyto názvy.|
|*soubor příkazů*|Soubor, který obsahuje více parametrů a názvů souborů. Zobrazit [soubory příkazů CL](../../build/reference/cl-command-files.md) Další informace.|
|*-opt odkaz*|Jeden nebo více [možnosti linkeru](../../build/reference/linker-options.md). CL předá tyto možnosti linkeru.|

Jako počet znaků v příkazovém řádku, které není delší než 1024, limit určený operační systém, můžete zadat libovolný počet možností, názvy souborů a názvy knihoven.

Informace o vrácené hodnotě cl.exe najdete v tématu [vrátit hodnota cl.exe](../../build/reference/return-value-of-cl-exe.md) .

> [!NOTE]
>  Příkazový řádek vstupní maximálně 1024 znaků. není zaručeno, že nebudou v budoucích verzích Windows.

## <a name="see-also"></a>Viz také

[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)