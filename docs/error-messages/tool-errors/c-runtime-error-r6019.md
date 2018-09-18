---
title: Chyba modulu Runtime R6019 C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6019
dev_langs:
- C++
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95bc763ab39df16c1cfc1b05689560edecf70570
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093298"
---
# <a name="c-runtime-error-r6019"></a>Chyba modulu Runtime R6019 C

Nelze otevřít konzolu zařízení

> [!NOTE]
>  Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože pokus o přístup ke konzole, ale neměli dostatečná oprávnění. Existuje několik možných důvodů pro tuto chybu, ale je obvykle, protože program musí spustit jako správce, nebo je chyba v programu.
>
>  Zkuste chybu odstranit pomocí tohoto postupu:
>
>  -   Spuštění programu jako správce.
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> -   Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K této chybě dochází, protože aplikace volá funkce konzoly, ale operační systém nezajistila přístup ke konzole. S výjimkou v režimu ladění, funkce konzoly nejsou obecně povoleny v aplikacích pro Microsoft Store. Pokud vaše aplikace vyžaduje oprávnění správce pro spuštění, ujistěte se, že je nainstalovaná ve výchozím nastavení Spustit jako správce.