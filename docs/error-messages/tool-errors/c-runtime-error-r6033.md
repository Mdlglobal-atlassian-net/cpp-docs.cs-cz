---
title: Chyba modulu C runtime R6033
ms.date: 11/04/2016
f1_keywords:
- R6033
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
ms.openlocfilehash: 39d8a20dacb0cdeb2a767529e9716bd476f406dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400003"
---
# <a name="c-runtime-error-r6033"></a>Chyba modulu C runtime R6033

Pokus o použití kód jazyka MSIL z tohoto sestavení během inicializace nativního kódu. To znamená chybu ve vaší aplikaci. Pravděpodobně je výsledek volání jazyka MSIL kompilována (/ clr) funkce z nativní konstruktoru nebo funkce DllMain.

> [!NOTE]
> Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má vnitřní problém. Tato chyba může být způsobena chybu v aplikaci nebo chybu v add-in nebo rozšíření, které používá.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** odebrat, opravte nebo přeinstalujte všechny přípony nebo doplňky.
> - Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> - Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Tato Diagnostika Určuje, že byly během zámek zavaděče spouštění instrukcí jazyka MSIL. Tato situace může nastat, pokud jste zkompilovali nativní kód C++ pomocí příznaku/CLR. Pouze pomocí příznaku/CLR na moduly, které obsahují spravovaného kódu. Další informace najdete v tématu [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md).