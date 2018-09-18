---
title: Chyba za běhu C R6033 jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6033
dev_langs:
- C++
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb107dcd2bd044ad6fb933869319bb7afd5aab72
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049797"
---
# <a name="c-runtime-error-r6033"></a>Chyba za běhu C R6033 jazyka

Pokus o použití kód jazyka MSIL z tohoto sestavení během inicializace nativního kódu. To znamená chybu ve vaší aplikaci. Pravděpodobně je výsledek volání jazyka MSIL kompilována (/ clr) funkce z nativní konstruktoru nebo funkce DllMain.

> [!NOTE]
>  Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má vnitřní problém. Tato chyba může být způsobena chybu v aplikaci nebo chybu v add-in nebo rozšíření, které používá.
>
>  Zkuste chybu odstranit pomocí tohoto postupu:
>
>  -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** odebrat, opravte nebo přeinstalujte všechny přípony nebo doplňky.
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> -   Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Tato Diagnostika Určuje, že byly během zámek zavaděče spouštění instrukcí jazyka MSIL. Tato situace může nastat, pokud jste zkompilovali nativní kód C++ pomocí příznaku/CLR. Pouze pomocí příznaku/CLR na moduly, které obsahují spravovaného kódu. Další informace najdete v tématu [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md).