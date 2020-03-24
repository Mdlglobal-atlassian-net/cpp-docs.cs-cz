---
title: Chyba modulu C runtime R6033
ms.date: 11/04/2016
f1_keywords:
- R6033
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
ms.openlocfilehash: 86ac98a2635975b811c7b50020e4d4782675ae4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197014"
---
# <a name="c-runtime-error-r6033"></a>Chyba modulu C runtime R6033

Došlo k pokusu o použití kódu jazyka MSIL z tohoto sestavení při inicializaci nativního kódu. To označuje chybu ve vaší aplikaci. Je pravděpodobně výsledkem volání funkce zkompilovaného jazyka MSIL (/CLR) z nativního konstruktoru nebo z DllMain.

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace byla vypnuta, protože došlo k vnitřnímu problému. Tato chyba může být způsobena chybou v aplikaci nebo chybou v doplňku nebo rozšíření, které používá.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - K opravě nebo přeinstalaci programu použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Na stránce **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** můžete odebrat, opravit nebo přeinstalovat jakákoli rozšíření nebo doplňky.
> - Ověřte **web Windows Update** v **Ovládacích panelech** pro aktualizace softwaru.
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Tato diagnostika indikuje, že instrukce jazyka MSIL byly spuštěny během zámku zavaděče. K této chybě může dojít, pokud jste C++ nakompilováni nativní pomocí příznaku/CLR. Pro moduly, které obsahují spravovaný kód, použijte pouze příznak/CLR. Další informace naleznete v tématu [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md).
