---
title: Chyba modulu C runtime R6019
ms.date: 11/04/2016
f1_keywords:
- R6019
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
ms.openlocfilehash: 93d340b2a12a00420a9003429251387b2f04ad37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214093"
---
# <a name="c-runtime-error-r6019"></a>Chyba modulu C runtime R6019

Nelze otevřít konzolu zařízení

> [!NOTE]
> Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože pokus o přístup ke konzole, ale neměli dostatečná oprávnění. Existuje několik možných důvodů pro tuto chybu, ale je obvykle, protože program musí spustit jako správce, nebo je chyba v programu.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Spuštění programu jako správce.
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> - Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> - Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K této chybě dochází, protože aplikace volá funkce konzoly, ale operační systém nezajistila přístup ke konzole. S výjimkou v režimu ladění, funkce konzoly nejsou obecně povoleny v aplikacích pro Microsoft Store. Pokud vaše aplikace vyžaduje oprávnění správce pro spuštění, ujistěte se, že je nainstalovaná ve výchozím nastavení Spustit jako správce.