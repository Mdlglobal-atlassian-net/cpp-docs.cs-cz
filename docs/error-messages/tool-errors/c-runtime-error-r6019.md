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
ms.openlocfilehash: 13653f54551501d5e35bd1285dc3d3f1a74343f1
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861593"
---
# <a name="c-runtime-error-r6019"></a>Chyba modulu Runtime R6019 C

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