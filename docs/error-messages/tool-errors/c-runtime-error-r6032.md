---
title: Chyba modulu C runtime R6032
ms.date: 11/04/2016
f1_keywords:
- R6032
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
ms.openlocfilehash: b29b946d08cff903cf0ca398ba0d7589cb5d54ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197090"
---
# <a name="c-runtime-error-r6032"></a>Chyba modulu C runtime R6032

Nedostatek místa pro informace o národním prostředí

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace se vypnula, protože má problém interní paměti. Tato chyba může mít několik příčin, ale často je způsobena extrémně nedostatkem paměti nebo chybou v programu.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Ukončete ostatní spuštěné aplikace nebo restartujte počítač pro uvolnění paměti.
> - K opravě nebo přeinstalaci programu použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Ověřte **web Windows Update** v **Ovládacích panelech** pro aktualizace softwaru.
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Modul runtime uchovává informace o národním prostředí v každém vlákně, aby mohl zpracovávat volání funkcí závislých na národním prostředí. Pokud přidělení paměti pro tyto informace neproběhne úspěšně, modul runtime nemůže pokračovat, protože na něm závisí příliš mnoho základních funkcí.
