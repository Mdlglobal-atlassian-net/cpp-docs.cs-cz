---
title: Chyba modulu Runtime R6031 C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6031
dev_langs:
- C++
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83dbcdc433ea731e6ddf0765b4b3a55d5707f429
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059495"
---
# <a name="c-runtime-error-r6031"></a>Chyba modulu Runtime R6031 C

Pokus o inicializaci CRT více než jednou. To znamená chybu ve vaší aplikaci.

> [!NOTE]
>  Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má vnitřní problém. To může být způsobeno chyb v aplikaci, nebo chybu v doplňku nebo rozšíření, které aplikace používá.
>
>  Zkuste chybu odstranit pomocí tohoto postupu:
>
>  -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** odebrat, opravte nebo přeinstalujte všechny doplněk nebo rozšíření programy, které aplikace používá.
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> -   Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Tato Diagnostika Určuje, že byly během zámek zavaděče spouštění instrukcí jazyka MSIL. Další informace najdete v tématu [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md).