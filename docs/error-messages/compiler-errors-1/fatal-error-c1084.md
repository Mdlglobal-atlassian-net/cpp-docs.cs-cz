---
title: Závažná chyba C1084 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1084
dev_langs:
- C++
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7266a2158c3e6ccd02ea82de22c6f90a8b6363d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229386"
---
# <a name="fatal-error-c1084"></a>Závažná chyba C1084
Nelze načíst soubor typ souboru: 'file': zpráva  
  
 Tato chyba je obecně výsledek volání se nezdařilo interní systémové rozhraní API provedené kompilátoru. Buď je často vygenerována zpráva zobrazí, když došlo k této chybě [_wcserror_s –](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) nebo [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351.aspx).  
  
 Následujícím postupem mohou napomoci vyřešení C1084:  
  
-   Zkontrolujte, zda že zadaný soubor existuje.  
  
-   Zkontrolujte, zda že jsou nastaveny příslušná oprávnění pro přístup zadaný soubor.  
  
-   Zkontrolujte syntaxi příkazového řádku dodržuje pravidla uvedených v části [syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md).  
  
-   Ujistěte se, že proměnné prostředí **TMP** a **TEMP** jsou správně sady, jakož i příslušná oprávnění pro přístup k adresáři těchto proměnných prostředí naleznete. Také zajistěte, aby jednotky odkazuje **TMP** a **TEMP** proměnné prostředí obsahovat dostatečné množství volného místa.  
  
-   Pokud zpráva říká "chybného souboru číslo", zadaný soubor může mít byla zavření v popředí při kompilování na pozadí.  
  
 Po provedení výše diagnostiky, vytvořit nové čisté sestavení.