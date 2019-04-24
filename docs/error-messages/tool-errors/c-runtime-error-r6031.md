---
title: Chyba modulu C runtime R6031
ms.date: 11/04/2016
f1_keywords:
- R6031
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
ms.openlocfilehash: 6ef3f5fa7d063fdc300e6ac28ca519992525851c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242679"
---
# <a name="c-runtime-error-r6031"></a>Chyba modulu C runtime R6031

Pokus o inicializaci CRT více než jednou. To znamená chybu ve vaší aplikaci.

> [!NOTE]
> Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má vnitřní problém. To může být způsobeno chyb v aplikaci, nebo chybu v doplňku nebo rozšíření, které aplikace používá.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** odebrat, opravte nebo přeinstalujte všechny doplněk nebo rozšíření programy, které aplikace používá.
> - Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> - Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Tato Diagnostika Určuje, že byly během zámek zavaděče spouštění instrukcí jazyka MSIL. Další informace najdete v tématu [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md).