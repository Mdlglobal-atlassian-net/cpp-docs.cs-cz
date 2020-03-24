---
title: Chyba modulu C runtime R6031
ms.date: 11/04/2016
f1_keywords:
- R6031
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
ms.openlocfilehash: 4b75b0855f0f0d60304cfe8b7a00b4ce27a8daab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197103"
---
# <a name="c-runtime-error-r6031"></a>Chyba modulu C runtime R6031

Pokus o inicializaci CRT více než jednou. To označuje chybu ve vaší aplikaci.

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace byla vypnuta, protože došlo k vnitřnímu problému. Příčinou může být chyba v aplikaci nebo chyba v doplňku nebo rozšíření, které aplikace používá.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - K opravě nebo přeinstalaci programu použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Na stránce **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** můžete odebrat, opravit nebo přeinstalovat všechny doplňky nebo programy rozšíření používané aplikací.
> - Ověřte **web Windows Update** v **Ovládacích panelech** pro aktualizace softwaru.
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Tato diagnostika indikuje, že instrukce jazyka MSIL byly spuštěny během zámku zavaděče. Další informace naleznete v tématu [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md).
