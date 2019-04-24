---
title: Závažná chyba C1084
ms.date: 11/04/2016
f1_keywords:
- C1084
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
ms.openlocfilehash: 8c90616165a7b47d4251ace998fd49c613f244b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208812"
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