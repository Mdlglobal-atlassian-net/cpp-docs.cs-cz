---
title: Chyba modulu C runtime R6025
ms.date: 11/04/2016
f1_keywords:
- R6025
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
ms.openlocfilehash: d5edb08278b7b6b9b3eb62e92fc04410f96a8f09
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075131"
---
# <a name="c-runtime-error-r6025"></a>Chyba modulu C runtime R6025

čistě virtuální volání funkce

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace byla vypnuta, protože došlo k vnitřnímu problému. Nejběžnějším důvodem této chyby je chyba v aplikaci nebo poškozená instalace.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - K opravě nebo přeinstalaci programu použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Ověřte **web Windows Update** v **Ovládacích panelech** pro aktualizace softwaru.
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Nevytvořila se instance žádného objektu pro zpracování čistě virtuální funkce volání.

Tato chyba je způsobena voláním virtuální funkce v abstraktní základní třídě pomocí ukazatele, který je vytvořen přetypováním na typ odvozené třídy, ale ve skutečnosti je ukazatel na základní třídu. K této chybě může dojít při přetypování z **void** <strong>\*</strong> na ukazatel na třídu, když byl<strong>\*</strong> **void** vytvořen během konstrukce základní třídy.
