---
title: Závažná chyba C1084 | Dokumentace Microsoftu
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
ms.openlocfilehash: 47d56641209ea1fe192bf0c32ace7701a1e579dc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054529"
---
# <a name="fatal-error-c1084"></a>Závažná chyba C1084

Nejde přečíst soubor filetype: 'file': zpráva

Tato chyba je obecně výsledek volání se nezdařilo interní systémové rozhraní API provedené kompilátorem. Zpráva zobrazená, když k této chybě dochází často generuje buď [_wcserror_s –](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) nebo [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage).

Provedením následujících kroků může vyřešit C1084:

- Ujistěte se, že zadaný soubor existuje.

- Ujistěte se, že jsou nastavené příslušná oprávnění pro přístup k souboru.

- Zkontrolujte syntaxi příkazového řádku dodržuje pravidel popsaných v části [syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md).

- Zkontrolujte, že proměnné prostředí **TMP** a **TEMP** jsou správně set, stejně jako příslušná oprávnění pro přístup k adresáři, tyto proměnné prostředí odkazovat. Také zajistěte, aby disky odkazuje **TMP** a **TEMP** proměnné prostředí obsahují odpovídající množství volného místa.

- Pokud zpráva "Chybné číslo souboru" zadaný soubor může mít byla zavření v popředí při kompilaci na pozadí.

Po provedení výše uvedených diagnostiky, proveďte čisté sestavení.