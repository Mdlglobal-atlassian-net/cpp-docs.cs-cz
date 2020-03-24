---
title: Chyba modulu C runtime R6019
ms.date: 11/04/2016
f1_keywords:
- R6019
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
ms.openlocfilehash: b647825b7e856be9dc51a5a652be87a4cc6d0e23
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197259"
---
# <a name="c-runtime-error-r6019"></a>Chyba modulu C runtime R6019

Nepovedlo se otevřít zařízení konzoly.

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace se vypnula, protože se pokusila získat přístup ke konzole, ale nemá dostatečná oprávnění. K této chybě může dojít z několika možných důvodů, je to však obvykle proto, že program musí být spuštěn jako správce nebo v programu došlo k chybě.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Spusťte program jako správce.
> - K opravě nebo přeinstalaci programu použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Ověřte **web Windows Update** v **Ovládacích panelech** pro aktualizace softwaru.
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K této chybě dochází, protože aplikace volala konzolovou funkci, ale operační systém neudělil přístup ke konzole. S výjimkou v režimu ladění nejsou funkce konzoly obecně v aplikacích Microsoft Store povoleny. Pokud vaše aplikace vyžaduje ke spuštění oprávnění správce, ujistěte se, že je ve výchozím nastavení spuštěná jako správce.
