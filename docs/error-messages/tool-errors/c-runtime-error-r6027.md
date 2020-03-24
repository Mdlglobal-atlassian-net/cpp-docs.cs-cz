---
title: Chyba modulu C runtime R6027
ms.date: 11/04/2016
f1_keywords:
- R6027
helpviewer_keywords:
- R6027
ms.assetid: c06a62b3-08d9-4bf5-bcad-8340ec552f69
ms.openlocfilehash: 8c2aab7b090dbfa4553b8d1622f13aef13f58aa3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197168"
---
# <a name="c-runtime-error-r6027"></a>Chyba modulu C runtime R6027

nedostatek místa pro inicializaci lowio

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace se vypnula, protože má problém interní paměti. K této chybě může dojít z několika možných důvodů, ale obvykle je způsobena extrémně nízkým stavem paměti. Může to být také způsobeno chybou v aplikaci, poškozením vizuálních C++ knihoven, které používá, nebo ovladačem.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Ukončete ostatní spuštěné aplikace nebo restartujte počítač pro uvolnění paměti.
> - K opravě nebo přeinstalaci programu použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Pokud aplikace pracovala před poslední instalací jiné aplikace nebo ovladače, odeberte novou aplikaci nebo ovladač pomocí stránky **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** a zkuste aplikaci znovu.
> - Použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** k opravě nebo přeinstalaci všech kopií Microsoft Visual C++ Redistributable.
> - Ověřte **web Windows Update** v **Ovládacích panelech** pro aktualizace softwaru.
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K této chybě dochází, pokud není k dispozici dostatek volné paměti pro inicializaci podpory vstupu a výstupu nízké úrovně v modulu runtime jazyka C. K této chybě obvykle dochází při spuštění aplikace. Ověřte, že vaše aplikace a ovladače a knihovny DLL, které načte, nepoškozují haldu při spuštění.
