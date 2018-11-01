---
title: Syntaxe příkazového řádku kompilátoru
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: a350a2cb793630b90143b7d190ada9469a79bfc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581295"
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